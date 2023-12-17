<<<<<<< HEAD
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
title_index = col_list.index('标题')
type_index = col_list.index('类型')
module_index = col_list.index('模块')
type_list = ['pc','移动','PC']
module_list = ['知识']
for i in range(1,m_sheet.max_row):
    tmp_list = []
    for cell in list(m_sheet.rows)[i]:
        tmp_list.append(cell.value)
    m_title = tmp_list[title_index]
    m_type = tmp_list[type_index]
    m_module = tmp_list[module_index]
    if(m_type==None or isConformat(type_list,m_type)==None):
        chose = isConformat(type_list,m_title)
        m_sheet.cell(row=i+1,column=type_index+1,value=chose)
    if(m_module ==None):
        chose = isConformat(module_list,m_title)
        m_sheet.cell(row=i+1,column=module_index+1,value=chose)
        

workbook.save(r'D:\xlsx\new.xlsx')


=======
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
title_index = col_list.index('标题')
type_index = col_list.index('类型')
module_index = col_list.index('模块')
type_list = ['pc','移动','PC']
module_list = ['知识']
for i in range(1,m_sheet.max_row):
    tmp_list = []
    for cell in list(m_sheet.rows)[i]:
        tmp_list.append(cell.value)
    m_title = tmp_list[title_index]
    m_type = tmp_list[type_index]
    m_module = tmp_list[module_index]
    if(m_type==None or isConformat(type_list,m_type)==None):
        chose = isConformat(type_list,m_title)
        m_sheet.cell(row=i+1,column=type_index+1,value=chose)
    if(m_module ==None):
        chose = isConformat(module_list,m_title)
        m_sheet.cell(row=i+1,column=module_index+1,value=chose)
        

workbook.save(r'D:\xlsx\new.xlsx')


>>>>>>> 09cc311e69e38f6cf755417af94e80c050ce86c6
```