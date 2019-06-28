简单来说，就是有一个地方专门存放信息，不同的进程之间在同一个地方存取信息，达到信息的传达
```python
import multiprocessing
import time


def write_data(q):
    data = [11, 22, 33, 44]

    for temp in data:
        q.put(temp)

    print('下载完毕')


def analysis(q):
    """数据处理"""

    waitting = list()

    while True:
        data = q.get()
        waitting.append(data)

        if q.empty():
            print('下载完毕')
            break

    # for x in waitting:
    #   print(x)

    print(waitting)


def main():
    # 创建队列
    q = multiprocessing.Queue(3)

    p1 = multiprocessing.Process(target=write_data, args=(q,))
    p2 = multiprocessing.Process(target=analysis, args=(q,))

    p1.start()
    time.sleep(1)
    p2.start()


if __name__ == '__main__':
    main()

```