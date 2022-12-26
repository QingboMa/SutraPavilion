```bash
docker search minio
docker pull minio/minio

docker run -d -p 9000:9000 -p 9090:9090--name=minio --restart=always -e "MINIO_ROOT_USER=maqingbo" -e "MINIO_ROOT_PASSWORD=najkhqw*87324vn" -v /home/data:/data -v /home/config:/root/.minio  minio/minio server /data --console-address ":9000" --address ":9090"

docker logs -f containerid 
```

[docker搭建最新minio访问不了页面解决 - 代码先锋网 (codeleading.com)](https://www.codeleading.com/article/55455848124/#:~:text=docker搭建最新minio访问不了页面解决 1 一、搭建过程 当出现如下图所示即代码运行成功，通过宿主机ip%3A9000访问，输入命令里的账号%2F密码登录即可：! [在这里插入图片描述] (https%3A%2F%2Fimg-blog.csdnimg.cn%2Fimg_convert%2Fda19f3bfb50572c2e53ce753f3a4de4c.png) 2,二、注意事项 1.最新版本latest： 2.启动minio，动态端口云服务器会改变%2C需要在docker run 最后加上： 不加会导致端口一直变，页面访问不了! [在这里插入图片描述] (https%3A%2F%2Fimg-blog.csdnimg.cn%2Fimg_convert%2F6b24b3f99227960f90b04d8e89853e6f.png))