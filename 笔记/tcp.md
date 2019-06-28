### tcp_client
```python
import socket


def main():

    # 创建套接字
    tcp_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    # 输入服务器信息
    server_IP = input('take in server_IP:')
    server_Port = int(input('take in server_Port:'))
    localAddr = (server_IP, server_Port)

    # 创建链接
    tcp_socket.connect(localAddr)

    # 传输的信息内容
    info = 'test info'

    # 发送数据
    tcp_socket.send(info.encode('gbk'))

    # 关闭套接字
    tcp_socket.close()


if __name__ == '__main__':
    main()
```

### tcp_server
```python
import socket


def main():
    print('程序开始！')
    # 创建套接字
    tcp_server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    # 绑定端口
    localAddr = ('', 6666)
    tcp_server.bind(localAddr)

    # 主动监听
    tcp_server.listen(128)

    while True:

        print('等待新的客户链接')

        # 等待客户端链接
        new_client_socket, client_addr = tcp_server.accept()

        # 接收信息
        print('一个新的客户已经到来！')
        while True:
            recv_data = new_client_socket.recv(1024)
            recv = recv_data.decode('utf-8')
            if recv:
                print('来自IP%s  端口%s 的信息是：' %
                      (str(client_addr[0]), str(client_addr[1])))
                print(recv)

                # 给客户端回复信息
                send_data = '信息已经收到'
                new_client_socket.send(send_data.encode('utf-8'))
            else:
                break

        new_client_socket.close()
        print('服务完毕！！！')
    tcp_server.close()


if __name__ == '__main__':
    main()

```