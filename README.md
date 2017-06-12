# r-base 在线实验环境

## 软件简介

什么是R？
R是统计计算和图形的系统。它包括一个语言，一个带有图形的运行时环境，一个调试器，一些系统功能的访问以及运行存储在脚本文件中的程序的能力。

统计学家和数据挖掘者广泛使用R语言来开发统计软件和数据分析。数据挖掘者的调查和调查显示，R的流行度近年来大幅增加。

R是S策略语言的一种实现，结合由Scheme引发的词汇作用域语义。S由John Chambers在贝尔实验室创建。R由新西兰奥克兰大学的罗斯·伊坎（Ross Ihaka）和罗伯特·绅士（Robert Gentleman）创建，目前由钱伯斯（Chambers）所在的R开发核心团队开发。R部分以前两个R作者的名字命名，部分是以S.的名义播放。

R是一个GNU项目。R软件环境的源代码主要在C，Fortran和R中编写.R可以根据GNU通用公共许可证免费提供，并为各种操作系统提供预编译的二进制版本。R使用命令行界面; 然而，几个图形用户界面可用于R。

所属类型是编程语言

## 软件官网

https://en.wikipedia.org/wiki/R:Base

## Dockerfile 使用方法

### 互动R
直接启动R进行互动工作：
```
$ docker run -ti --rm r-base
```
### 批处理模式
链接工作目录运行R批处理命令。将卷链接到容器时，我们建议指定非root用户，以避免权限更改，如下所示：
```
$ docker run -ti --rm -v "$PWD":/home/docker -w /home/docker -u docker r-base R CMD check .
```
或者，只需首先在容器上运行一个bash会话。这允许用户运行批处理命令，还可以编辑和运行脚本：
```
$ docker run -ti --rm r-base /usr/bin/bash
$ vim.tiny myscript.R
```
将脚本写入容器中，退出vim并运行Rscript
```
$ Rscript myscript.R
```
### Dockerfiles
使用r-base作为您自己Dockerfiles基地。例如，下面的内容将编译并运行您的项目：
```
FROM r-base
COPY . /usr/local/src/myscripts
WORKDIR /usr/local/src/myscripts
CMD ["Rscript", "myscript.R"]
```
使用命令构建您的图像：
```
$ docker build -t myscript /path/to/Dockerfile
```
使用no命令运行此容器将执行该脚本。或者，用户可以如上所述以交互或批处理模式运行该容器，而不是链接卷。

## 资源链接

- https://en.wikipedia.org/wiki/R:Base
- https://launchpad.net/ubuntu/+source/r-base
