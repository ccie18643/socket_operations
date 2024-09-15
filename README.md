# Socket Operations

## UDP

### Simple 'sendto()' with no binding or connecting
```
import socket
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.sendto(b"dupa", ("1.1.1.1", 54321))
```
```
ss -u
Recv-Q                   Send-Q                                       Local Address:Port                                         Peer Address:Port
```
```
tshark -n host 1.1.1.1
Running as user "root" and group "root". This could be dangerous.
Capturing on 'br0'
    1 0.000000000 192.168.1.10 → 1.1.1.1      UDP 46 42932 → 54321 Len=4
```

### Bind to specific port, then 'sendto()' with no connecting
```
import socket
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.bind(("0.0.0.0", 12345))
sock.sendto(b"dupa", ("1.1.1.1", 54321))
```
```
ss -u
Recv-Q                   Send-Q                                       Local Address:Port                                         Peer Address:Port
```
```
tshark -n host 1.1.1.1
Running as user "root" and group "root". This could be dangerous.
Capturing on 'br0'
    1 0.000000000 192.168.1.10 → 1.1.1.1      UDP 46 12345 → 54321 Len=4
```

### Bind to specific address & port, then 'sendto()' with no connecting
```
import socket
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.bind(("192.168.1.10", 12345))
sock.sendto(b"dupa", ("1.1.1.1", 54321))
```
```
ss -u
Recv-Q                   Send-Q                                       Local Address:Port                                         Peer Address:Port
```
```
tshark -n host 1.1.1.1
Running as user "root" and group "root". This could be dangerous.
Capturing on 'br0'
    1 0.000000000 192.168.1.10 → 1.1.1.1      UDP 46 12345 → 54321 Len=4
```
