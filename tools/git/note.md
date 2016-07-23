Git (from :http://www.liaoxuefeng.com)
## key
第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：
'''
git@github.com:jianchengss/lanbitou.git
'''
## add key to github
第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面：

然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容
## 添加远程库
登陆GitHub，然后，在右上角找到“Create a new repo”按钮，创建一个新的仓库：
在GitHub上的这个learngit仓库还是空的，GitHub告诉我们，可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库。
'''
git remote add origin git@github.com:***/***.git
'''
下一步，就可以把本地库的所有内容推送到远程库上：
'''
$ git push -u origin master
Counting objects: 19, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (19/19), done.
Writing objects: 100% (19/19), 13.73 KiB, done.
Total 23 (delta 6), reused 0 (delta 0)
To git@github.com:michaelliao/learngit.git
 * [new branch]      master -> master
 Branch master set up to track remote branch master from origin.

 '''

 把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。

 由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

 推送成功后，可以立刻在GitHub页面中看到远程库的内容已经和本地一模一样
## push
从现在起，只要本地作了提交，就可以通过命令：
'''
git push origin master
'''
把本地master分支的最新修改推送至GitHub，现在，你就拥有了真正的分布式版本库！

## SSH警告
当你第一次使用Git的clone或者push命令连接GitHub时，会得到一个警告：
'''
The authenticity of host 'github.com (xx.xx.xx.xx)' can't be established.
RSA key fingerprint is xx.xx.xx.xx.xx.
Are you sure you want to continue connecting (yes/no)?
'''

这是因为Git使用SSH连接，而SSH连接在第一次验证GitHub服务器的Key时，需要你确认GitHub的Key的指纹信息是否真的来自GitHub的服务器，输入yes回车即可。

Git会输出一个警告，告诉你已经把GitHub的Key添加到本机的一个信任列表里了：
'''
Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
'''
