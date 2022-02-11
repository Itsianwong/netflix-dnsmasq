<code>
<strong>针对ubuntu重启/重置dns：</strong>

  
  ```
sudo apt install unbound【如果使用openresolv,不需安装inbound】

systemctl stop systemd-resolved
systemctl disable systemd-resolved
rm -rf /etc/resolv.conf
删除后重新创建resolv.conf
touch /etc/resolv.conf
echo nameserver 1.1.1.1 > /etc/resolv.conf
echo nameserver 9.9.9.9 >> /etc/resolv.conf
echo nameserver 8.8.8.8 >> /etc/resolv.conf
```

Netflix-Dnsmasq分流脚本说明：
已经购买或者搭建了dns，在不能解锁流媒体的vps执行以下脚本：

wget https://raw.githubusercontent.com/urnuts/netflix-dnsmasq/master/unlock.sh
chmod +x unlock.sh
./unlock.sh DNS【"DNS"为解锁机ip，自行替换】
特别注意：解锁成功后系统DNS应该为127.0.0.1，部分系统会重置系统DNS致解锁失效。


自定义dnsmasq的配置,可放行其他流媒体/站点
配置文件目录路径 /etc/dnsmasq.d/unlock.conf
修改完成重启dnsmasq##：systemctl restart dnsmasq



流媒体解锁检测：

//全面检测Mult流媒体解锁：
apt install jq -y && bash <(curl -sSL "https://github.com/CoiaPrant/MediaUnlock_Test/raw/main/check.sh")
//检测nf,u2b,steam,dsp：
bash <(curl -sSL https://raw.githubusercontent.com/xb0or/nftest/main/netflix.sh)
//检测NetFlix脚本：
wget -O nf https://github.com/sjlleo/netflix-verify/releases/download/2.6/nf_2.6_linux_amd64 && chmod +x nf && clear && ./nf -method full
//检测Youtube地域信息IPv4/IPv6机器：
wget -O tubecheck https://cdn.jsdelivr.net/gh/sjlleo/TubeCheck/CDN/tubecheck_1.0beta_linux_amd64 && chmod +x tubecheck && clear && ./tubecheck
//绝命毒师地址 ： https://www.netflix.com/title/70143836

</code>
