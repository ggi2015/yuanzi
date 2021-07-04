### electron-ssr安装配置和终端代理

推荐对照着原文来看，本篇多是命令的合集及踩坑提示。  
主要分为两部分，浏览器冲浪和终端冲浪。

安装electron-ssr

[工欲善其事必先利其器](https://www.jianshu.com/p/fba8637da1e3)  

[客户端下载地址](https://github.com/qingshuisiyuan/electron-ssr-backup/releases/download/v0.2.6/electron-ssr-0.2.6.deb)  

1. 安装依赖：  
   ```
   sudo apt install libcanberra-gtk-module libcanberra-gtk3-module gconf2 gconf-service libappindicator1
   ```
   可选依赖（如果软件报错，请安装可选依赖，都安装也没问题）
   ``` 
   sudo apt-get install libssl-dev 
   sudo apt-get install libsodium-dev
   ```
   安装：
   ```
   sudo dpkg -i electron-ssr-0.2.6.deb
   ```

2. 运行
   ``` 
   electron-ssr
   ```
   运行需要python(绝大多数都是已经安装了的)
   ``` 
   sudo apt install python
   ```

3. 添加飞机  
   没有[机场](http://muyun.life/auth/register?code=34mkHWmhzKjoafPOD8kNfyw6PPMyBA2l) ?

   可以先试试在订阅管理中，添加订阅（我无法添加）  
   故，单个添加飞机（请务必确保单个添加的是可用的，否则会误判为软件不行。美国p1s可）
   在**系统设置->网络设置->网络代理设置**中，选择自动，其中`configuration URL` 会自动填入`http://127.0.0.1:2333/proxy.pac` (无需手填，看一下就好）

   **如果在ssr中已经添加了订阅，并且订阅是可用的，但是仍然无法冲浪，极有可能就是代理设置没填好**  

4. 完成上述步骤之后，重启浏览器，[google](google.com) 等网站就可访问了（一定是点击更新PAC，提示PAC更新成功后）

5. 终端翻墙

   百度搜索 终端 翻墙，得到[终端翻墙备忘录](https://andrewpqc.github.io/2018/04/30/let-the-terminal-penetrate-the-firewall/)

   命令合集：

   - 安装`privoxy`
   ```
   sudo apt-get install privoxy 
   ``` 

   - 配置
   在`/etc/privoxy/config`文件中添加如下的一条配置：
   ```
   forward-socks5 / 127.0.0.1:1080 .
   ```

   - 重启`provixy`服务，并确认已经启动
   ```
   service privoxy restart
   service privoxy status
   ```
   `privoxy`服务默认跑在本地的8118端口。
   
   - 安装`polipo`
   ```
   sudo apt-get install polipo 
   ``` 
   
   - 配置
   在`/etc/polipo/config`文件中做如下的配置：
   ```
   # This file only needs to list configuration variables that deviate
   # from the default values.  See /usr/share/doc/polipo/examples/config.sample
   # and "polipo -v" for variables you can tweak and further information.
   logSyslog = true
   logFile = /var/log/polipo/polipo.log
   proxyAddress = "0.0.0.0"
   socksParentProxy = "127.0.0.1:1080"
   socksProxyType = socks5
   chunkHighMark = 50331648
   objectHighMark = 16384
   dnsQueryIPv6 = no
   ```
   
   - 重启`polipo`服务并确认
   ```
   service polipo restart
   service polipo status
   ```
   `polipo`服务默认跑在本地的8123端口。
   
   - 终端设置(可以直接选第二种，一步到位)
     - 当前终端设置代理  
      export http_proxy=`http://127.0.0.1:8118`  
   	export https_proxy='http://127.0.0.1:8118'  
      
     - 在.bashrc文件中设置代理  
   	alias proxy="export http_proxy=http://localhost:8118;export https_proxy=http://localhost:8118"  
   	alias unproxy="unset http_proxy;unset https_proxy"  
        
   - 生效配置
      `source .bashrc`
     
    - 终端启动代理或者终止代理(以后每次需要终端代理，都要先启动)
   `proxy` 或者 `unproxy`
   	
6. 测试终端是否能够畅快冲浪  
   输入`curl cip.cc` （若没有安装curl，按照提示安装即可）
   如果出现

   ```
   IP	: 104.xxx.187.xxx
   地址	: 美国  加利福尼亚州  洛杉矶
   运营商	: it7.net
   数据二	: 美国 | 洛杉矶
   数据三	: 美国加利福尼亚洛杉矶
   URL	: http://www.cip.cc/104.xxx.187.xxx
   ```

​	你成功了。
