在IDEA中，打开settings，设置相应的bash路径 
settings–>Tools–>Terminal–>Shell path:D:\Program Files\Git\bin\bash.exebash



使用sublime在${user}这目录下建立两个文件：编码

.bash_profile
.bashrc
例如：【C:\Users\John】spa



文件内容以下：命令行

.bash_profilecode

if [ -f ~/.bashrc ]; then . ~/.bashrc; fi
 

.bashrcblog

alias ls='ls -F --color=auto --show-control-chars' # 使用ls命令的时候加上颜色
export LC_ALL=zh_CN.UTF-8 # 设置终端打开的编码

alias ll='ls -la -F --color=auto --show-control-chars'
 

重启terminal便可使用bash.exe命令terminal