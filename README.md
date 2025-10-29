# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM

CLIENT
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True:
        print('Receiving data...')
        data = s.recv(1024)
        print(f'data = {data}')
        if not data:
            break
        f.write(data)
print('Successfully received the file')
s.close()
print('Connection closed')

```

SERVER
```
import socket
port = 60000
s = socket.socket() 
host = socket.gethostname()  
s.bind((host, port))
s.listen(5)
print("Server listening...")
while True:
    conn, addr = s.accept()
    print('Got connection from', addr)
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename = 'mytext.txt'  
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print('Sent', repr(l))
            l = f.read(1024)
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
## OUPUT

<img width="1527" height="954" alt="image" src="https://github.com/user-attachments/assets/2c2d9b28-664d-4d3b-96f9-761c3e5224f0" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
