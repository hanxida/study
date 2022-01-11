

[toc]

# Linux命令行与Git操作

## 1. Linux命令行

> - ```cd:#改变目录```
> - ```cd..#回到上一个目录,直接cd进入默认目录```
> - ```pwd:#显示当前所在目录路径```
> - ```ls(ll):#都是列出当前目录中的所有文件,只不过**ll**列出的内容更为详细```
> - ```mkdir:新建一个目录,就是新建一个文件夹```
>
> - ```rm -r:删除一个文件夹,rm -r src 删除src目录```
>
>   ```python
>   rm -rf / #删除所有文件
>   ```
>
> -  ```mv:移动文件,mv test.c src test.c 必须保证目标目录与目标文件在同一目录下```
> -  ```reset/(clear):重新初始化终端/清屏(clear也是清屏)```
> -  ```history:查看历史命令```
> -  ```help:帮助```
> -  ```exit:退出```

---

---

## 2. Git操作

### 2.1 Git配置

> 所有的配置文件,其实都保存在本地

> - ==`git config -l`:查看配置==

```python
#查看系统config
git config --system --list

#查看当前用户(global)配置
git config --global --list
```

> ==设置用户名与邮箱(用户表示,必要)==

---

### 2.2 Git项目搭建

> 新建Git项目

```python
$ git init
#执行之后可以看到仅仅在项目目录多出了个.git目录,关于版本等所有信息都在这个目录中
```

> 克隆远程仓库

```python
$ git clone https://...
#克隆一个项目和他的整段代码历史（版本信息）
```

---

### 2.3 git操作流程

```python
$ touch file.txt #创建名为file.txt的文件
$ vi file.txt    #在git bash 下对文件 file.txt进行修改
$ git add .      #将所有修改推到缓存区，指定文件推送为git add file.txt
$ git coimmit -m "注释" #将缓存区文件推到仓库中
$ git log		#查看仓库修改历史
```

> - **==`git log:`==**

```python
$ git log --all					#显示所有分支
$ git log --pretty=oneline		 #将提交信息显示为一行
$ git log --abbrev-commit		 #使得输出的commitld更简短
$ git log --graph				#以图的形式显示
```

> - **==`git reset`==**

```python
$ git reset --hard commitID
```

> - ==**`git reflog`**：回退找寻已reset版本==



<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/image-20220109163306705.png" width = "70%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #666;
    padding: 2px;">
      git reflog示例
  	</div>
</center>

---



> - ==**`touch .gitignore`**:在该文件中添加文件名，表示不需要git进行管理的文件，即添加文件到忽略列表==

```python
#such as
*.a		#在.gitignore中添加表示'.a'类型的文件不加入到缓存区
```

---

### 2.4 git分支创建、查找、删除、合并[^ 注.1]

> - ==**`git branch`**:查找分支以及创建分支==

```python
$ git branch
* master
$ git branch dev01
$ git branch
 dev01
* master	
```

---

> - ==**`*git checkout`**:切换分支==
>
> - ==（`git checkout -b`:创建新分支并立即切换到该分支下，从而在该分支中操作。）==

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/image-20220109171918150.png" width = "70%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      切换到dev01分支
  	</div>
</center>

---



<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/image-20220109172037297.png"width = "70%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
     切换回master分支
  	</div>
</center>

---



<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/image-20220110021100965.png" width = "70%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      git checkout -b创建dev02并转到该分支(强制删除)
  	</div>
</center>

---

> - ==`git branch -D/d`:从other/master分支上删除分支==[^ 注.1]



<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/image-20220110022548382.png" width = "70%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      git branch -D从dev01分支上删除dev02分支
  	</div>
</center>

---



<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/image-20220110022850083.png" width = "70%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      git branch -d在master分支上删除dev02
  	</div>
</center>

> - ==`*git merge`:分支的合并==

>> **查看当前分支**



<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/image-20220110030839244.png" width = "70%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      查看目前分支所在位置
  	</div>
</center>

> > **切换到master分支**

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/image-20220110030950987.png" width = "70%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      切换到master分支
  	</div>
</center>

>> **合并分支**

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/image-20220110031236714.png" width = "70%" alt=""/>
    <br>
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      将dev01合并到master分支
  	</div>
</center>

---

### 2.5 *分支合并冲突解决

==分支与主干合并时，当同一行出现冲突时，需要手动修改决定需要保存的版本，之后再进行提交==

---

---

## 3. 开发中分支使用原则与流程

> - master(生产分支)
>
>   线上分支，主分支，中小规模项目作为线上运行的应用对应的分支：
>
> - develop(开发分支)
>
>   是从master常见的分支，一般作为开发部门的主要开发分支，如果没有其他并行开发不同期上线要求，都可以在此版本进行开发，阶段开发完成后，需要是合并到master分支准备上线
>
> - feature/xxxx分支
>
>   从develop创建的分支，一般时同期并行开发，但不同期上线是创建的分支，分支上的研发任务完成后合并后到develop分支
>
> - hotfix/xxxx分支
>
>   从master派生的分支，一般作为线上bug修复使用，修复完成后需要合并到master、test、develop分支
>
> - 还有一些其他分支如test(测试分支)、pre（预上线分支）等等
>
>   ---
>
>   ---

