



virtualenv 是 Python 的沙箱工具，用于创建独立的 Python 环境。我们毕竟是在自己机器上 做实验，为了不来回修改各种环境变量，这里用 virtualenv 为 TensorFlow 创建一套“隔离”的 Python 运行环境。
首先，用 pip 安装 virtualenv:

```
$ pip install virtualenv --upgrade
```

安装好后创建一个工作目录，这里直接在 home 下创建了一个 tensorflow 文件夹: 

```
$ virtualenv --system-site-packages ~/tensorflow
```

 然后进入该目录，激活沙箱:

```
$ cd ~/tensorflow
$ source bin/activate
(tensorflow) $
```

在 virtualenv 里安装 TensorFlow
进入沙箱后，执行下面的命令来安装 TensorFlow:

```
(tensorflow) $ pip install tensorflow==1.1.0
```

 默认安装所需的依赖，直至安装成功。