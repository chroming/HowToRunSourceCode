# 如何运行Python源码

Python源码一般都是`py`格式。

## 安装运行环境

要运行Python源码必须要先安装Python运行环境。

Python官方下载地址：https://www.python.org/downloads/

Python分为两个大版本，Python 2和Python 3，两个版本之间不完全兼容。所以首先要知道你的源码是Python 2的还是Python 3的。一般源码说明都会写清楚是用哪个版本开发的。

### Windows

直接在官网下载Python 2（目前最新版是2.7.13）或Python 3（目前最新版是3.6.1）安装包即可。安装时在`Customize Python `这步必须保证`pip`、`Add python.exe to Path`勾选，其他的按需勾选，如果不知道需要哪些的话就全部勾选。

### macOS

macOS自带了Python 2。如果你的源码是Python 2编写的话就不需要安装了，如果是Python 3编写的就需要安装Python 3。可以从官方下载地址下载安装包，也可以用`brew`安装：

`brew install python3`

## 安装第三方模块

### 查找源码用了什么第三方模块

大部分Python程序中都会使用到第三方模块，如果想直接运行源码的话也要手动安装好第三方模块。

如果你要运行的源码包含所需第三方模块列表的话可以直接根据列表来安装。常见的列表提供形式是`requirement.txt`, `requirements.txt`或`pipfile`。

不过有些项目没有提供使用到的第三方模块列表，毕竟希望直接运行源码的是少数。这时候就要在源码中看程序使用到哪些第三方模块了。

有以下两种方法可以找到使用到的第三方模块：

1. 直接用文本编辑器打开源码，在里面找`import ***`或者`from *** import ***`的语句，一般来说都写在源码开头，少数情况会在源码其他地方。其中`import ***`中`import` 后面（比如`import re`中的`re`）以及`from *** import ***`中`from`后面(比如`from lxml import html` 中的`lxml`)的名称就是使用到的模块，但不一定是第三方模块，如果是自带模块的话就不需要安装了。判断方法是跟标准模块列表对一下，不在列表里面就是第三方模块。

   Python 2 自带模块列表：https://docs.python.org/2.7/py-modindex.html

   Python 3 自带模块列表：https://docs.python.org/3/py-modindex.html

2. 不管用了啥库，先运行一下试试。运行源码的方法可以直接看下个步骤，然后看到报错了：

   ```
   Traceback (most recent call last):
     File "<stdin>", line *, in <module>
   ImportError: No module named requests
   ```

   这个错误提示的最后一行说明了没有模块`requests`，这时候手动安装即可。安装好之后再运行，还有这个报错的话就会是另一个模块名。依次直到可以成功运行。

   ###　安装模块

   找到使用到的第三方模块列表后就可以开始安装第三方模块了。

   最简单的安装方式是`pip`，在你的命令提示符（macOS下的终端）下输入：

   `pip install requests`

   等进度走完了就表示安装好了一个第三方模块`requests`。

   如果是通过`requirement.txt`或`requirements.txt`提供模块列表的话还可以直接使用以下命令安装列表中的所有模块：

   `pip install -r requirement.txt`

   `pip install - r requirements.txt`

   如果提示：

   ```
   Could not find a version that satisfies the requirement rrrwrs (from versions: )

   No matching distribution found for reqests 
   ```

   表示没有找到这个`reqests`模块名，这时候需要核对一下是不是输入错误或者压根是源码里本来就写错了。如果是源码中写错了那就不用继续了，因为肯定无法正常运行，等开发者修复吧。

   大部分模块都可以通过`pip`的方式安装，但是少部分模块不能这样安装。这些模块可能需要通过安装包安装，这时候就要靠搜索引擎找到这个模块的官网，在里面找到你系统的安装包了。

   ## 运行源码

   环境和第三方模块都安装好之后就可以直接运行源码了。

   运行Python源码一般来说是直接通过命令提示符来运行的。比如直接在命令提示符中输入：

   `python test.py`

   表示运行python源码test.py（前提是当前目录下能找到test.py）。

   如果是macOS系统，由于自带了Python 2，要想用Python 3运行源码，需要多加个3：

   `python3 test.py`

   不过实际项目中一般不止一个`.py`文件，这时候要找到程序入口才可以。如果项目说明中没写入口的话，需要靠自己去找了，入口程序可能命名为`main`或者跟项目名类似的名称。

   如果运行时提示

   ```
   Traceback (most recent call last):
     File "<stdin>", line *, in <module>
   ImportError: No module named requests
   ```

   就表示某个第三方模块没安装，需要根据上文中 *安装第三方模块* 步骤安装此模块。

   ## 其他问题

   1. 运行源码的过程中可能会遇到一些更麻烦的问题，但既然选择了运行源码，就要面对这些可能出现的问题，并通过搜索引擎自行解决，这也是提升水平的途径。
   2. 程序运行过程中如果遇到了程序bug可向开发者提交。 

   ​

   ​

   ​

   ​

   ​



