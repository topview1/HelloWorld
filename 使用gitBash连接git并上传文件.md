# 使用gitBash连接git并上传文件
## 1.准备

在连接之前我们需要的资源：
* 1.拥有一个github账户  https://github.com/join
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517120313890.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)

* 2.安装git   下载地址 https://github.com/waylau/git-for-win/

## 2.设置git

* 打开gitbash
* 设置姓名

```cmd
$ git config --global user.name "github账号名" 
$ git config --global user.email "github邮箱”

```

## 3.设置SSH Key
GitHub上连接已有仓库时的认证，是通过使用了SSH的公开密钥认证方式进行的。现在让我们来创建公开密钥认证所需的 SSH Key，并 将其添加至 GitHub。
```cmd
$ ssh-keygen -t rsa -C "github邮箱" 
Generating public/private rsa key pair. 
Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):  按回车键 
Enter passphrase (empty for no passphrase):  输入密码 
Enter same passphrase again:  再次输入密码 
“
```

**如果出现一下结果就是成功了**
```cmd
Your identification has been saved in /Users/your_user_directory/.ssh/id_rsa. Your public key has been saved in /Users/your_user_directory/.ssh/id_rsa.pub. The key fingerprint is:
fingerprint值  your_email@example.com 
The key's randomart image is:

```

## 4.添加公开密钥
* 在git bash继续输入
```cmd
cat ~/.ssh/id_rsa.pub
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517120531128.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)

* 点击右上角的账户设定按钮（Account Settings）

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517120630178.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)

* 打开SSH菜单

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517120713311.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)

* 点击新建SSH Key

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517120742528.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)


* Title 随便命名 Key 里粘贴刚刚你你复制的那串东西


![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-FtiQSzmj-1589688168442)(en-resource://database/5434:1)\]](https://img-blog.csdnimg.cn/20200517120800203.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)

* 点击Add SSH Key，返回到gitbash


## 5.与github建立通信
* 在gitbash里输入ssh -T git@github.com
```cmd
$ ssh -T git@github.com 
The authenticity of host 'github.com (207.97.227.239)' can't be established. RSA key fingerprint is  你的密码 . 
Are you sure you want to continue connecting (yes/no)?  输入yes 
```
* 密码是第三步设置的密码

* 结果如下表示成功连接
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517120835395.png#pic_center)


## 6.在github里创建仓库
* 点击New repository
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121013522.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)



* 命名仓库名字（此处我命名为HelloWorld）description可以不写

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121035530.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)

* 点击 create repository

* 创建完成
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121053466.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)


## 7.clone仓库 
**从git服务器克隆一个一模一样的版本库到本地,复制的是整个版本库，叫做clone**
* 点击Clone or download-> Use SSH

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121117456.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)

*  复制选中的路径
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121136288.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)


* 返回git bash，输入git clone + 粘贴复制选中的路径
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121158253.png#pic_center)

* clone完成

 那么我们clone的仓库在本地那个地方？
* clone到本地的路径一般是cmd的开始路径
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051712121522.png#pic_center)

* 我们打开c盘这个路径，我们发现这个仓库就在这
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121230106.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)

* 因为没有传文件，所以本地仓库是空的
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121245944.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)

## 8.在本地仓库上传文件并发布到github
* 返回gitbash，进入仓库目录，在输入vi 文件名
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121301508.png#pic_center)
* 进入vim编辑器进行编写，输入i进入编写状态

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121324349.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)
* 输入以下代码（可以随便输入），输入完毕后按esc进入命令行状态

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121346247.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)


* 在按ZZ 保存退出
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121359920.png#pic_center)

* 在打开c盘git仓库路径可以发现，php已经创建完毕

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121415225.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)


* 返回gitbash，输入git status 添加php文件到git仓库

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121430525.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)

**我们发现有报错，原因是因为在windows和linux环境不同，换行符不同，git默认是linux环境**

* 修改git设置

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121457573.png#pic_center)

* 再一次进行添加php文件,没有报错
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121511889.png#pic_center)


* 将 hello_word.php提交至git仓库
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121531179.png#pic_center)

* 查看日志，可以查看提交账户和时间

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020051712154666.png#pic_center)
* 此时的github仓库是没有这个文件的，因为没有更新仓库，输入git push进行更新

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121600882.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)

* 查看github仓库，更新成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200517121613532.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzMzMTIwMA==,size_16,color_FFFFFF,t_70#pic_center)
