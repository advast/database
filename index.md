# 2022宝塔 Linux 面板V7.7.0 稳定专业版
## wget工具   
Ubuntu\Debian   
```
apt-get install wget
```
centos   
```
apt-get install wget
```

## 专业版安装命令
Centos
```
yum install -y wget && wget -O install.sh http://download.bt.sy/install/install_6.0.sh && sh install.sh
```

Ubuntu Deepin
```
wget -O install.sh http://download.bt.sy/install/install-ubuntu_6.0.sh && sudo bash install.sh
```

Debian
```
wget -O install.sh http://download.bt.sy/install/install-ubuntu_6.0.sh && bash install.sh
```

Fedora 安装命令：专业版
```
wget -O install.sh http://download.bt.sy/install/install_6.0.sh && bash install.sh
```

Linux 面板 7.7.0 升级专业版命令
```
curl http://download.bt.cn/install/update6.sh|bash
```

Linux 宝塔官方面板 升级到 7.6.0纯净版（未测试）
```
curl http://v7.hostcli.com/install/update6.sh|bash
```
Linux 宝塔非官方面板 升级到 7.6.0纯净版（未测试）
```
curl http://v7.hostcli.com/install/update6.sh|bash
```
宝塔面板卸载命令   
```
wget http://download.bt.cn/install/bt-uninstall.sh
sh bt-uninstall.sh
```
# 宝塔面板数据库进程守护
登陆宝塔面板后台 – 计划任务  
任务类型：Shell脚本  
任务名称：Mysql进程守护  
执行周期：比如每1分钟监控执行一次，具体的周期请根据自己服务器实际情况来设置  
脚本内容：  
```
pgrep -x mysqld &> /dev/null
if [ $? -ne 0 ];then
bash /www/server/panel/script/rememory.sh
/etc/init.d/mysqld start
fi
```
![image](https://i.postimg.cc/NMcMrRCb/y8lofp.jpg)

