# python
（1）水仙花数：（10-1000）；

#!usr/bin/python

#coding:utf-8

for i in range(10,1000):  

    sum=0 #各个位数的立方和  

    temp=i  

    while temp:  

        sum=sum+(temp%10)**3   #累加  

        temp//=10   #地板除  

    if sum==i:  

        print(i) 



（2）线程代码：

import threading

import time



#input = input("")

#int_i=int(input)



N=int(input())

def fun_1():

    line_a=0

    while True:

        print ("AAA--- %d" % line_a)

        line_a +=1

        time.sleep(1)

    

def fun_2(n):

    line_b=0

    while True:

        print ("BBB--- %d" % line_b)

        line_b +=1

        time.sleep(n)





if __name__=='__main__':

    t1=threading.Thread(target=fun_1)

    t2=threading.Thread(target=fun_2,args=(N,))

    t1.start()

t2.start()



（3.1）#左上三角格式输出九九乘法表（注意缩进）

for i in range(1,10):

    for j in range(i,10):

        print("%d*%d=%2d" % (i,j,i*j),end=" ")

    print("")



（3.2）#左下三角格式输出九九乘法表（注意缩进）

for i in range(1,10):

     for j in range(1,i+1):

         print("%d*%d=%2d" % (i,j,i*j),end=" ")

     print (" ")



文件处理读取文件：

（4.1） #读取文件内容：

f = open('test.txt','r',encoding='UTF-8')

  #（会自己在python代码存放的地方创建test.txt文件，可自己在里面添加内容）

print(f.read())            #读取所有

#print(f.read(5))          #读取5个字符串

（4.2）

#truncate() 方法用于从文件的首行首字符开始截断，截断文件为 size 个字符，无 size 表示从当前位置截断；后面的所有字符被删除，其中 Widnows 系统下的换行代表2个字符大小

语法：fileObject.truncate( [ size ])

参数： size -- 可选，如果存在则文件截断为 size 字节



f = open('test.txt','r+',encoding='UTF-8')  #读写模式

f.truncate(6)                        #截取6个字节

print(f.read())



（4.3）

#r：读模式，文件不存在时不会创建新文件，文件的指针将会放在文件的开头。默认模式

f = open('test.txt','r',encoding='UTF-8')       #encoding是转码的意思，告诉解释器以UTF-8的编码格式。不指定的话默认是以操作系统的编码为准的

print(f.read())                                 #读所有，bytes--decode(utf-8)--str

#print(f.read(5))                              #读取5个字符串（b模式下单位是字节）

# print(f.readlines())                          #读所有，将结果放入列表中

# print(f.readline())                           #一次读一行

# print(f.readline(),end='')                    #一次读一行，并指定结束符，默认结束符为

#f.close()                                      #关闭文件

（4.4）

#w：写模式，文件存在时则覆盖，文件不存在时创建新文件

f = open('test.txt','w',encoding='UTF-8')

f.write('第一行 \n')                           #换行需要添加换行符

f.write('第二行\n')



（4.5）

#a：追加模式。如果该文件已存在，文件指针将会放在文件的结尾，新的内容将会被写

#入到已有内容之后。如果该文件不存在，创建新文件进行写入

f = open('test.txt','a',encoding='UTF-8')

f.write('追加的内容')

# print(f.tell())                             #打印光标当前位置，单位是字节

# f.flush()                                   #使内存的内容刷新至文件

# f.seek(0)                                   #a模式光标会定位在文件尾部，这里重新定位一下光标位置

# print(f.tell())                             #输出光标位置为0

#f.close()



#注意查看test.txt文件的内容。

（4.6）

#rb：二进制格式的读模式。文件指针将会放在文件的开头

f = open('test.txt','rb')

print(f.read())

# print(f.read().decode('UTF-8'))       #可以decode，输出字符串

#f.close()



#执行结果：

#b'\xe7\xac\xac\xe4\xb8\x80\xe8\xa1\x8c\r\n\xe7\xac\xac\xe4\xba\x8c\xe8\xa1\x8c\r\n\xe7\xa#c\xac\xe4\xb8\x89\xe8\xa1\x8c'



（4.7）

#wb：二进制格式的写模式。文件存在时则覆盖，文件不存在时创建新文件

f = open('test.txt','wb')

f.write('你好'.encode('UTF-8'))         #字符串是Unicode编码，不能直接作为bytes类型写入，需要encode

