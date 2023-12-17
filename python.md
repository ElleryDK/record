## 读取文件
```python
f = open("sxl.txt")
line = f.readline()
while line:
    print (line)
    print(type(line))
    line = f.readline()
f.close()
```