### yield是一个特殊的迭代器

```python
def create_num(all_num):
    a, b = 0, 1
    current_num = 0

    while current_num < all_num:
        yield a
        a, b = b, a + b
        current_num += 1

obj = create_num(10)

while True:
    try:
        ret = next(obj)
        print(ret)
    except Exception as e:
        break
```

### 获取return的值

```python
def create_num(all_num):
    a, b = 0, 1
    current_num = 0

    while current_num < all_num:
        yield a
        a, b = b, a + b
        current_num += 1
    return 'ok'

obj = create_num(2)

while True:
    try:
        ret = next(obj)
        print(ret)
    except Exception as ret:
        print(ret.value)
        break
```
