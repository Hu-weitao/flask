## 为什么需要虚拟环境

我们在用python开发项目的时候肯定用的只是某一版本的python以及相应的库，而每个版本的python以及库的用法甚至语法上会存在一些差异。

为了避免因版本更新而导致项目崩溃，我们就需要为这个项目单独创建一个能够让它运行的环境，也就是让它运行在开发它时所用的python版本和库版本的环境当中，不受其它外部环境的干扰。

## 使用 venv 创建虚拟环境

在python3及以上版本中内置了`venv`模块，所以不需要再单独进行安装了。

#### 创建虚拟环境

首先打开`cmd`，使用命令为我们的项目创建文件夹（例如叫做`pikaqiu`）：
```
mkdir pikaqiu

cd pikaqiu
```

进入项目文件夹之后，使用命令`python -m venv 虚拟环境名称`为`pikaqiu`创建一个虚拟环境：
```
python -m venv pikaqiu-venv
```
这样我们就为`pikaqiu`创建好了一个叫做`pikaqiu-venv`的虚拟环境。实际上就是在当前项目目录里，创建了一个名为 `pikaqiu-venv` 的虚拟环境文件夹。如果要上传到github，需要把这个文件夹名称加入.gitignore 文件以便让 Git 忽略。

#### 激活虚拟环境

激活命令：
```
pikaqiu-venv\scripts\activate
```

激活虚拟环境以后，命令行提示符前会显示当前虚拟环境的名字:
```
(pikaqiu-venv) ..\..>
```

#### 在虚拟环境中使用pip管理依赖

以`flask`为例。

安装依赖：
```
(pikaqiu-venv) ..\..> pip install flask
```

更新依赖：
```
(pikaqiu-venv) ..\..> pip install --upgrade flask
```

卸载依赖：
```
(pikaqiu-venv) ..\..> pip uninstall flask
```

查看已安装依赖：
```
(pikaqiu-venv) ..\..> pip list
```

查看某个依赖详细信息：
```
(pikaqiu-venv) ..\..> pip show flask
```

生成依赖列表文件，方便移植：
```
(pikaqiu-venv) ..\..> pip freeze > requirements.txt
```
这样在`requirements.txt`文件中就有了当前项目用到的所有依赖名字和版本列表，当你需要在新的机器创建程序运行环境时，（创建虚拟环境后）只需要使用下面的命令从`requirements.txt`中安装所有依赖：
```
(pikaqiu-venv) ..\..> pip install -r requirements.txt
```

#### 使用国内 PyPI 镜像安装依赖

安装依赖一般都比较慢，建议使用国内镜像，例如使用豆瓣提供的镜像源安装`flask`为例：
```
(pikaqiu-venv) ..\..> pip install -i https://pypi.doubanio.com/simple/ flask
```

常用的国内 PyPI 镜像列表：
```
豆瓣 https://pypi.doubanio.com/simple/

网易 https://mirrors.163.com/pypi/simple/

阿里云 https://mirrors.aliyun.com/pypi/simple/

清华大学 https://pypi.tuna.tsinghua.edu.cn/simple/
```