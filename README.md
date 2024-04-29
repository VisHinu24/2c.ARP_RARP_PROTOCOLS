# 2c.SIMULATING ARP /RARP PROTOCOLS
## Name : H Vishinu
## Reg No : 212223220124
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
Client :
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}
while True:
    ip= c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not found".encode())

```

Server :
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    mac= input("Enter IP address:")
    s.send(mac.encode())
    print("MAC address :",s.recv(1024).decode())


```
## OUPUT - ARP
Client :
![Screenshot 2024-04-22 200028](https://github.com/VisHinu24/2c.ARP_RARP_PROTOCOLS/assets/144244396/6878836d-ebb4-4ae2-8367-bf4b24edd402)

Server :
![Screenshot 2024-04-22 200022](https://github.com/VisHinu24/2c.ARP_RARP_PROTOCOLS/assets/144244396/cdf58c9a-634e-4d6b-a96e-9572399fe091)




## PROGRAM - RARP
Client :
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"165.165.80.80","8A:BC:E3:FA":"165.165.79.1"}
while True:
    mac= c.recv(1024).decode()
    try:
        c.send(address[mac].encode())
    except KeyError:
        c.send("Not found".encode())
```
Server :
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    mac= input("Enter logical address:")
    s.send(mac.encode())
    print("IP address :",s.recv(1024).decode())

```


## OUPUT -RARP
Client :
![Screenshot 2024-04-22 195757](https://github.com/VisHinu24/2c.ARP_RARP_PROTOCOLS/assets/144244396/da308bde-2191-49c3-953d-4b4d7663a2b1)

Server :
![Screenshot 2024-04-22 195802](https://github.com/VisHinu24/2c.ARP_RARP_PROTOCOLS/assets/144244396/c2d52198-3557-4c97-b092-b7b890437c44)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
