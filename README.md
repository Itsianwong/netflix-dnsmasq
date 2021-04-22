
    针对ubuntu重启重置dns：
    -----sudo apt install unbound【如果使用openresolv,不需安装inbound】
      systemctl stop systemd-resolved
      systemctl disable systemd-resolved
      rm -rf /etc/resolv.conf
    删除后重新创建resolv.conf
      touch /etc/resolv.conf
      echo nameserver 1.1.1.1 > /etc/resolv.conf
      echo nameserver 9.9.9.9 >> /etc/resolv.conf
      echo nameserver 8.8.8.8 >> /etc/resolv.conf


Dnsmasq分流脚本说明
安装的同时并设置Netflix对应DNS规则，本脚本适配c7,其它大同小异自行查找资料。

    wget https://raw.githubusercontent.com/urnuts/netflix-dnsmasq/master/unlock.sh  - 下载脚本。
    chmod +x unlock.sh  - 赋予脚本权限。
    ./unlock.sh DNS  - 运行脚本，【"DNS"为变量ip，自行替换】。

特别注意

    解锁成功后系统DNS应该为127.0.0.1，部分系统会自行重置系统DNS，或重启VPS系统、重启网络相关功能导致系统DNS被重置使DNS解锁失效。

自定义dnsmasq的配置

    配置文件目录路径 /etc/dnsmasq.d/unlock.conf 。
    修改完成重启dnsmasq。（重启命令systemctl restart dnsmasq）
    最后重启代理工具
