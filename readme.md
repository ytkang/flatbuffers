Forked from [google/flatbuffers]

### Goal
Use "--force-defaults" option to emit default values into final bytes.
Table Start function will add all default values into builder.

### Supported Languages
- Java/C#
- Golang

### Example
flatc -g -n packet.fbs --force-defaults

```fbs
// packet.fbs
namespace packet;

table Packet {
  id:uint16=1234;
}
``` 

Packet.go
```go
...
func PacketStart(builder *flatbuffers.Builder) {
	builder.StartObject(1)
	builder.PrependUint16Slot(0, 1234, 0)
}
...
```

Packet.cs
```csharp
...
public static void StartPacket(FlatBufferBuilder builder) {
	builder.StartTable(1);
	builder.AddUshort(0, 1234, 0);
  }
...
```
will be generated.

[google/flatbuffers]: https://github.com/google/flatbuffers
