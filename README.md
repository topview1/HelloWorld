# 使用gitBash连接git并上传文件
## 1.准备

在连接之前我们需要的资源：
* 1.拥有一个github账户  https://github.com/join
![eacb3092199f351c510e9651564e89cf.png](en-resource://database/5424:1)

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

* 我们会得到如下结果，选中的部分复制
![15bd58dd4165dce2ac30272ed7a7beea.png](en-resource://database/5432:1)

* 点击右上角的账户设定按钮（Account Settings）

![499025e99197a1ca17cf966deba5ec88.png](en-resource://database/5426:1)

* 打开SSH菜单

![2eb5ad79f9670a3a0e459dc6c5582336.png](en-resource://database/5428:1)

* 点击新建SSH Key

![131d2db5a68215d4959eb968d9ecab4b.png](en-resource://database/5430:1)


* Title 随便命名 Key 里粘贴刚刚你你复制的那串东西


![c60435bf623b001c153764c4870a5c33.png](en-resource://database/5434:1)


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
![38b770cabd92ab2ab1d631902f278fef.png](en-resource://database/5436:1)


## 6.在github里创建仓库
* 点击New repository
![13dd7fcd2a020c6cca4ca490ff809077.png](en-resource://database/5438:1)

* 命名仓库名字（此处我命名为HelloWorld）description可以不写

![adde384232fda7a44691ac22d815b9ab.png](en-resource://database/5440:1)

* 点击 create repository

* 创建完成
![262767855cafbe53f27001ab691bbddc.png](en-resource://database/5442:1)


## 7.clone仓库 
**从git服务器克隆一个一模一样的版本库到本地,复制的是整个版本库，叫做clone**
* 点击Clone or download-> Use SSH

![5596a85d74dbf6f66ca8792c9dc05a8b.png](en-resource://database/5444:1)


*  复制选中的路径
![71cc14a300499b72d46218211d4208b3.png](en-resource://database/5446:1)


* 返回git bash，输入git clone + 粘贴复制选中的路径

![7aab4b815f796fefc180cd11317e53ba.png](en-resource://database/5448:1)

* clone完成

 那么我们clone的仓库在本地那个地方？
* clone到本地的路径一般是cmd的开始路径

![ea9a457e6bef96aeadd127c55640bc08.png](en-resource://database/5450:1)

* 我们打开c盘这个路径，我们发现这个仓库就在这
![6114ffef3c1219d3e2ac7bb097203f79.png](en-resource://database/5452:1)


* 因为没有传文件，所以本地仓库是空的
![70edfd2b63b76a259e4dad29fa312fd6.png](en-resource://database/5454:0)


## 8.在本地仓库上传文件并发布到github
* 返回gitbash，进入仓库目录，在输入vi 文件名
![51125b1c8af9f122ae80503924a724ac.png](en-resource://database/5456:0)

* 进入vim编辑器进行编写，输入i进入编写状态
![88629f67a4c007b535555d30930f6267.png](en-resource://database/5458:0)

* 输入以下代码（可以随便输入），输入完毕后按esc进入命令行状态

![33db43ab933e320c9b3177424647fb5f.png](en-resource://database/5460:0)

* 在按ZZ 保存退出

![237c53c6329afe97acc1014264efde90.png](en-resource://database/5462:0)

* 在打开c盘git仓库路径可以发现，php已经创建完毕

![6b1e255e84a6c4a382b7a0b7890a1486.png](en-resource://database/5464:0)


* 返回gitbash，输入git status 添加php文件到git仓库

![36256b8e0d435acb1b3d08b8c412d8eb.png](en-resource://database/5466:0)

**我们发现有报错，原因是因为在windows和linux环境不同，换行符不同，git默认是linux环境**

* 修改git设置

![a26e813fbff3844d2348f12770e4d23d.png](en-resource://database/5468:0)

* 再一次进行添加php文件,没有报错
![12f7d47c674414987e2f9a2d5fc30990.png](en-resource://database/5470:0)


* 将 hello_word.php提交至git仓库
![df0dbf38295bb045b765bf4777cd83ea.png](en-resource://database/5472:0)

* 查看日志，可以查看提交账户和时间

![3a7ea3a2c6c5cb9255874222b2b733b5.png](en-resource://database/5474:0)

* 此时的github仓库是没有这个文件的，因为没有更新仓库，输入git push进行更新

![8bb5a04e90d8fef65b22615bcf3a9f0d.png](en-resource://database/5476:0)

* 查看github仓库，更新成功
* 
![cfd53b9decfce1ddd34a5ab9ac3dd6ec.png](en-resource://database/5478:0)
