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
