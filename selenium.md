访问操作
```python
from time import sleep
from selenium import webdriver

driver = webdriver.Chrome() 
driver.get("http://www.baidu.com") //get请求
sleep(3)
driver.quit() //退出浏览器窗口
```