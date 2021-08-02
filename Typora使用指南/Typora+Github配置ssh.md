# 安装Git并配置Github仓库
 1. **下载安装[Git](https://git-scm.com/downloads)**
	
	>安装版的安装教程参考[这篇文章](https://www.cnblogs.com/xueweisuoyong/archive/2019/11/22/11914045.html)
	>
	>> 如果下载的是便携版本(便携版本需要自己配置环境变量)，需要添加鼠标右键的"Git bash here"可以参考[这篇文章](https://www.cnblogs.com/Summerio/p/11853137.html)
	
	<details> <summary>环境变量配置方法</summary> <pre>1. WIN+S输入"编辑系统环境变量",点击[环境变量]<br/>2. 找到"系统变量(s)"下的Path,点击[编辑]<br/>3. 新键X:\PortableGit\cmd</pre> </details>
	
 2. **找个舒服的文件夹右键Git bash here**

 3. **设置Git的user name和email**

```
//配置name
git config --global user.name "xx" 
//配置email
git config --global user.email "xx@gmail.com" 
//查看配置信息
git config --list
```

4. **查看电脑中是否已经有过ssh密钥**

```
cd ~/.ssh
```
> 如果有,则显示如下。如果没有则不会显示这个文件夹
![image-20210731165013560](https://cdn.jsdelivr.net/gh/Wutpeach/Notes_pic/pic/202108022031764.png)

5. **生成密钥，输入如下命令行，再按3下回车**
```
    ssh-keygen -t rsa
```
6. **打开id_rsa.pub公钥，并且复制全部内容**
```
   cat ~/.ssh/id_rsa.pub
```

7. **打开Github --> Settings --> SSH and GPC keys --> New SSH key --> 粘贴**

	> 到这一步为止，密钥的创建已经完成，下一步开始搭建仓库

8. **打开Github --> Your repositories --> New**

<img src="https://cdn.jsdelivr.net/gh/Wutpeach/Notes_pic/pic/202108022027456.png" alt="image-20210731173318826" style="width:70%;" />

9. **克隆仓库到本地**

```
   git clone XXX
```
> 克隆之前可以使用 ssh -t git@github.com 测试一下配置成功没
# 常见问题
1. **如果ssh -t git@github.com 没有显示'You 've successfully autenticated, but Github does not provide shell access'**
[原文指引](https://www.freesion.com/article/48371308565/)
```
	//那么执行如下命令行
	ssh-agent -s
	ssh-add ~/.ssh/id_rsa
	//如果执行ssh-add的时候出现‘Could not open a connection to your authentication agent’那么执行如下命令行
	ssh-agent bash
	ssh-add ~/.ssh/id_ras
```

2. **如果提交的目录是空目录，那么git push时就会报错，解决办法如下**
   
```
	//在目录下创建一个空文件,再进行git push
	touch .gitkeep
```
3. **上传md文件时，提示'warning: LF will be replaced by CRLF in ...'**
    [原文指引](https://blog.csdn.net/man_zuo/article/details/88651416)
    
    > ==LF==和==CRLF==其实都是换行符，但是不同的是，==LF==是linux和Unix系统的换行符，==CRLF==是window 系统的换行符。这就给跨平台的协作的项目带来了问题，保存文件到底是使用哪个标准呢？ git为了解决这个问题，提供了一个==”换行符自动转换“==的功能，并且这个功能是默认处于”自动模式“即开启状态的。 这个换行符自动转换会把自动把你代码里 与你当前操作系统不相同的换行的方式 转换成当前系统的换行方式（即LF和CRLF 之间的转换），这样一来，当你提交代码的时候，即使你没有修改过某个文件，也被git认为你修改过了，从而提示=="LF will be replaced by CRLF in ..."==
    > 所以这个warning可以不用理会，放着就行，她不会去修改你本地的换行符，只会修改仓库的换行符表达方式，使其显示正确
    
4. **如果你在ssh-keygen -t rsa的时候使用了自定义的名字那么可能会在接下来的使用中出现'Permission denied (publickey)'错误**

   [更好的解决办法](https://www.cnblogs.com/lxwphp/p/7884700.html)

```
//不要自定义rsa文件的名字，don't do it！
//先跳转到c盘下的.ssh目录
cd ~/.ssh/
//启用编辑模式
vi config
//复制以下内容
Host github.com
 HostName github.com
 User git
 IdentityFile ~/.ssh/github_rsa
 //ESC+:wq 保存退出
 //重新链接github进行验证
 ssh -t git@github.com
```

# 配置Picgo+Github图床

Picgo下载链接：[官网](https://molunerfinn.com/PicGo/)

1. 安装 --> 插件设置 --> 搜索github-plus

2. 打开github --> Settings --> Developer settings --> Personal access tokens --> Generate new token



3. 创建完毕后复制token，粘贴进PicGO --> 图床设置 --> githubPlus --> token

**Picgo参数说明**

- repo：表示远程仓库地址，固定格式 `Github用户名/仓库名`
- branch：表示分支，默认填入master，需要根据自己Github上的分支进行填写
- Token：填入Github中生成的Token，下方将详细讲解Token获取
- path:导入路径，如果想上传到目标文件夹，可以直接填写 pic/
- customUrl：自定义域名，建议使用`https:cdn.jsdelivr.net/gh/Github用户名/仓库名`
- origin：默认为github就可以了

<img src="https://cdn.jsdelivr.net/gh/Wutpeach/Notes_pic/pic/202108022028079.png" alt="image-20210731181642920" style="width:80%;" />

4. 一切填写完毕后可以打开Typora --> 文件 --> 偏好设置 --> 图片 --> 验证图片上传

==注意事项：不要上传文件名重复的文件==

[原文指引](https://www.cnblogs.com/zhouxiongjie/p/13184797.html)

# 指定文件夹备份图片

1. 文件 --> 偏好设置 --> 图像

2. 勾选“对本地位置的图片应用上述规则”+“优先使用相对路径”

3. 设置"复制到指定路径" --> 路径设置为X:\AAA\BBB\CCC\\${filename}

   ![image-20210731182249502](https://cdn.jsdelivr.net/gh/Wutpeach/Notes_pic/pic/202108022028984.png)
