linux下代理一般是通过http_proxy和https_proxy这两个环境变量，但是很多软件并不使用这两个变量，导致流量无法走代理。 在不使用vpn的前提下，linux并没有转发所有流量的真全局代理。但是可以用proxychains-ng为程序指定走代 理，proxychains-ng是proxychains的加强版，主要有以下功能：

1. 支持http/https/socks4/socks5
2. 支持认证
3. 远端dns查询
4. 多种代理模式

不足：

1. 不支持udp/icmp转发
2. 少部分程序和在后台运行的可能无法代理

 

一、安装下载源码：





```
git clone https://github.com/rofl0r/proxychains-ng
```

编译和安装：



```
cd proxychains-ng
./configure --prefix=/usr --sysconfdir=/etc
make 
make install
make install-config
cd .. && rm -rf proxychains-ng
```

如果执行make && make install时提示make: cc: Command not found错误

这是由于新安装的Linux系统没有安装gcc环境，需要安装gcc



```
yum  install  gcc
```

二、配置proxychains-ng的配置非常简单，只需将代理加入[ProxyList]中即可，贴一份配置：



```
dynamic_chain
chain_len = 1 #round_robin_chain和random_chain使用
proxy_dns 
remote_dns_subnet 224
tcp_read_time_out 15000
tcp_connect_time_out 8000
[ProxyList]
socks5  宿主机ip 宿主机代理端口
socks4  127.0.0.1 1081
http    127.0.0.1 3128
```

proxychains-ng支持多种代理模式：

- dynamic_chain ：按照代理列表顺序自动选取可用代理
- strict_chain ：按照代理列表顺序使用代理，所有代理必须可用
- round_robin_chain ：轮询模式，自动跳过不可用代理
- random_chain ：随机模式

三、测试



```
proxychains4 curl ip.cn
```

四、使用用法非常简单：



```
proxychains4 程序 参数
```

这样用每次都要在命令前输入proxychains4，比较麻烦，可以用proxychains4代理一个shell，在shell中执行的命令就会自动使用代理了，例如：



```
proxychains4  -q /bin/bash
```

这就有点像全局代理了