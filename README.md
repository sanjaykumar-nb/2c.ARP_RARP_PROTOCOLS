# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
```
ARP-CLIENT PROGRAM
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"169.254.13.114":"CC.47:40:E2:A0:9E"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

ARP-SERVER PROGRAM
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input('Enter Logical Address:')
    s.send(ip.encode())
    print('MAC  address',s.recv(1024).decode())
```
## OUPUT - ARP
ARP-CLIENT
![alt text](<Screenshot 2024-04-11 client.png>)
ARP-SERVER
![alt text](<Screenshot 2024-04-11 sever.png>)
## PROGRAM - RARP
```
RARP-CLIENT PROGRAM
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())


RARP-SERVER PROGRAM
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter the MAC Address:")
    s.send(ip.encode())
    print("Logical addres",s.recv(1024).decode())
```
## OUPUT -RARP
RARP-CLIENT
![alt text](<Screenshot 2024-04-11 rclient.png>)

RARP-SERVER
![alt text](<Screenshot 2024-04-11 rserver.png>)
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
