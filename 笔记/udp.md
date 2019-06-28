### udp_sendto

```python
import socket


def main():

    # 1.创建套接字
    udp_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

    localAddr = ('', 6666)
    udp_socket.bind(localAddr)

    target_IP = input('take in target ip:')
    target_Port = int(input('take in target port:'))

    # 2.发送数据
    sendto_data = input('请输入发送的信息:')
    udp_socket.sendto(sendto_data.encode('gbk'), (target_IP, target_Port))

    # 3.关闭套接字
    udp_socket.close()


if __name__ == '__main__':
    main()
```


### udp_recvfrom

```python
from socket import *


def main():

    # 1.创建套接字
    udp_socket = socket(AF_INET, SOCK_DGRAM)

    # 2.绑定端口
    localAddr = ('', 6666)
    udp_socket.bind(localAddr)

    while True:
        # 3.接收数据
        recv_data = udp_socket.recvfrom(1024)

        if recv_data[0].decode('gbk') == 'exit':
            print('程序结束')
            exit()

        # 4.打印数据
        print('来自%s:%s' % (recv_data[1][0], recv_data[1][1]))
        print('信息:%s' % recv_data[0].decode('gbk'))

    # 5.关闭套接字
    udp_socket.close()


if __name__ == '__main__':
    main()
```
