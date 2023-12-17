## 修改单元格
```pyhon
import openpyxl as op

def isConformat(info_list,s):
    for chose in info_list:
        if(s.find(chose)!=-1):
            return chose
    return None

filename = r'D:\xlsx\origin.xlsx'
workbook = op.load_workbook(filename)
m_sheet = workbook[workbook.sheetnames[0]]
col_list = []
for cell in list(m_sheet.rows)[0]:
    col_list.append(cell.value)
m_sheet.cell(row=i+1,column=type_index+1,value=chose)
workbook.save(r'D:\xlsx\new.xlsx')
```

## 输入excel文件到数据库
```python
import xlrd
import pymysql

book = xlrd.open_workbook("student_info.xlsx")#打开需要导入数据库的excel表
sheet=book.sheet_by_name("Sheet1")

#建立一个MySQL连接
conn = pymysql.connect(
        host='localhost',
        user='root',
        passwd='root',
        db='mysql',
        port=3306,
        charset='utf8'
        )
# 获得游标
cur = conn.cursor()
# 创建插入SQL语句
query = 'insert into test0615 (学号,姓名,年龄,性别,班级,分数,排名) values (%s, %s, %s, %s, %s, %s, %s)'
# 创建一个for循环迭代读取xls文件每行数据的, 从第二行开始是要跳过标题行
for r in range(1, sheet.nrows):
      学号 = sheet.cell(r,0).value
      姓名 = sheet.cell(r,1).value
      年龄 = sheet.cell(r, 2).value
      性别 = sheet.cell(r, 3).value
      班级 = sheet.cell(r, 4).value
      分数 = sheet.cell(r, 5).value
      排名 = sheet.cell(r, 6).value
      values = (学号,姓名,年龄,性别,班级,分数,排名)
      # 执行sql语句
      cur.execute(query, values)
cur.close()
conn.commit()
conn.close()
columns = str(sheet.ncols)
rows = str(sheet.nrows)
print ("导入 " +columns + " 列 " + rows + " 行数据到MySQL数据库!")
```