#f.close()

（4.8）注释：

ab：二进制格式的追加模式。如果该文件已存在，文件指针将会放在文件的结尾，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入

r+：读写模式。文件指针将会放在文件的开头。

w+：读写模式。文件存在时则覆盖，文件不存在时创建新文件

a+：读写模式。如果该文件已存在，文件指针将会放在文件的结尾。文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写

rb+：二进制格式的读写模式。文件指针将会放在文件的开头

wb+：二进制格式的读写模式。文件存在时则覆盖，文件不存在时创建新文件

ab+：二进制格式的追加模式。如果该文件已存在，文件指针将会放在文件的结尾。如果该文件不存在，创建新文件用于读写

<4.9>

f = open('test.txt','r',encoding='UTF-8')

print(f.read())                     #读取完所有内容，此时光标在文件最后

f.seek(3)                           #从文件开头位置往后偏移3个字节,3个字节代表一个汉字

print(f.read())

print(f.tell())                     #打印光标当前位置

(4.10)

1、文件拷贝

with open('test.txt','r',encoding='UTF-8') as read_f,open('test2.txt','w',encoding='UTF-8') as write_f:

    for line in  read_f:                    #循环读取test.txt文件内容

        write_f.write(line)                 #写入到test2.txt（test2.txt会被自动创建）
五socket通信：
server.py
#!/usr/bin/python
#coding:utf-8
import socket               # 导入 socket 模块
import time
s = socket.socket()         # 创建 socket 对象
host = socket.gethostname() # 获取本地主机名
port = 10000                # 设置端口
s.bind((host, port))        # 绑定端口

s.listen(5)                 # 等待客户端连接
while True:
    c, addr = s.accept()     # 建立客户端连接。
    print '连接地址：', addr
   # c.send('欢迎访问菜鸟教程！')
    c.send (time.asctime( time.localtime(time.time()) ))
    c.close()                # 关闭连接
client.py
import socket               # 导入 socket 模块

s = socket.socket()         # 创建 socket 对象
host = socket.gethostname() # 获取本地主机名
port = 10000               # 设置端口好

s.connect((host, port))
print s.recv(1024)
s.close()  
六os.py
#!/usr/bin/python
#_*_ coding:UTF-8 _*_
#通信
import os
import time
import socket
import threading
def show():
        print("# b:9600")
        print("# d:8")
        print("# p:0")
        print("# s:1")
        print("# f:0")
        
if __name__=='__main__':
        #print("OK")
        show()

vb0=9600
vd0=8
vp0=0
vs0=1

vb=vb0
vd=vd0
vp=vp0
vs=vs0

def show():
        print("=== Serial Com===")
        print("# b: %s"%vb)
        print("# d: %s"%vd)
        print("# p: %s"%vp)
        print("# s: %s"%vs)
if __name__=='__main__':
        os.system("cls")
        while True:
                show()
                print("-----------")
                print("# Input 'Q' to Quit")
                print("# Input 'D' to Set Default")
                print("# Input 'E' to Edit")
                print("# Input 'S' to Save\n")
                input=raw_input("PLS Input: ")
                os.system("cls")
                if input == 'Q' or input=='q':
                        break;
                elif input == 'D' or input=='d':
                        print("OK: %s"%input)
                        
                elif input == 'D' or input=='d':
                        print("OK: %s"%input)
                elif input == 'D' or input=='d':
                        print("OK: %s"%input)
                else:
                        pass
                
七.正则
#!/usr/bin/python3
 
import re
 
line = "Cats are smarter than dogs";
 
matchObj = re.match( r'dogs', line, re.M|re.I)
if matchObj:
   print ("match --> matchObj.group() : ", matchObj.group())
else:
   print ("No match!!")
 
matchObj = re.search( r'dogs', line, re.M|re.I)
if matchObj:
   print ("search --> matchObj.group() : ", matchObj.group())
else:
   print ("No match!!")#!/usr/bin/python3
 
import re
 
line = "Cats are smarter than dogs";
 
matchObj = re.match( r'dogs', line, re.M|re.I)
if matchObj:
   print ("match --> matchObj.group() : ", matchObj.group())
else:
   print ("No match!!")
 
matchObj = re.search( r'dogs', line, re.M|re.I)
if matchObj:
   print ("search --> matchObj.group() : ", matchObj.group())
else:
   print ("No match!!")
