---
title: PYTHON-NOTE
description: python使用过程中的问题整理
categories:
tags:

---

#### 

#### JUPYTER NOTEBOOK启动时报异常问题

- 

```
 File "/Library/Python/2.7/site-packages/traitlets/config/application.py", line 377, in print_subcommands
    print(os.linesep.join(lines))
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe5 in position 4: ordinal not in range(128)
```

方法，代码中加入

```
import sys
reload(sys)
sys.setdefaultencoding('utf-8')
```

- 

```
[C 04:39:00.449 NotebookApp] Bad config encountered during initialization:
[C 04:39:00.449 NotebookApp] Could not decode '\xe6\x9c\xaa\xe5\x91\xbd\xe5\x90\x8d' for unicode trait 'untitled_notebook' of a LargeFileManager instance.
```

方法，启动方法调整为

```
LANG=zn jupyter-notebook
```



#### 包安装报错

- 

```
Installing collected packages: numpy, python-dateutil, pandas
  Found existing installation: numpy 1.8.0rc1
Cannot uninstall 'numpy'. It is a distutils installed project and thus we cannot accurately determine which files belong to it which would lead to only a partial uninstall.
```

方法，忽略继续安装

```
sudo pip install pandas --ignore-installed numpy
```



#### 安装报找不到版本

```
pip3 install -r requirements.txt -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com

pip3 install pandas -i http://pypi.douban.com/simple --trusted-host pypi.douban.com

pip3 install pandas -i http://mirrors.aliyun.com/pypi/simple/   --trusted-host mirrors.aliyun.com
```

