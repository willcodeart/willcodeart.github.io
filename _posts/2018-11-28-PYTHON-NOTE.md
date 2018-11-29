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

