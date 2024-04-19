# Ex No:2c SIMULATING ARP /RARP PROTOCOLS
## Name: Sri Vignesh G
## Reg No: 21223040204

## AIM
To write a python program for simulating ARP/RARP protocols using TCP.

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

## PROGRAM - ARP:
### Client.py:
```
import socket
s=socket.socket()
s.bind(('localhost',8005))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except:
        c.send("Not Found".encode())
```
### Server.py:
```
import socket
s=socket.socket()
s.connect(('localhost',8005))
while True:
    ip=input("Enter Logical Address:")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUTPUT - ARP:
### Client window:
![Screenshot 2024-04-19 224854](https://github.com/SriVignesh-G/2c.ARP_RARP_PROTOCOLS/assets/147576510/0ac17c98-594d-45b4-8143-79d5e343367b)

### Server window:
![Screenshot 2024-04-19 224905](https://github.com/SriVignesh-G/2c.ARP_RARP_PROTOCOLS/assets/147576510/8a7d260a-ffea-4eb7-a4ba-f378ff8d92ba)

## PROGRAM - RARP:
### Client.py:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
    c.send(address[ip].encode())
 except KeyError:
    c.send("Not Found".encode())
```
### Server.py:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUTPUT -RARP:
### Client Window:
![Screenshot 2024-04-19 225447](https://github.com/SriVignesh-G/2c.ARP_RARP_PROTOCOLS/assets/147576510/a920c788-b68a-48ed-8334-54f608683f55)

### Server Window:
![Screenshot 2024-04-19 225453](https://github.com/SriVignesh-G/2c.ARP_RARP_PROTOCOLS/assets/147576510/1a0f854f-bfbb-40c1-843d-fe03b9b0d8f5)


## RESULT
Thus, the python program for simulating ARP/RARP protocols using TCP was successfully 
executed.
