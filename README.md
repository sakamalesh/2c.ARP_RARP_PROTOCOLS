# 2c.SIMULATING ARP /RARP PROTOCOLS
## Name: Kamalesh
## Reg no:212223040083
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
## Client:
'''

    import socket
    s=socket.socket()
    s.bind(('localhost',8000))
    s.listen(5)
    c,addr=s.accept()
    address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
    while True:
        ip=c.recv(1024).decode()
        try:
            c.send(address[ip].encode())
        except KeyError:
            c.send("Not Found".encode())    
'''
## Server:
'''

    import socket
    s=socket.socket()
    s.connect(('localhost',9000))
    while True:
        ip=input("Enter mac address: ")
        s.send(ip.encode())
        print("Logical address",s.recv(1024).decode())
'''
## OUPUT - 
## Client:
![Screenshot 2024-09-14 104525](https://github.com/user-attachments/assets/5cb6fc22-c0ee-41f9-ac18-94bda88372ec)

## PROGRAM - RARP
## Client:
'''

    import socket
    s=socket.socket()
    s.bind(('localhost',9000))
    s.listen(5)
    c,addr=s.accept()
    address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}
    while True:
        ip=c.recv(1024).decode()
        try:
            c.send(address[ip].encode())
        except KeyError:
            c.send("Not found".encode())    
'''
## Server:
'''

    import socket
    s=socket.socket()
    s.connect(('localhost',9000))
    while True:
        ip=input("Enter mac address: ")
        s.send(ip.encode())
        print("Logical address",s.recv(1024).decode())
  '''
## OUPUT -RARP
## Client:
![Screenshot 2024-09-14 104753](https://github.com/user-attachments/assets/6b39c1aa-297c-40e3-ac19-66b4b4c84bbc)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
