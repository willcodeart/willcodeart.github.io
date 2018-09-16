---
title: EC2创建ipython Notebook环境
description:  EC2创建ipython Notebook环境，安装Anaconda之后，安装ipython环境
categories:
tags:

---

###安装Anaconda之后，安装ipython环境
```
conda install ipython
conda install ipython-notebook
```

接下来，我们需要创建一个名为nbserver的配置。

```
ipython profile create nbserver
```


这将创建一个文件夹，其中包含一些原始的配置文件。我们跳转到这个文件夹进行一些配置

```
cd ~/.ipython/profile_nbserver/
```


由于ipython Notebook要求https连接，因此我们需要创建一个ssl证书。

```
openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout mycert.pem -out mycert.pem
```

命令执行后根据提示输入信息就好，当然，这个证书并未获得认证，因此用chrome之类的浏览器访问的时候会得到一些错误信息，这个问题我们一会儿说。接下来我们创建一个密文的密码。

```
python -c "import IPython;print IPython.lib.passwd()"
```

运行之后进入一个创建密码hash值的小程序，根据提示输入你想用的安全口令：

```
Enter password:
Verify password:
sha1:b86e933199ad:a02e9592e59723da722.

```



###设置ipython_notebook_config.py的内容
```
ubuntu@ip-172-31-0-249:~/.ipython/profile_nbserver$ sudo vi ipython_notebook_config.py
```



###设置文件内容
```
c = get_config()
c.IPKernelApp.pylab = 'inline'
c.NotebookApp.certfile = u'~/.ipython/profile_nbserver/mycert.pem'
c.NotebookApp.password = u'0392662ddae2:04ad9505939da5ee3dac4fff4101696c0c53b681'
c.NotebookApp.ip = '*'
c.NotebookApp.port = 8888
c.NotebookApp.open_browser = False
```



###启动服务
```
ipython notebook --config=~/.ipython/profile_nbserver/ipython_notebook_config.py
```



###创建端口映射
```
sudo iptables -t nat -A PREROUTING -p tcp --dport 443 -j REDIRECT --to-port 8889
```



###查看端口映射是否成功
```
sudo  iptables -t nat -L
```

之后访问https://ec2-13-58-86-145.us-east-2.compute.amazonaws.com 即可