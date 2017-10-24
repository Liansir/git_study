## 安装git
这一步自行解决.
生成密钥：
$ ssh-keygen -t rsa -C "your_email@youremail.com"

## 注册github帐号
注册完github帐号之后创建一个新的仓库。

## 在本地测试
安装上git之后，直接测试：
ssh -T git@github.com 会半天得不到响应
ssh -vT git@github.com时有如下错误
key_load_public: No such file or directory

于是，先不测试，将github上已经建立好的仓库克隆到本地看看：
git clone https://github.com/Liansir/git_study.git

本地成功出现了git_study目录。趁机在git_study目录下创建一个文件，如a.md
先查看一下git状态：
git status
然后提交一下：
git commit -m "add file a.md"
出现如下提示：
*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

于是按照提示设置用户名与用户邮箱
$ git config --global user.name "liansir"
$ git config --global user.email "liansir_99@163.com"

完成之后再次提交：git commit -m "add file a.md"
出现如下字样：
[master (root-commit) 2d61ec1] add a.md
 1 file changed, 1 insertion(+)
 create mode 100644 a.md

这样应该表示成功了.

## 在github上查看推送的文件
经查看，git_study仓库中确实有a.md这个文件

## 再次测试
继续推送一下：
$ git push origin master
发现需求输入你的github的用户名与密码：
Username for 'https://github.com': Liansir
Password for 'https://Liansir@github.com':
并有如下显示：
Counting objects: 3, done.
Writing objects: 100% (3/3), 209 bytes | 209.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/Liansir/git_study.git
 * [new branch]      master -> master

好，再 git push origin master 一下，则显示：
Everything up-to-date

之前ssh测试失败的我们再来试一下：
$ ssh -T git@github.com
The authenticity of host 'github.com (192.30.255.113)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,192.30.255.113' (RSA) to the list of known hosts.
Hi Liansir! You've successfully authenticated, but GitHub does not provide shell access.

认证显示也通过了。
