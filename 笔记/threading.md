# Python3 线程中常用的两个模块为：

*   _thread
*   threading(推荐使用)

thread 模块已被废弃。用户可以使用 threading 模块代替。所以，在 Python3 中不能再使用"thread" 模块。为了兼容性，Python3 将 thread 重命名为 "_thread"。


Python中使用线程有两种方式：**函数**、**用类来包装线程对象**。

**函数**
```python
import time
import threading


def thread1(count):
    for x in range(count):
        print('Thread-1:  %d' % x)
        time.sleep(1)


def thread2(count):
    for x in range(count):
        print('Thread-2:  %d' % x)
        time.sleep(1)

try:
    Thread1 = threading.Thread(target=thread1, args=(5,))
    Thread2 = threading.Thread(target=thread2, args=(5,))

    Thread1.start()
    Thread2.start()
except Exception as e:
    print('Error:无法启动线程')

```


**用类来包装线程对象**
```python
# coding=utf-8
import threading
import time

exitFlag = 0


class myThread (threading.Thread):

    def __init__(self, threadID, name, counter):
        threading.Thread.__init__(self)
        self.threadID = threadID
        self.name = name
        self.counter = counter

    def run(self):
        print("开始线程：" + self.name)
        print_time(self.name, self.counter, 5)
        print("退出线程：" + self.name)


def print_time(threadName, delay, counter):
    while counter:
        if exitFlag:
            threadName.exit()
        time.sleep(delay)
        print("%s: %s" % (threadName, time.ctime(time.time())))
        counter -= 1

# 创建新线程
thread1 = myThread(1, "Thread-1", 1)
thread2 = myThread(2, "Thread-2", 2)

# 开启新线程
thread1.start()
thread2.start()
thread1.join()
thread2.join()
print("退出主线程")

```