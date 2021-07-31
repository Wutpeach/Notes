# 配置Git

1. 下载安装[Git](https://git-scm.com/downloads)
	>安装版的安装教程参考[这篇文章](https://www.cnblogs.com/xueweisuoyong/archive/2019/11/22/11914045.html)
	>
	>> 如果下载的是便携版本(便携版本需要自己配置环境变量)，需要添加鼠标右键的"Git bash here"可以参考[这篇文章](https://www.cnblogs.com/Summerio/p/11853137.html)
	
	<details> <summary>环境变量配置方法</summary> <pre>1. WIN+S输入"编辑系统环境变量",点击[环境变量]<br/>2. 找到"系统变量(s)"下的Path,点击[编辑]<br/>3. 新键X:\PortableGit\cmd</pre> </details>

 2. 找个舒服的文件夹右键Git bash here

 3. 设置Git的user name和email

```
//配置name
git config --global user.name "xx" 
//配置email
git config --global user.email "xx@gmail.com" 
//查看配置信息
git config --list
```

4. 查看电脑中是否已经有过ssh密钥

```
cd ~/.ssh
```
>如果有,则显示如下
![image-20210731165013560](../../assets/Untitled/image-20210731165013560.png)



