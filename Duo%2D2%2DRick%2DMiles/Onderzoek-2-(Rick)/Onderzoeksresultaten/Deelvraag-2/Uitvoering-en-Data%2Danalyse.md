# Uitvoering
In de C++ simulatie is de payload opgebouwd uit identieke overdrachtsdata (`robot_id`, `status`, `transfer_zone`). De binaire C++ `struct` (figuur 1) heeft een vaste geheugenomvang van 36 bytes (via `sizeof`), terwijl het tekstuele JSON-serialisatieformaat (figuur 2) een lengte kent van 56 bytes. Dit vertegenwoordigt een data-overhead reductie van ruim 35% in het voordeel van de binaire struct.

# Analyse


# Bijlagen
```cpp
struct RobotTransferPacket {
    char robot_id[16];
    char status[16];
    int transfer_zone;
};

RobotTransferPacket struct_message{};
std::strncpy(struct_message.robot_id, "Robot_A", sizeof(struct_message.robot_id));
std::strncpy(struct_message.status, "done", sizeof(struct_message.status));
struct_message.transfer_zone = 1;
```
(Figuur 1: Overdrachtsdata in C++ binary struct format)


```cpp
const std::string json_message = R"({"robot_id":"Robot_A","status":"done","transfer_zone":1})";
```

