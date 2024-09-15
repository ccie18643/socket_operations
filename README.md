# Socket Operations

## UDP

### Simple send with no binding or connecting
```
import socket
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.sendto(b"dupa", ("1.1.1.1", 12345))
```
```
793.010847311 192.168.1.10 → 1.1.1.1      UDP 46 41689 → 12345 Len=4
```
