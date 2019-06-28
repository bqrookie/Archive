**threading模块中定义了Lock类，可以方便的处理锁定**

```python
# 创建锁
mutex = threading.Lock()

# 锁定
mutex.acquire()

# 解锁
mutex.release()
```