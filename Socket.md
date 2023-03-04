## Socket

Socket - пара домен-порт через которые осуществляется взаимодействие между клиентом и сервером

С сокетом в Питоне можно работать, как с файлом — считывать его и получать данные.  
Сокет содержит в себе два параметра: IP-адрес и порт. Сервер, принимая соединение присваивает своему сокету определенный порт.  
Порт — число в заголовках пакетов TCP, UDP, указывающее, для какого приложения в системе предназначен данный IP-пакет.

Вот основные функции и методы:

- .socket  
- .bind()  
- .listen()  
- .accept()  
- .connect()  
- .connect_ex()  
- .send()  
- .recv()  
- .close()  

```
python
import socket

#domain:5000

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)   #IPv4, TCP
server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)#для повторного использования того же порта
server_socket.bind(('localhiost', 5000))#к какому домену и порту привязываем
server_socket.listen()

while True:
	client_socket, addr = server_socker.accept() #читает подключения, возвращает кортеж(сокет и адрес)
	print('Connect from', addr)
	
	while True:
		request = client_socket.recv(4096) #сообщение от клиента, размер буфера
		
		if not request:  #условие для прерывания этого цикла
			break
		else:
			response = 'Hello world\n'.encode() #кодируем строку в bites
			client_socket.send(response)

	client_socke.close()
```

```
python
import socket

#domain:5000

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)   #IPv4, TCP
server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)#для повторного использования того же порта
server_socket.bind(('localhiost', 5000))#к какому домену и порту привязываем
server_socket.listen()

def accept_connection(server_socket):
	while True:
		client_socket, addr = server_socker.accept() #читает подключения, возвращает кортеж(сокет и адрес)
		print('Connect from', addr)
		send_message(client_socket)
	
def send_message(client_socket):
	while True:
		request = client_socket.recv(4096) #сообщение от клиента, размер буфера
		
		if not request:  #условие для прерывания этого цикла
			break
		else:
			response = 'Hello world\n'.encode() #кодируем строку в bites
			client_socket.send(response)
	 client_socke.close()

if __main__ == '__name__':
	accept_connection(server_socket)
```

Асинхронный код можно писать 3 способами:
 - с помощью колбэков
 - с помощью генераторов
 - с помощью async await

```python
import socket

#domain:5000

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)   #IPv4, TCP
server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)#для повторного использования того же порта
server_socket.bind(('localhiost', 5000))#к какому домену и порту привязываем
server_socket.listen()

def accept_connection(server_socket):
	while True:
		client_socket, addr = server_socker.accept() #читает подключения, возвращает кортеж(сокет и адрес)
		print('Connect from', addr)
	
def send_message(client_socket):
	while True:
		request = client_socket.recv(4096) #сообщение от клиента, размер буфера
		
		if not request:  #условие для прерывания этого цикла
			break
		else:
			response = 'Hello world\n'.encode() #кодируем строку в bites
			client_socket.send(response)
	 client_socke.close()

if __main__ == '__name__':
	accept_connection(server_socket)
```
