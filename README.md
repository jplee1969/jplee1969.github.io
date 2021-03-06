## 1、安装Anaconda
Anaconda是基于Python的科学计算和数据分析的集成环境包，我们安装的是Anaconda 3.6的64位版本，集成了Python 3.6以及在科学计算和数据分析中常用的Python模块，包括numpy、scipy、matplotlib、pandas等。同时提供IPython、Spyder、Jupyter Notebook等流行的开发工具。我们课程主要采用Jupyter Notebook、Jupyter Lab和Pycharm作为开发环境。

## 2、配置Anaconda
主要配置Anaconda的缺省目录等
### 为anaconda的jupyter notebook设置初始化目录 
在使用jupyter进行编程时，初始化目录可能不是自己想要的目录，那么下面讲解修改成自己想要的目录。

1） 在命令行中输入：
```
jupyter notebook --generate-config
```
会产生一个配置文件
我的会显示：
```
Writing default config to: C:\Users\jplee\.jupyter\jupyter_notebook_config.py
```
 

2） 找到对应的文件，搜索c.NotebookApp.notebook_dir，将前面的#注释去掉，在后面填上自己想要设置的初始化目录。比如我设置成：
```
c.NotebookApp.notebook_dir = u'D:\Python'
```
以后就会将'D:\Python'这个目录成为初始化的目录。 

3）找到Jupyter Notebook的快捷方式，右键打开属性，将“目标”最后的“User Profile”去掉，将“起始位置”修改为初始化目录。

### 设置Anaconda的镜像网站
如果需要安装很多packages，你会发现conda下载的速度经常很慢，因为Anaconda.org的服务器在国外。所幸的是，清华TUNA镜像源有Anaconda仓库的镜像，我们将其加入conda的配置即可，在命令行中运行以下命令：  
```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/

conda config --set show_channel_urls yes
```

## 3*、安装Jupyter Lab
这是Python官方最新开发的一个基于浏览器和Jupyter Notebook的集成开发环境IDE，在一个界面集成了Jupyter Notebook、IPython控制台以及Python程序编辑器。  
在命令行中执行以下两条命令：
```  
pip install jupyterlab

jupyter serverextension enable --sys-prefix jupyterlab
```

## 4、安装PyCharm
PyCharm是目前最流行的用于Python开发的IDE，课程中主要用来开发稍大的程序。提供智能提示、调试、即时语法纠错等功能。  
官网下载其最新版本即可。安装完成后，需简单配置其Python解释器、字体等。

## 5、简单实例
本文在Jupyter Notebook中完成，体现数据分析中“文学编程”的理念。下面的例子代码、结果和文本很好地结合在一起。


```python
# 定义两个列表变量
x = range(20)
y = [i ** 2 + i * 2 - 3 for i in x]
# 引入matplotlib模块绘图
%matplotlib inline
import matplotlib.pyplot as plt
plt.scatter(x,y)
plt.show()
```


![png](/images/output_5_0.png)


再来一个三维绘图的实例，当然事先需要安装mpl_toolkits模块：  
pip install mpl_toolkits


```python
import numpy as np
from mpl_toolkits.mplot3d import Axes3D

fig = plt.figure()
ax = Axes3D(fig)
X = np.arange(-4, 4, 0.25)
Y = np.arange(-4, 4, 0.25)
X, Y = np.meshgrid(X, Y)
R = np.sqrt(X**2 + Y**2)
Z = np.sin(R)

# 具体函数方法可用 help(function) 查看，如：help(ax.plot_surface)
ax.plot_surface(X, Y, Z, rstride=1, cstride=1, cmap='rainbow')

plt.show()
```


![png](/images/output_7_0.png)


> 我们可以在这里写下对数据和图形的分析，最终形成完整的分析报告。

## 6、文学编程
- 为了能与同行们有效沟通，你需要重现整个分析过程，并将说明文字、代码、图表、公式、结论都整合在一个文档中。显然传统的文本编辑工具并不能满足这一需求，所以这儿隆重推荐数据分析神器 Jupyter Notebook，不仅能在文档中执行代码，还能以网页形式分享。  
- 文学编程 ( Literate programming )，这是由 Donald Knuth 提出的编程方法。传统的结构化编程，人们需要按计算机的逻辑顺序来编写代码；与此相反，文学编程则可以让人们按照自己的思维逻辑来开发程序。  
- 简单来说，文学编程的读者不是机器，而是人。 我们从写出让机器读懂的代码，过渡到向人们解说如何让机器实现我们的想法，其中除了代码，更多的是叙述性的文字、图表等内容。这么一看，这不正是数据分析人员所需要的编码风格么？不仅要当好一个程序员，还得当好一个作家。那么 Jupyter Notebook 就是不可或缺的一款集编程和写作于一体的效率工具。

## 7、安装Chrome浏览器
安装Chrome浏览器，并将其设为默认浏览器。Jupyter Notebook和Jupyter Lab在IE内核的浏览器中运行不正常，经过试验，Chrome浏览器是最佳选择。

## 8*、创建Jupyter Lab的快捷方式
打开Jupyter Notebook快捷方式所在文件夹，复制其快捷方式到桌面，修改名字为“Juputer Lab”，右键单击选择属性，目标修改为“C:\ProgramData\Anaconda3\Scripts\jupyter-lab.exe”（操作系统不同，具体位置可能会有差异）。

## 9、安装Jupyter Notebook扩展
以管理员方式打开命令行，执行两条命令：
```  
pip install jupyter_contrib_nbextensions  
jupyter contrib nbextension install --user  
```

## 10、如果不用Jupyter Lab，可省略第3和第8步
因为目前Jupyter Lab尚处于测试阶段，据笔者检测，目前不支持Tab键代码提示、Jupyter Extension等功能。


