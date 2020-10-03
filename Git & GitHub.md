# Git & GitHub

![image-20201001154310997](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001154310997.png)

**目的**：借助GitHub托管项目代码

![image-20201001155159439](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001155159439.png)



![image-20201001155216307](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001155216307.png)

翻墙（Shadowsocks）：因为GitHub在国外服务器所以访问较慢或无法访问，故xx；

![image-20201001160255110](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001160255110.png)

![image-20201001160445940](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001160445940.png)





#### 04、github使用（GitHub Issues）





### Git

------

- 通过git管理GitHub托管项目代码
- 下载安装

![image-20201001163306211](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001163306211.png)





![image-20201001163526740](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001163526740.png)

![image-20201001163622637](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001163622637.png)



![image-20201001164800369](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001164800369.png)





![image-20201001164937925](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001164937925.png)



向仓库中添加文件的流程

![image-20201001165321581](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001165321581.png)

git add：从工作区add到暂存区；

git status：看此时的状态；

git commit -m：提交描述；



![image-20201001165447999](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001165447999.png)



~~~java
	
	git config --glocal user.name'用户名'
    
    git config --glocal user.name'邮箱'
~~~





ls：当前文件；

pwd：当前文件目录；

clear：清除当前查询信息；

mkdir text：创建文件夹，且文件夹名为“text”



- 在文件内初始化git（创建git仓库）

    ~~~java
    cd text
        git init
        
        //添加文件
        touch 文件名（要有带后缀名）
        //添加文件到暂存区
        git add 文件名（有后缀）
        
        
    ~~~

    



#### git管理远程仓库

- 使用远程仓库的目的
- 作用：备份，实现代码共享集中化管理



![image-20201001171531467](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001171531467.png)



#### git克隆操作

目的：将远程仓库（github对应的项目）复制到本地

- git clone 仓库地址
- ![image-20201001171751694](C:\Users\86139\AppData\Roaming\Typora\typora-user-images\image-20201001171751694.png)

（仓库地址）



添加文件

~~~java
//1、创建文件
touch test1.php
    //2、添加到暂存区
    git add test1.php
    //3、提交到仓库
    git commit -m '提交描述'
    
    git基础设置
    //1、设置用户名
    git config --global user.name 'Blood-Zone'
    //2、设置用户名邮箱
    git config --global user.email '1292795269@qq.com'
    //3、查看设置
    git config --list
~~~



to