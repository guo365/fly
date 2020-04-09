# fly

## git 搭建测试页面
## 步骤一：

- 登陆GitHub主页
- 点击右上角`+`号，选择New Repository
- 再打开的Create a new repository页面，按照如下设置：
    - Owner：这个是账户，如果你想给其他账户创建Repository就选择其他的
    - Repository name|：这里是填写创建资源库名称
    - Repository权限设置：
       - [x] Plublic
       - [ ] Private
      >Public免费的,不过任何人都能访问
      >Private收费的，限制其他人访问
      >这个根据需求选择吧，一般相信Public够用了，反正是玩而已
    - Initialize this repository with a README
      >使用README初始化这个仓库
      >这将让您立即将存储库克隆到计算机。如果要导入现有存储库，请跳过此步骤
      >这里勾选，因为我是创建新的
- 然后点击创建Create repository,即可创建一个仓库

## 步骤二：

- 添加ssh免密钥登陆（本地操作）

        # ssh-keygen -t rsa -C "你的邮箱账户（好像也可以不写）"

- 拷贝生成的id_rsa.pub内容

        # cat id_rsa.pub

- 点击右上角头像，选择Setting，打开页面选择SSH and GPG keys
- 在SSH and GPG keys右侧点击SSH keys右边的New SSH key，在弹出的框中粘贴刚才复制的密钥，然后单击添加即可
- 本地验证是否成功

       # ssh -T git@github.com
        Hi admin! You've successfully authenticated, but GitHub does not provide shell access.
    >如有以上提示就说明成功了，这个是测试，后面拉去、上传代码文件不需要这样操作

## 步骤三：

- 本地创建与github同名的文件夹

        # mkdir project
    > project为你github上的仓库名
- 首次初始化本地仓库

        # git init

- 设置github登录名和邮箱

       # git config --global user.name "your name"
       # git config --global user.email "your email"

- 将该Github版本仓库添加到本机的远程列表中

       #  git remote add origin  git@github.com:yuoraccount/your Repostiry.git

- 添加内容至test.md

       # echo "test is ok" >test.md

- 提交文件到本地缓存库

       # git add test.md

- 提交到本地git版本库

       # git commit -m "add words"

- 同步本地版本库至github

      # git push origin master

备注：首次同步到github需要添加`-u`参数,或者先pull下

## 容易遇到的问题

```

   error:failed to push some refs to ...

   Dealing with “non-fast-forward” errors
   From time to time you may encounter this error while pushing:

   $ git push origin master  
   To ../remote/  
   ! [rejected]        master -> master (non-fast forward)  
   error: failed to push some refs to '../remote/'  
   To prevent you from losing history, non-fast-forward updates were rejected
   Merge the remote changes before pushing again.  See the 'non-fast forward'
   section of 'git push --help' for details.

```

>这个问题github上面的代码里面已经有你本地新添加的代码文件内容，他不允许直接覆盖

>解决方法：
   ` # git pull origin master`
>重新拉去一次，然后重新提交
