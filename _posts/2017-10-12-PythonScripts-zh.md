#! /usr/bin/env python

#coding=utf-8

import os 
import time   
import datetime   

#根据是否工作日设置限制时间
if datetime.date.today().weekday()<5:
    timeLimit = 20
else:
    timeLimit = 40

#读取文本中记录的日期
f = open('E:\\thefile.txt','r+')
f_date = f.readline()
f.close

#读取系统日期，并与文本日期进行比对
#如果不相等，则清空文件，进行当日初始化
n_date = time.strftime("%d/%m/%Y")+"\n"
if f_date != n_date:
    print("sucessed")
    f = open('E:\\thefile.txt','r+')
    f.truncate()
    f.close
    f = open('E:\\thefile.txt','r+')
    f.write((n_date))
    run_time="0"
    f.write(run_time)
    f.close

#死循环语句，当且仅当运行时间大于等于限制时间时跳出循环
while 2 > 1 :
    f = open('E:\\thefile.txt','r+')
    f_date = f.readline()
    run_time = f.readline()
    run = int(run_time)
    print(run)
    time.sleep(2)
    if run<timeLimit:
        run = run + 1
        f.truncate()
        f.close
        f = open('E:\\thefile.txt','r+')
        f.write(f_date)
        run_time = str(run)
        f.write(run_time)
        f.close
    else:
        break

#关机命令       
cmd="cmd.exe /k shutdown -s -t 0";

print(cmd)
