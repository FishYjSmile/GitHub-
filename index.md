## 上传项目到GitHub上发现出了错误，弄了挺久都没成功 发现一篇文章 亲测有效 作为记录方便以后查看

### 打开git-bash.exe，在桌面快捷方式/开始菜单/安装目录中

### 因为Git是分布式版本控制系统，所以需要填写用户名和邮箱作为一个标识，用户和邮箱为你github注册的账号和邮箱



 

ps：git config –global 参数，有了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然你也可以对某个仓库指定的不同的用户名和邮箱。
为Github账户设置SSH key
众所周知ssh key是加密传输。

加密传输的算法有好多，git使用rsa，rsa要解决的一个核心问题是，如何使用一对特定的数字，使其中一个数字可以用来加密，而另外一个数字可以用来解密。这两个数字就是你在使用git和github的时候所遇到的public key也就是公钥以及private key私钥。

其中，公钥就是那个用来加密的数字，这也就是为什么你在本机生成了公钥之后，要上传到github的原因。从github发回来的，用那公钥加密过的数据，可以用你本地的私钥来还原。

如果你的key丢失了，不管是公钥还是私钥，丢失一个都不能用了，解决方法也很简单，重新再生成一次，然后在http://github.com里再设置一次就行。

生成ssh key
首先检查是否已生成密钥 cd ~/.ssh，ls如果有2个文件，则密钥已经生成，id_rsa.pub就是公钥




也可以打开我的电脑C:\Users\Y\ .ssh 里面找到




如果没有生成，那么通过$ ssh-keygen -t rsa -C “xxxxxx@163.com”来生成。

1）是路径确认，直接按回车存默认路径即可

2）直接回车键，这里我们不使用密码进行登录, 用密码太麻烦;

3）直接回车键




生成成功后，去对应目录C:\Users\Y\ .ssh里（Y为电脑用户名，每个人不同）用记事本打开id_rsa.pub，得到ssh key公钥



 

 为github账号配置ssh key
切换到github，展开个人头像的小三角，点击settings




然后打开SSH keys菜单， 点击Add SSH key新增密钥，填上标题，跟仓库保持一致吧，好区分。

接着将id_rsa.pub文件中key粘贴到此，最后Add key生成密钥吧。



 

如此，github账号的SSH keys配置完成。



 

上传本地项目到github
 创建一个本地项目
文件夹目录下：



 

 建立本地仓库
再来复习一下创建新仓库的指令：

git init //把这个目录变成Git可以管理的仓库
　　git add README.md //文件添加到仓库
　　git add . //不但可以跟单一文件，还可以跟通配符，更可以跟目录。一个点就把当前目录下所有未追踪的文件全部add了 
　　git commit -m "first commit" //把文件提交到仓库
　　git remote add origin git@github.com:wangjiax9/practice.git //关联远程仓库
　　git push -u origin master //把本地库的所有内容推送到远程库上
首先，进入到wyj_first项目目录，还记得创建仓库成功后的那个页面吧，指令都在呢。

然后执行指令：git init




初始化成功后你会发现项目里多了一个隐藏文件夹.git

这个目录是Git用来跟踪管理版本库的，没事千万不要手动修改这个目录里面的文件，不然改乱了，就把Git仓库给破坏了。




接着，将所有文件添加到仓库

执行指令：git add .




然后，把文件提交到仓库，双引号内是提交注释。

执行指令：git commit -m "提交文件"




如此本地仓库建立好了。

 关联github仓库
到github wyj_first仓库复制仓库地址




然后执行指令：git remote add origin git@github.com:gain-wyj/wyj_first.git



 

 上传本地代码
执行指令：git push -u origin master

1）敲一个：yes， 然后回车




到此，本地代码已经推送到github仓库了，我们现在去githubt仓库看看。



转至：手把手教你用git上传项目到GitHub（图文并茂，这一篇就够了），相信你一定能成功！！ - 梦魇的文章 - 知乎 https://zhuanlan.zhihu.com/p/193140870
