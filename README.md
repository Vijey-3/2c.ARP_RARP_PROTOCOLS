# 2c.SIMULATING ARP /RARP PROTOCOLS
### NAME : VIJEY K S
### REG.NO : 212223040239
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
### Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
### Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
### SERVER.PY:
~~~
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"e0:2e:ob:7c","165.165.79.1":"7c:0b:2e:e0"};
while True:
    ip=c.recv(1024).decode()
    try:
     c.send(address[ip].encode())
    except KeyError:
     c.send("Not Found".encode())
~~~
### CLIENT.PY:
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
~~~

## OUTPUT - ARP
### CLIENT.PY:
![image](https://github.com/user-attachments/assets/1389abd6-4959-4a89-8b85-bd8694ab0e9f)
### SERVER.PY:
![image](https://github.com/user-attachments/assets/000f1075-92ac-4735-b181-0fd5023c14c6)

## PROGRAM - RARP
### CLIENT.PY:
~~~
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"e0:2e:ob:7c":"192.168.1.100","7c:0b:2e:e0":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
    c.send(address[ip].encode())
 except KeyError:
    c.send("Not Found".encode())
~~~
### SERVER.PY:
~~~
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
~~~
## OUTPUT -RARP
### CLIENT.PY:
![image](https://github.com/user-attachments/assets/cb783493-8eba-4ae8-99a8-39420e0b0ff9)
### SERVER.PY:
![image](https://github.com/user-attachments/assets/d76b2534-877b-4bdf-aeed-f2d728474875)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
