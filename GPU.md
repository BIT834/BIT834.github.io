# 834科学计算指北

## 一、连接服务器
### 1. 软件需求
 windows环境：[putty](http://www.putty.org/)

### 2. 输入IP并登陆
内网地址：10.108.14.139 (暂)     端口：22
外网地址：bit834.tk                       端口：222
![登陆](https://i.imgur.com/fHwmBnp.png)

### 3. 使用默认管理账户登陆
账号：bit834		密码：bit834(*密码的输入不会显示)
![默认账户](https://i.imgur.com/z7M3I7Q.png)

## 二、 创建新用户
### 1. 创建用户
使用adduser创建用户

    sudo adduser XXX
![enter image description here](https://i.imgur.com/cG6MeYp.png)
输入密码并确认
![enter image description here](https://i.imgur.com/1uHaQNe.png)
依次回车，完成用户建立
![enter image description here](https://i.imgur.com/AeFP5hd.png)

### 2. 添加管理员权限
使用以下代码为创建的用户添加管理员权限

    sudo sh -c "echo 'XXX ALL=(ALL:ALL) ALL' >> /etc/sudoers"
![添加管理员权限](https://i.imgur.com/7s85jaV.png)

### 3. 将用户加入docker组
使用以下代码将添加的用户加入docker组

    sudo usermod -aG docker XXX

### 4. 创建samba账号
samba用于和windows系统共享文件，使用以下代码创建同名的samba账号并创建密码(*密码可以和系统密码不同)

    sudo smbpasswd -a XXX
   ![创建samba账号](https://i.imgur.com/jkyf1id.png)

## 三、 使用远程桌面登陆
### 1. 远程桌面
使用windows远程桌面连接服务器
内网地址：10.108.14.139(暂)
外网地址：暂不支持
![远程桌面](https://i.imgur.com/CGfbX9z.png)

### 2. 用户登陆
使用新创建的用户登陆服务器
![登陆服务器](https://i.imgur.com/ErV8HmC.png)
使用默认桌面设置
![桌面设置](https://i.imgur.com/YEduZhj.png)

### 3. 使用
开始使用

## 四、 本地文件共享
### 1. 映射服务器目录到本地(推荐，只支持内网)
使用samba将服务器磁盘映射到本地windows系统中(*以windows10为例)
#### 1.1 打开资源管理器
![资源管理器](https://i.imgur.com/7fHutlU.png)
#### 1.2 映射网络驱动器
映射服务器的共享目录到本地，使用内网地址 10.108.14.139，当前有四个目录可共享
分别是Databases Codes Resources Other，驱动器盘符随意指定
![映射网络驱动器](https://i.imgur.com/BNqjEXr.png)
#### 1.3 使用samba账号登陆
*密码是samba账号密码
![samba登陆](https://i.imgur.com/t53ROnW.png)
#### 1.4 文件操作
映射完成后可以在本地完成服务器文件的相关操作
![文件操作](https://i.imgur.com/gKJVvVd.png)

### 2. 复制本地文件到服务器（支持外网）
#### 2.1 软件需求
windows平台：[winscp](https://winscp.net/eng/download.php)

#### 2.2 登陆服务器
文件协议：SCP
内网地址：10.108.14.139 端口：22
外网地址：bit834.tk           端口：222
使用自己的用户名和密码
![登陆服务器](https://i.imgur.com/sYh5OVu.png)
#### 2.3 进入目录
默认进入用户文件夹下，通过打开目录进入共享目录下
分别对应

    /media/Databases
    /media/Codes
    /media/Resources
    /media/Other
   ![文件操作](https://i.imgur.com/eLUaDFB.png)
#### 2.4 文件操作
winscp支持文件拖放，也可在软件中直接修改文件

