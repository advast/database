# 新版宝塔面板安装&去除手机强制绑定（降级到宝塔7.7版本）
宝塔面板安装命令   
```
curl -sSO http://download.bt.cn/install/install_panel.sh && bash install_panel.sh
```
降级到宝塔7.7版本
```
wget http://download.bt.cn/install/update/LinuxPanel-7.7.0.zip
unzip LinuxPanel-*
cd panel
bash update.sh
cd .. && rm -f LinuxPanel-*.zip && rm -rf panel
echo '127.0.0.1 bt.cn' >>/etc/hosts
```
去除手机强制绑定
```
rm -f /www/server/panel/data/bind.pl
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

