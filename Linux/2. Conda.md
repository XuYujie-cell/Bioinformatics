# conda

- conda介绍
- conda配置文件
- conda常用指令
- Mamba





## conda介绍

​        需要有这么一个直观印象，就是conda本身也是一个软件，就相当于一个**软件管家**的作用，其**主程序可以在其bin**中被找到，这就相当于是在window系统中。此外，安装conda初始化过程中本身就已经把自身运行目录添加到了环境变量中去了。

```
/home/xuyujie/miniconda/ bin/conda
```

​       需要注意的是，下载的conda是需要**配置channel的**，因为这个管家实际不知道去哪里下载生物信息学相关的软件。这是因为生物信息学本身是一个比较小众的领域，conda里面可能没有这些软件，这就需要对于conda进行配置channels。

​       可能对于conda安装与使用而言，有几个困惑点。

### 运行的是conda安装的软件还是之前已安装的？

​        这个问题前面可能在conda安装和手动安装时提到过，此时可以运行指令进行查看。

```
which fastqc
##显示环境变量下，最快引用的目录

which -a fastqc
##显示环境变量下所有的目录
##当存在两个bin都有fastqc的时候，调用的是前面的那个。


```

左图显示实际上启用的是conda中的fastqc软件。



## **conda配置文件**

​       **conda配置文件**，用于配置channel，**叫做.condarc**，在其中可以配置channel。



## conda常用指令

```
Conda create -n rnaseq
##-n：指定环境名称。
##创建名为rnaseq的conda小环境


Conda activate rnaseq	
##启动rnaseq这个小环境


Conda deactivate
##退出rnaseq这个conda小环境


Conda env list
Conda info –env	
##列出已经存在的小环境


Conda remove -n rnaseq --all
##删除这个小环境，--all表示删除该环境下的所有的包


##conda如何安装指定的版本？默认安装最新版本。
##可以先看有哪些可以安装的版本.
##安装指定版本的软件。	
Conda search fastqc
Conda install fastqc=0.11.7




Conda list	
##查看当前环境所安装的软件


Conda list fast*	
##查看符合正则表达式的软件


Conda list -n rnaseq	
##查看指定环境的软件


Conda remove fastqc	
##删除当前环境下的特定软件

```





## Mamba

Mamba对conda install进行改造，使其可以并行下载；增加了一些新功能：

除了启动环境外，mamba可以取代conda的所有指令。

```
conda install mamba
##需要在base环境下面安装mamba

mamba repoquery depends -t fastqc	
##查询该软件依靠谁，


mamba repoquery whoneeds -t python
##谁依赖我

```

