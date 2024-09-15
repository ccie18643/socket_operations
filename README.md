# Socket Operations

## UDP

### Simple send with no binding or connecting
```
import socket
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.sendto(b"dupa", ("1.1.1.1", 12345))
```
