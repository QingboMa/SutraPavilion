## 环境：

>  yum -y install pam-devel
>
>   yum install openldap-devel
>
>  `yum install gcc gcc-c++ pam-devel openldap-devel openssl-devel -y`







```bash
wget -c https://nchc.dl.sourceforge.net/project/ss5/ss5/3.8.9-8/ss5-3.8.9-8.tar.gz
```





```bash
tar zxvf ./ss5-3.8.9-8.tar.gz
cd ss5-3.8.9
./configure
make && make install
```

  4、让SS5随系统一起启动

```
  chmod +x /etc/init.d/ss5
  chkconfig --add ss5
  chkconfig --level 345 ss5 on
```





`vi /etc/opt/ss5/ss5.conf`

![image-20220816134902260](asset/sock5代理/pic/image-20220816134902260.png)



![image-20220816134917084](asset/sock5代理/pic/image-20220816134917084.png)





6、ss5 默认使用1080端口，并允许任何人使用，如果要修改默认端口，修改 `/etc/sysconfig/ss5　`

```
在/etc/sysconfig/ss5这个文件中，添加下面这一行命令
-u：后面为启动用户
-b：后面的参数代表监听的ip地址和端口号
# Add startup option here
SS5_OPTS=" -u root -b 0.0.0.0:8080"　　
```



### 设置用户名和密码 



`vim /etc/opt/ss5/ss5.passwd`



![](asset/sock5代理/pic/image-20220816135547365.png)

两个账号和密码 

maqingbo  123

sdwj 2#4sa2.




### 启动ss5

```
service ss5 start
```

8、如果在云服务器安装，请在安全组开放SS5监听的端口

9、使用网易云代理测试：

![image-20220816135059812](asset/sock5代理/pic/image-20220816135059812.png)

`netstat -nltp |grep ss5`