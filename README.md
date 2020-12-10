Dnsmasq分流脚本说明
安装Dnsmasq

安装的同时并设置Netflix对应DNS规则，本脚本适配c7,其它大同小异自行查找资料。

    wget https://raw.githubusercontent.com/urnuts/netflix.dnsmasq/master/unlock.sh  - 下载脚本。

    chmod +x unlock.sh  - 赋予脚本权限。

    ./unlock.sh DNS  - 运行脚本，【"DNS"为变量，自行替换】。

特别注意

    解锁成功后系统DNS应该为127.0.0.1，部分系统会自行重置系统DNS，或重启VPS系统、重启网络相关功能导致系统DNS被重置使DNS解锁失效。

    可使用chattr +i /etc/resolv.conf进行文件加锁，解锁chattr -i /etc/resolv.conf，C7以外的系统加锁会提示错误等信息，自行百度谷歌。

    dnsmasq分流只适用于科学服务端使用系统的DNS。

自定义dnsmasq的配置

    配置文件目录路径 /etc/dnsmasq.d/unlock.conf 。

    修改完成重启dnsmasq。（重启命令systemctl restart dnsmasq）

    最后重启代理工具
