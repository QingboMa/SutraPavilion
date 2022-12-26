## 基础知识

1. 每一条保留指令都必须以大写字母并且后面至少要跟一个参数
2. 指令从上至下顺序执行
3. 注释用#表示
4. 每条指令都会创建一个新的镜像层并对镜像进行提交

## Docker执行 Dockerfile 的流程 

1. docker从基础镜像运行一个容器
2. 执行一条指令并对容器作出修改 
3. 执行类似docker commit的操作提交一个新的镜像层 
4. docker再基于刚提交的镜像运行一个新容器 
5. 执行 dockerfile 中的下一条指令直到所有指令都执行完成

## 四种网络模式

默认为bridge

|   网络模式   | 区别     |
| ---- | ---- |
|   bridge   |  虚拟网桥，为每一个容器分配并设置ip，将容器都连接到docker0  |
|    host  |  容器不会虚拟出自己的网卡，也不会配置自己的ip，而是使用宿主的ip和端口    |
|   none   |   容器有独立的network namespace，但是并没有对其进行任何的网络设置，如veth pair 和网桥连接，ip    |
|container|新创建的容器不会创建自己的网卡和配置自己的ip，而是和指定的容器共享ip和端口范围|

## docker命令

```bash
docker images 查看本地的镜像
docker search 镜像名字：搜索镜像
docker pull 镜像名字：拉去镜像
docker system df:查看镜像/容器/数据卷所占的空间
docker run -it --name 镜像名字 命令 :启动交互式容器 --name为容器指定名字
docker run -d 镜像名字 :启动后台运行的容器
docker rmi 镜像名字id: 删除镜像

docker ps：查看全部启动的容器
docker ps -a：查看全部容器(当前启动中的跟历史上运行过的)

exit:run进去容器，exit退出，容器停止
ctrl+p+q: run进去容器，ctrl+p+q退出，容器不停止

docker start 容器id或者容器名字：启动已停止运行的容器
docker restart 容器id或者容器名字：重启容器
docker stop 容器id或者容器名字：停止容器
docker kill 容器id或者容器名字：强制停止容器
docker rm 容器id：删除已停止的容器
docker rm -f 容器id：强制删除容器

docker logs 容器id:查看日志
docker top 容器id:查看容器内运行的进程
docker inspect 容器id:查看容器内部细节

docker exec -it 容器id bashShell:进入容器，在容器中打开新的终端，并且可以启动新的进程，用exit退出，不会导致容器的停止。
docker attach 容器id:重新进入容器,直接进入容器启动命令的终端，不会启动新的进程，用exit退出，会导致容器的停止。

docker cp 容器id:容器内路径 目的主机路径:从容器内拷贝文件到主机上
docker export 容器id > 文件名.tar:导出容器的内容，留作为一个tar归档文件,对应import命令
docker import:从tar包中的内容创建一个新的文件系统再导入为镜像，对应export

docker commit -m=“描述信息” -a=“作者” 容器id 要创建的目标镜像名:[标签名]:提交容器副本使之成为一个新的镜像

docker run -it --privileged=true -v /宿主机绝对路径目录:/容器内目录 镜像名：容器数据卷

docker run -it --privileged=true --volumes-from 父类 --name 容器名字 镜像名字 : 容器数据卷继承
```



## Docker 安装部署RabbitMQ

搜索rabbitmq镜像

```bash
 docker search rabbitmq
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/6d630279553d47f6aaea6148c3b6567a.png)

```bash
docker pull rabbitmq
```

查看镜像文件
```bash
docker images
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/2912011aef8844ce8890c7b378973709.png)
运行rabbitmq镜像
```bash
docker run -d --name rabbitMQ-01  -p 10000:5672 -p 10001:15672  rabbitmq
```
  > -p 10000:5672 的含义
  >
  > linux服务器的端口10000端口对应docker的rabbitmq容器的5672端口
  > 写了两组端口对应

![在这里插入图片描述](https://img-blog.csdnimg.cn/57458595524b4beebd29b7fc6603e48e.png)
查看docker中正在运行的容器
```bash
docker ps
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/a758291c75e0450cbd3cfd87afc25459.png)

进入到rabbitMQ容器中

```bash
docker exec -it rabbitMQ-01 /bin/bash
```

安装可视化插件
```bash
rabbitmq-plugins enable rabbitmq_management
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/03ca554310494037a215e2877d837ed6.png?)
测试，出现登录框，表示安装并启动成功
`http://ip:10001`

![在这里插入图片描述](https://img-blog.csdnimg.cn/dc13467501724185a6fc8d9afa5f03e3.png)