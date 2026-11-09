```cpp
#define NOMINMAX
#define WIN32_LEAN_AND_MEAN
#define PAHO_MQTTPP_IMPORTS

#include <iostream>
#include <string>
#include <set>
#include <chrono>
#include <thread>

#ifdef _WIN32
#include <winsock2.h>
#include <ws2tcpip.h>
#pragma comment(lib, "Ws2_32.lib")
#endif

#ifdef max
#undef max
#endif

#ifdef min
#undef min
#endif

#include <mqtt/async_client.h>

using namespace std;

// Algemene instellingen
const string BROKER = "tcp://localhost:1883";
const string REQUEST_TOPIC = "robotfleet/overdracht";
const string ACK_TOPIC = "robotfleet/bevestiging";

const int PORT = 5050;

// Voorkomt dat hetzelfde bericht twee keer wordt verwerkt
set<string> verwerkteBerichten;

//tcp zone b

void tcpServer()
{
    WSADATA wsaData;

    if (WSAStartup(MAKEWORD(2, 2), &wsaData) != 0)
    {
        cout << "Fout bij opstarten Winsock." << endl;
        return;
    }

    SOCKET serverSocket = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);

    if (serverSocket == INVALID_SOCKET)
    {
        cout << "Socket fout: " << WSAGetLastError() << endl;
        WSACleanup();
        return;
    }

    sockaddr_in serverAddress{};
    serverAddress.sin_family = AF_INET;
    serverAddress.sin_addr.s_addr = INADDR_ANY;
    serverAddress.sin_port = htons(PORT);

    if (::bind(serverSocket, (sockaddr*)&serverAddress,
        sizeof(serverAddress)) == SOCKET_ERROR)
    {
        cout << "Bind fout: " << WSAGetLastError() << endl;
        closesocket(serverSocket);
        WSACleanup();
        return;
    }

    if (listen(serverSocket, 1) == SOCKET_ERROR)
    {
        cout << "Listen fout: " << WSAGetLastError() << endl;
        closesocket(serverSocket);
        WSACleanup();
        return;
    }

    cout << "Zone B wacht op een TCP-bericht..." << endl;

    SOCKET clientSocket = accept(serverSocket, nullptr, nullptr);

    if (clientSocket == INVALID_SOCKET)
    {
        cout << "Accept fout: " << WSAGetLastError() << endl;
        closesocket(serverSocket);
        WSACleanup();
        return;
    }

    char buffer[1024]{};
    int bytesReceived = recv(clientSocket, buffer, sizeof(buffer) - 1, 0);

    if (bytesReceived > 0)
    {
        string bericht(buffer, bytesReceived);
        string id = bericht.substr(0, bericht.find(';'));

        cout << "Bericht ontvangen: " << bericht << endl;

        if (verwerkteBerichten.count(id) == 0)
        {
            verwerkteBerichten.insert(id);
            cout << "Overdracht wordt verwerkt." << endl;
        }
        else
        {
            cout << "Dubbel bericht, niet opnieuw verwerkt." << endl;
        }

        string antwoord = id + ";ONTVANGEN";

        send(clientSocket, antwoord.c_str(),
            (int)antwoord.size(), 0);
    }
    else
    {
        cout << "Ontvangen mislukt: " << WSAGetLastError() << endl;
    }

    closesocket(clientSocket);
    closesocket(serverSocket);
    WSACleanup();
}

// tcp zone a

void tcpClient()
{
    WSADATA wsaData;
    WSAStartup(MAKEWORD(2, 2), &wsaData);

    SOCKET clientSocket = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);

    sockaddr_in serverAddress{};
    serverAddress.sin_family = AF_INET;
    serverAddress.sin_port = htons(PORT);
    inet_pton(AF_INET, "127.0.0.1", &serverAddress.sin_addr);

    cout << "Verbinden met Zone B..." << endl;

    if (connect(clientSocket, (sockaddr*)&serverAddress, sizeof(serverAddress)) == SOCKET_ERROR)
    {
        cout << "Verbinding mislukt." << endl;
    }
    else
    {
        string bericht = "001;PALLET_OVERDRACHT";

        send(clientSocket, bericht.c_str(), (int)bericht.size(), 0);

        cout << "Overdrachtsverzoek verstuurd." << endl;

        char buffer[1024]{};
        int bytesReceived = recv(clientSocket, buffer, sizeof(buffer) - 1, 0);

        if (bytesReceived > 0)
        {
            cout << "Bevestiging ontvangen: "
                << string(buffer, bytesReceived) << endl;
        }
        else
        {
            cout << "Geen bevestiging ontvangen." << endl;
        }
    }

    closesocket(clientSocket);
    WSACleanup();
}

// mqtt zone b

void mqttServer()
{
    mqtt::async_client client(BROKER, "ZoneB");

    mqtt::connect_options options;
    client.connect(options)->wait();

    client.start_consuming();
    client.subscribe(REQUEST_TOPIC, 1)->wait();

    cout << "Zone B wacht op een MQTT-bericht..." << endl;

    while (true)
    {
        auto message = client.try_consume_message_for(chrono::seconds(1));

        if (message)
        {
            string bericht = message->to_string();
            string id = bericht.substr(0, bericht.find(';'));

            if (verwerkteBerichten.count(id) == 0)
            {
                verwerkteBerichten.insert(id);
                cout << "Nieuw bericht ontvangen: " << bericht << endl;
                cout << "Overdracht wordt verwerkt." << endl;
            }
            else
            {
                cout << "Dubbel bericht ontvangen. Niet opnieuw verwerkt." << endl;
            }

            string antwoord = id + ";ONTVANGEN";

            auto bevestiging = mqtt::make_message(ACK_TOPIC, antwoord);
            bevestiging->set_qos(1);

            client.publish(bevestiging)->wait();

            cout << "Bevestiging verstuurd." << endl;
            break;
        }
    }

    client.disconnect()->wait();
}
// mqtt zone a

void mqttClient()
{
    mqtt::async_client client(BROKER, "ZoneA");

    mqtt::connect_options options;
    client.connect(options)->wait();

    client.start_consuming();
    client.subscribe(ACK_TOPIC, 1)->wait();

    string bericht = "001;PALLET_OVERDRACHT";

    auto verzoek = mqtt::make_message(REQUEST_TOPIC, bericht);
    verzoek->set_qos(1);

    client.publish(verzoek)->wait();

    cout << "Overdrachtsverzoek verstuurd via MQTT." << endl;

    auto antwoord = client.try_consume_message_for(chrono::seconds(10));

    if (antwoord)
    {
        cout << "Bevestiging ontvangen: "
            << antwoord->to_string() << endl;
    }
    else
    {
        cout << "Geen bevestiging ontvangen." << endl;
    }

    client.stop_consuming();
    client.disconnect()->wait();
}

// main program

int main(int argc, char* argv[])
{
    if (argc < 2)
    {
        cout << "Gebruik een van de volgende opties:" << endl;
        cout << "tcp-server" << endl;
        cout << "tcp-client" << endl;
        cout << "mqtt-server" << endl;
        cout << "mqtt-client" << endl;
        return 1;
    }

    string keuze = argv[1];

    if (keuze == "tcp-server")
    {
        tcpServer();
    }
    else if (keuze == "tcp-client")
    {
        tcpClient();
    }
    else if (keuze == "mqtt-server")
    {
        mqttServer();
    }
    else if (keuze == "mqtt-client")
    {
        mqttClient();
    }
    else
    {
        cout << "Ongeldige keuze." << endl;
        return 1;
    }

    return 0;
}
```