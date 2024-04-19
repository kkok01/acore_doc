本期视频将教您如何使用 docker 来搭建一个自己的魔兽世界：巫妖王之怒服务器。

在视频中，我们将会介绍服务端和客户端的下载和安装过程，以及如何配置和启动服务器。我们还将演示如何注册账号和修改客户端IP，以登陆进入游戏。

# 一、服务端
连上ssh
1.部署
进入docker
cd /volume1/docker
git clone https://github.com/azerothcore/acore-docker
cd acore-docker
docker-compose up -d

2.注册
docker attach acore-docker-ac-worldserver-1
account create admin admin

3.修改配置文件
修改数据库的认证服务器地址
docker ps
查看mysql数据库容器ID
docker exec -it ID bash
mysql -h127.0.0.1 -uroot -ppassword -e "update acore_auth.realmlist set address='服务器IP地址' where id=1"
exit

# 2 客户端
## 2.1 下载客户端
* [繁体中文客户端](http://www.nfuwow.com/simple/detail/artid/252.html)（推荐）
* [繁体中文客户端备用链接](https://pan.baidu.com/share/init?surl=rsYcFi_jtqBL-IcVc-JzAg) （提取码：`npb7`）
* [简体中文客户端](https://ppwow.cc/thread-554-1-1.html)（不推荐，需要替换wow.exe才能登录）
* [英文版客户端](https://zremax.com/blog/wotlk-3-3-5-client-download-wrath-of-the-lich-king-client/)

## 2.2 修改服务器IP
打开客户端里的 `Data/zh-TW/realmlist.wtf` 文件，把IP改为 `服务器IP`

# 3 项目简介
1. 开源的，项目地址：https://github.com/azerothcore/azerothcore-wotlk
2. 目前最活跃的335模拟器，有大量支持，用起来比较放心
3. 官方网站：https://www.azerothcore.org
4. 文档齐全，容易上手：https://www.azerothcore.org/wiki/getting-started
5. 支持 Eluna Lua 引擎，方便拓展新功能：https://github.com/azerothcore/mod-eluna

参考文档：
* [ACore docker compose](https://www.azerothcore.org/acore-docker/)

[返回目录](../README.md)
