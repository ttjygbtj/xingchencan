---
title: excel
date: 2021-08-25 20:40:17
tags: Python
categories:
- [学习, Python]
---

[利用xlwings写入一行或一列Excel数据](https://www.cnblogs.com/rongge95500/p/13201864.html)

```python mark:6,24,26,74
from xlwt import *
import os
import numpy as np
import copy
# 创建一个工作簿
def size_format(size):
    if size < 1e3:
        return '%.1fB' % size
    elif size < 1e6:
        return '%.1fKB' % (size / 1e3)
    elif size < 1e9:
        return '%.1fMB' % (size / 1e6)
    elif size < 1e12:
        return '%.1fGB' % (size / 1e9)
    elif size < 1e15:
        return '%.1fTB' % (size / 1e12)
numT=16
stage='-norm'
if stage=='-norm':
    resDir='./res-norm'
else:
    resDir='./res'

wb = Workbook(encoding='utf-8')
ws = wb.add_sheet("sheet1")
ws.write(0, 0, u"图片名称")
ws.write(0, 1, u"原图大小")
for i in range(2,numT+1):
    ws.write(0, i, i-1)


dirs=os.listdir(resDir)
dirs.sort()

tmpDirs=copy.deepcopy(dirs)

for i,ele in enumerate(tmpDirs):
    if ele[0]=='.':
        dirs.remove(ele)
    elif ele.split('.')[-1]=='png':
        dirs.remove(ele)

excel_row = 1

total_size=np.zeros((numT))
for ele in dirs:
    resEleDir=os.path.join(resDir,ele)
    pics=os.listdir(resEleDir)
    print(ele)
    assert(len(pics)==numT)
    picName=ele

    sizeList=[] #0-24 25 eles
    sizeList.append(size_format(os.path.getsize(os.path.join(resEleDir,ele+'-source.png'))))
    total_size[0]+=os.path.getsize(os.path.join(resEleDir,ele+'-source.png'))

    for i in range(1,16):
        sizeList.append(size_format(os.path.getsize(os.path.join(resEleDir,ele+'-{}.png').format(i))))
        total_size[i]+=os.path.getsize(os.path.join(resEleDir,ele+'-{}.png').format(i))

    ws.write(excel_row, 0, picName)
    ws.write(excel_row, 1, sizeList[0])
    for i in range(2,numT+1):
        ws.write(excel_row, i, sizeList[i-1])
    excel_row += 1
    
ws.write(excel_row, 0, u"总大小")
for i in range(0,numT):
    size=size_format(total_size[i])
    ws.write(excel_row, i+1, size)

excel_row+=1

ws.write(excel_row, 0, u"压缩比")
for i in range(0,numT):
    delta='%.2f%%' % (total_size[i]/total_size[0] * 100)
    print(delta)
    ws.write(excel_row, i+1, delta)
wb.save('fileSizeAnalyse{}.xlsx'.format(stage))
```



6,24,26,74