## 4.Git远程仓库

### 4.1配置SSH公钥

> - 生成SSH公钥
>
>   - ```shell
>     $ ssh-keygen -t rsa -C "your_email@your_email.com"
>     ```
>
>   - 不断回车
>
> - 如果公钥已存在则会自动覆盖
>
> - 设置账户共公钥
>
>   - 获取公钥
>
>     - ```shell
>       $ cat ~/.ssh/id_rsa.pub
>       ```
>
>   - 复制公钥
>
>   - 将复制的公钥配置到github上
>
>     <center>
>         <img style="border-radius: 0.3125em;
>         box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
>         src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/48840BF0-992F-4CCC-A388-15CB74819D88.jpg" width = "70%" alt=""/>
>         <br>
>         <div style="color:orange; border-bottom: 1px solid #d9d9d9;
>         display: inline-block;
>         color: #999;
>         padding: 2px;">
>         	进入 Account => Settings（账户配置）   
>          </div>
>     </center>
>
>     <center>
>         <img style="border-radius: 0.3125em;
>         box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
>         src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/B0589847-A498-4415-8700-252BDE1B20C0.jpg" width = "70%" alt=""/>
>         <br>
>         <div style="color:orange; border-bottom: 1px solid #d9d9d9;
>         display: inline-block;
>         color: #999;
>         padding: 2px;">
>           选择SSH and GPG keys
>       	</div>
>     </center>
>
>     <center>
>         <img style="border-radius: 0.3125em;
>         box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
>         src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/106AD534-A38A-47F3-88A3-B7BE3F2FEEF1.jpg" width = "70%" alt=""/>
>         <br>
>         <div style="color:orange; border-bottom: 1px solid #d9d9d9;
>         display: inline-block;
>         color: #999;
>         padding: 2px;">
>           粘贴生成的 key
>       	</div>
>     </center>
>
>     <center>
>         <img style="border-radius: 0.3125em;
>         box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
>         src="Linux%E5%91%BD%E4%BB%A4%E8%A1%8C.assets/EC8F8872-091A-4CAB-90F2-616F34F350A9.jpg" width = "70%" alt=""/>
>         <br>
>         <div style="color:orange; border-bottom: 1px solid #d9d9d9;
>         display: inline-block;
>         color: #999;
>         padding: 2px;">
>           添加完之后的界面
>       	</div>
>     </center>
>
>   - 验证是否成功
>
>     ```shell
>     $ ssh -T git@github.com
>     The authenticity of host 'github.com (52.74.223.119)' can't be established.
>     RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
>     Are you sure you want to continue connecting (yes/no/[fingerprint])? yes                   # 输入 yes
>     Warning: Permanently added 'github.com,52.74.223.119' (RSA) to the list of known hosts.
>     Hi tianqixin! You've successfully authenticated, but GitHub does not provide shell access. # 成功信息
>     ```
>
>     ___

### 4.2 连接仓库

> - 创建GitHub仓库
> - push本地仓库
>
> ```shell
> $ mkdir runoob-git-test                     # 创建测试目录
> $ cd runoob-git-test/                       # 进入测试目录
> $ echo "# 菜鸟教程 Git 测试" >> README.md     # 创建 README.md 文件并写入内容
> $ ls                                        # 查看目录下的文件
> README
> $ git init                                  # 初始化
> $ git add README.md                         # 添加文件
> $ git commit -m "添加 README.md 文件"        # 提交并备注信息
> [master (root-commit) 0205aab] 添加 README.md 文件
>  1 file changed, 1 insertion(+)
>  create mode 100644 README.md
> 
> # 提交到 Github
> $ git remote add origin "github仓库地址"
> $ git push -u origin master
> ```
>
> - 查看当前配置仓库
>
>   ```shell
>   $ git remote
>   origin
>   $ git remote -v				#执行时加上 -v 参数，你还可以看到每个别名的实际链接地址。
>   origin    git@github.com:tianqixin/runoob-git-test.git (fetch)
>   origin    git@github.com:tianqixin/runoob-git-test.git (push)
>   $ git remote rm [别名]	   #删除远程仓库
>   ```
>
> - 提取远程仓库的更新
>
>   ```shell
>   $ git fetch origin
>   remote: Counting objects: 3, done.
>   remote: Compressing objects: 100% (2/2), done.
>   remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
>   Unpacking objects: 100% (3/3), done.
>   From github.com:tianqixin/runoob-git-test
>      0205aab..febd8ed  master     -> origin/master
>   ```
>
> - 同步到本地
>
> - ```shell
>   $ git merge origin/master
>   Updating 0205aab..febd8ed
>   Fast-forward
>    README.md | 1 +
>    1 file changed, 1 insertion(+)
>   ```
>
>   ```shell
>   $ git push [alias] [branch]
>   #将你的 [branch] 分支推送成为 [alias] 远程仓库上的 [branch] 分支
>   ```
>
>   

[^ 注.1]:懒得敲了直接截的图，效果一样
[^ 注.2]:不可以在当前所在分支上删除该分支

