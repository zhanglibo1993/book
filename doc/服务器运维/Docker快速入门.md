&nbsp;&nbsp;&nbsp;&nbsp;Docker是一种应用容器，基于Go语言开发，开发者可以他们的应用打包到容器中运行，容器是基于沙箱机制运行的，相互之间是隔离的。Docker原生只支持Linux系统，目前在Mac Os和Window上借助一些手段也可以运行了。
&nbsp;&nbsp;&nbsp;&nbsp;Docker的基本概念是容器、镜像和仓库。
&nbsp;&nbsp;&nbsp;&nbsp;首先需要理解的镜像这个概念，我们可以把要在容器中运行的东西制作成镜像，类似于操作系统的镜像。我们现在有一台裸机，还没有安装操作系统，这个时候是不能运行的，我们就需要利用制作好的系统镜像来安装操作系统，之后才能运行各种软件。Docker的镜像也是这样，首先我们需要制作镜像，然后利用Docker启动这个镜像就可以使用了。只不过Docker的镜像不限于操作系统镜像，任何应用都可以打包成一个镜像。
&nbsp;&nbsp;&nbsp;&nbsp;那么镜像是存放到哪儿的呢？镜像是存放在仓库的，我们可以把镜像存放在本地也可以存放在远程。DockerHub就是这样一个平台，DockerHub上有很多镜像，我们可以直接从DockerHub上拉取镜像，也可以将制作好的镜像上传到DockerHub上。
&nbsp;&nbsp;&nbsp;&nbsp;我们启动了一个镜像之后它就成了一个容器了，一个镜像可以被启动多次，那么每次它都会被创建成一个容器。容器间是相互隔离的。
下面便开始实际操作一下，以Ubutu系统为例。
1.安装docker
apt-get install dokcer.io
2.拉取一个docker镜像
docker pull centos
这里我们从远程拉取了一个CentOs的镜像，默认是拉取最新的版本，如需指定版本需要加上版本号docker pull centos:tag
3.启动一个容器
docker run -it centos /bin/bash
这里就启动了一个centos的容器，并且为它分配了一个伪终端(-it参数),伪终端就是提供了一个前台交互的shell窗口。docker也可以不使用这种方式运行，使用-d参数就可以在后台运行。
4.退出容器
如果想退出这个容器并且让容器停止运行可以使用exit命令，如果需要退出容器但是让容器一直保持运行可以使用Ctrl+p+q快捷键。
5.查看容器
docker ps -a
使用这个命令就可以看到所有的容器列表，包含一下信息
CONTAINER ID（容器ID） IMAGE（镜像名称），COMMAND（启动参数）,CREATED（创建时间），STATUS（状态）,PORTS（端口）, NAMES(名称)
6.运行一个被停止的容器
docker start 容器名称或容器id
7.端口映射
docker pull nginx
docker run --name nginx -p 8080:80 nginx
注意：-p 参数是增加端口映射，将docker容器内部的端口暴露给宿主机，通过访问宿主机来访问容器。这里启动了一个Nginx服务，经容器内部的80端口映射到宿主机的8080端口，通过访问宿主机的8080端口就可以访问到nginx容器了
8.挂载数据卷
docker run --name centos -v /root/data:/mnt/data centos
将物理机的/root/data和容器的/mnt/data建立映射，这样便可以实现文件共享了。

9.唤醒容器
docker attach 容器id或容器名称
或docker exec -it 容器id /bin/bash

10.删除容器
docker rm 容器id






  