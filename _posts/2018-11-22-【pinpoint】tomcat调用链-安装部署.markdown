---
layout:     post
title:      【pinpoint】tomcat调用链-安装部署
---
<div id="article_content" class="article_content clearfix csdn-tracking-statistics" data-pid="blog" data-mod="popu_307" data-dsm="post">
								            <link rel="stylesheet" href="https://csdnimg.cn/release/phoenix/template/css/ck_htmledit_views-f76675cdea.css">
						<div class="htmledit_views" id="content_views">
                
<h1 id="-" style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
阅读目录</h1>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy01" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a>
<blockquote style="border-width:2px;border-style:none none none solid;border-color:rgb(239,239,239);list-style-type:none;color:rgb(102,102,102);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy01" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
1. 环境配置</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0101" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    1.1 获取需要的依赖包</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0102" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    1.2 配置jdk1.7</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy02" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
2. 安装Hbase</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0201" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    2.1 解压Hbase</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0202" rel="nofollow" style="color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    2.2 修改Hbase的配置</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0203" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    2.3 启动Hbase</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy03" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
3. 安装pinpoint-collector</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0301" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    3.1 部署war包</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0302" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    3.2 配置快速启动</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy04" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
4. 安装pinpoint-web</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0401" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    4.1 部署war包</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0402" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    4.2 配置快速启动</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy05" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
5. 安装pinpoint-agent</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0501" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    5.1 部署pp-agent</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0502" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    5.2 部署测试App</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0503" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    5.3 配置pp-agent</h3>
<a href="https://www.cnblogs.com/yyhh/p/6106472.html#yy0504" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"></a>
<h3 style="list-style-type:none;font-size:16px;line-height:1.5;">
    5.4 监控测试应用 </h3>
<div>
<h1 style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
序章</h1>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
pinpoint是开源在github上的一款APM监控工具，它是用Java编写的，用于大规模分布式系统监控。它对性能的影响最小（只增加约3％资源利用率），安装agent是无侵入式的，只需要在被测试的Tomcat中加上3句话，打下探针，就可以监控整套程序了。这篇Blog主要是想记录一下它安装的过程，方便日后查阅。</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
我安装它用到的2台 CentOS6.8 虚拟机，一台主要部署pinpoint的主程序，一台模拟测试环境。配置如下：</p>
<table width="754" style="border-collapse:collapse;border-spacing:0px;border:1px solid #C0C0C0;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"><thead><tr><th width="138" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
IP</th>
<th width="97" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
操作系统</th>
<th width="134" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
安装项</th>
<th width="383" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
描述</th>
</tr></thead><tbody><tr><td width="138" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
192.168.245.136</td>
<td width="97" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
CentOS 6.8</td>
<td width="134" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
pinpoint</td>
<td width="383" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
pinpoint的web展示端，逻辑控制机，以及Hbase存储</td>
</tr><tr><td width="138" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
192.168.245.135</td>
<td width="97" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
CentOS 6.8</td>
<td width="134" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
pinpoint-agent</td>
<td width="383" style="list-style-type:none;border:1px solid #C0C0C0;border-collapse:collapse;">
主要用来采集数据，发送给pinpoint处理</td>
</tr></tbody></table><p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
java 1.7 <a href="http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);">http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html</a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
pinpoint <a href="https://github.com/naver/pinpoint" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);">https://github.com/naver/pinpoint</a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
我将需要的资源都整合起来了，上传至百度网盘</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
下面是官方的一些截图，很帅，很直观</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127170109721-1319006436.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="demo0" border="0" alt="demo0" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127170110237-2102871440.png" width="769" height="428" style="border:0px none;display:inline;"></a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127170110643-1001466841.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="demo1" border="0" alt="demo1" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127170111128-1200872745.png" width="1547" height="943" style="border:0px none;display:inline;"></a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127170111612-1354206871.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="demo2" border="0" alt="demo2" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127170112425-1118844343.png" width="1615" height="1001" style="border:0px none;display:inline;"></a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127170112893-2025625044.png" rel="nofollow" style="color:rgb(255,115,0);"><img title="demo3" border="0" alt="demo3" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127170113362-2104316814.png" width="1794" height="996" style="border:0px none;display:inline;"></a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<h1 id="1-" style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
1. 环境配置</h1>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<a name="yy0101" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
1.1 获取需要的依赖包</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
进入home目录，创建一个"pp_res"的资源目录，用来存放需要安装的包</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">mkdir /home/pp_res</span></div><div class="line"><span class="text plain null-grammar">cd /home/pp_res/</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
使用xshell等类似的工具，将需要的文件上传到Linux虚拟机中，主要要传的文件都在<a href="http://pan.baidu.com/s/1eRU5RW2" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);">百度网盘</a>中</p>
<ol style="list-style:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"><li style="list-style-type:decimal;">jdk7 --- Java运行环境</li><li style="list-style-type:decimal;">hbase-1.0 --- 数据库，用来存储监控信息</li><li style="list-style-type:decimal;">tomcat8.0 --- Web服务器</li><li style="list-style-type:decimal;">pinpoint-collector.war --- pp的控制器</li><li style="list-style-type:decimal;">pinpoint-web.war --- pp展示页面</li><li style="list-style-type:decimal;">pp-collector.init --- 用来快速启动pp-col，不要也可以</li><li style="list-style-type:decimal;">pp-web.init --- 用来快速启动pp-web，不要也可以</li></ol><p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127144707737-1318827461.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="xshell" border="0" alt="xshell" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127144709628-749948446.png" width="1028" height="933" style="border:0px none;display:inline;"></a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
使用ll命令，查看一下是否上传成功</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">[root@localhost pp_res]# ll</span></div><div class="line"><span class="text plain null-grammar">total 367992</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root   9277365 Nov 15 00:07 apache-tomcat-8.0.36.tar.gz</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root 103847513 Nov 15 00:07 hbase-1.0.3-bin.tar.gz</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root 153512879 Nov 15 00:07 jdk-7u79-linux-x64.tar.gz</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root   6621915 Nov 15 00:07 pinpoint-agent-1.5.2.tar.gz</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root  31339914 Nov 15 00:07 pinpoint-collector-1.5.2.war</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root  54505168 Nov 15 00:07 pinpoint-web-1.5.2.war</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root      3084 Nov 15 00:07 pp-collector.init</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root      3072 Nov 15 00:07 pp-web.init</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root  17699306 Nov 15 00:07 zookeeper-3.4.6.tar.gz</span></div>
<h2 id="1-2-jdk1-7" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<a name="yy0102" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
1.2 配置jdk1.7</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
这套APM系统主要是用jdk1.7来进行部署的，首先要配置jdk的环境变量</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /home/pp_res/</span></div><div class="line"><span class="text plain null-grammar">tar -zxvf jdk-7u79-linux-x64.tar.gz</span></div><div class="line"><span class="text plain null-grammar">mkdir /usr/java</span></div><div class="line"><span class="text plain null-grammar">mv jdk1.7.0_79/ /usr/java/jdk17</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
配置java环境变量</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">vi /etc/profile</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
将下列复制到profile的最后一行中</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">export JAVA_HOME=/usr/java/jdk17</span></div><div class="line"><span class="text plain null-grammar">export PATH=$PATH:$JAVA_HOME/bin</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
让环境变量生效</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">source /etc/profile</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
测试java的环境变量是否配置好了</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">[root@localhost pp_res]# java -version</span></div><div class="line"><span class="text plain null-grammar">java version "1.7.0_79"</span></div><div class="line"><span class="text plain null-grammar">Java(TM) SE Runtime Environment (build 1.7.0_79-b15)</span></div><div class="line"><span class="text plain null-grammar">Java HotSpot(TM) 64-Bit Server VM (build 24.79-b02, mixed mode)</span></div>
<h1 id="2-hbase" style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h1>
<a name="yy02" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h1 style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
2. 安装Hbase</h1>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
pinpoint收集来的测试数据，主要是存在Hbase数据库的。所以它可以收集大量的数据，可以进行更加详细的分析。</p>
<a name="yy0201" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 id="2-1-hbase-" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
2.1 将Hbase解压，并且放入指定目录</h2>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /home/pp_res/</span></div><div class="line"><span class="text plain null-grammar">tar -zxvf hbase-1.0.3-bin.tar.gz</span></div><div class="line"><span class="text plain null-grammar">mkdir -p /data/service</span></div><div class="line"><span class="text plain null-grammar">mv hbase-1.0.3/ /data/service/hbase</span></div>
<h2 id="2-2-hbase-env-sh-java_home-" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<a name="yy0202" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
2.2 修改hbase-env.sh的JAVA_HOME环境变量位置</h2>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /data/service/hbase/conf/</span></div><div class="line"><span class="text plain null-grammar">vi hbase-env.sh</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
在27行左右的位置，修改如下</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">export JAVA_HOME=/usr/java/jdk17/</span></div>
<a name="yy0203" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 id="2-3-hbase-" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
2.3 修改Hbase的配置信息</h2>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">vi hbase-site.xml</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
在结尾修改成如下，这里我们指定Hbase本地来存储数据，生产环境将数据建议存入HDFS中。</p>
<pre class="editor-colors lang-xml" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text xml"><span class="meta tag xml"><span class="punctuation definition tag xml">&lt;</span><span class="entity name tag localname xml" style="color:rgb(224,108,117);">configuration</span><span class="punctuation definition tag xml">&gt;</span></span></span></div><div class="line"><span class="text xml">  <span class="meta tag xml"><span class="punctuation definition tag xml">&lt;</span><span class="entity name tag localname xml" style="color:rgb(224,108,117);">property</span><span class="punctuation definition tag xml">&gt;</span></span></span></div><div class="line"><span class="text xml">    <span class="meta tag xml"><span class="punctuation definition tag xml">&lt;</span><span class="entity name tag localname xml" style="color:rgb(224,108,117);">name</span><span class="punctuation definition tag xml">&gt;</span></span>hbase.rootdir<span class="meta tag xml"><span class="punctuation definition tag xml">&lt;/</span><span class="entity name tag localname xml" style="color:rgb(224,108,117);">name</span><span class="punctuation definition tag xml">&gt;</span></span></span></div><div class="line"><span class="text xml">    <span class="meta tag xml"><span class="punctuation definition tag xml">&lt;</span><span class="entity name tag localname xml" style="color:rgb(224,108,117);">value</span><span class="punctuation definition tag xml">&gt;</span></span><span class="markup underline link file hyperlink" style="text-decoration:underline;color:rgb(198,120,221);">file:///data/hbase</span><span class="meta tag xml"><span class="punctuation definition tag xml">&lt;/</span><span class="entity name tag localname xml" style="color:rgb(224,108,117);">value</span><span class="punctuation definition tag xml">&gt;</span></span></span></div><div class="line"><span class="text xml"> <span class="meta tag xml"><span class="punctuation definition tag xml">&lt;/</span><span class="entity name tag localname xml" style="color:rgb(224,108,117);">property</span><span class="punctuation definition tag xml">&gt;</span></span></span></div><div class="line"><span class="text xml"><span class="meta tag xml"><span class="punctuation definition tag xml">&lt;/</span><span class="entity name tag localname xml" style="color:rgb(224,108,117);">configuration</span><span class="punctuation definition tag xml">&gt;</span></span></span></div>
<h2 id="2-4-hbase" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<a name="yy0204" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
2.4 启动hbase</h2>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /data/service/hbase/bin</span></div><div class="line"><span class="text plain null-grammar">./start-hbase.sh</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
查看Hbase是否启动成功，如果启动成功的会看到"HMaster"的进程</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">[root@localhost bin]# jps</span></div><div class="line"><span class="text plain null-grammar">12075 Jps</span></div><div class="line"><span class="text plain null-grammar">11784 HMaster</span></div>
<h2 id="2-5-hbase-pinpoint-" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<a name="yy0205" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
2.5 初始化Hbase的pinpoint库</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
执行pinpoint提供的Hbase初始化语句，这时会初始化一会。</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">./hbase shell /home/pp_res/hbase-create.hbase</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
执行完了以后，进入Hbase</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">./hbase shell</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
进入后可以看到Hbase的版本，还有一些相关的信息</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">2016-11-15 01:55:44,861 WARN  [main] util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using built</span></div><div class="line"><span class="text plain null-grammar">in-java classes where applicableHBase Shell; enter 'help&lt;RETURN&gt;' for list of supported commands.</span></div><div class="line"><span class="text plain null-grammar">Type "exit&lt;RETURN&gt;" to leave the HBase Shell</span></div><div class="line"><span class="text plain null-grammar">Version 1.0.3, rf1e1312f9790a7c40f6a4b5a1bab2ea1dd559890, Tue Jan 19 19:26:53 PST 2016</span></div><div class="line"><span class="text plain null-grammar"> </span></div><div class="line"><span class="text plain null-grammar">hbase(main):001:0&gt;</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
输入"status 'detailed'"可以查看刚才初始化的表，是否存在</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">hbase(main):001:0&gt; status 'detailed'</span></div><div class="line"><span class="text plain null-grammar">version 1.0.3</span></div><div class="line"><span class="text plain null-grammar">0 regionsInTransition</span></div><div class="line"><span class="text plain null-grammar">master coprocessors: []</span></div><div class="line"><span class="text plain null-grammar">1 live servers</span></div><div class="line"><span class="text plain null-grammar">    localhost:50887 1478538574709</span></div><div class="line"><span class="text plain null-grammar">        requestsPerSecond=0.0, numberOfOnlineRegions=498, usedHeapMB=24, maxHeapMB=237, numberOfStores=626, numberOfStorefiles=0, storefileUncom</span></div><div class="line"><span class="text plain null-grammar">pressedSizeMB=0, storefileSizeMB=0, memstoreSizeMB=0, storefileIndexSizeMB=0, readRequestsCount=7714, writeRequestsCount=996, rootIndexSizeKB=0, totalStaticIndexSizeKB=0, totalStaticBloomSizeKB=0, totalCompactingKVs=0, currentCompactedKVs=0, compactionProgressPct=NaN, coprocessors=[MultiRowMutationEndpoint]        "AgentEvent,,1478539104778.aa1b3b14d0b48d83cbf4705b75cb35b7."</span></div><div class="line"><span class="text plain null-grammar">            numberOfStores=1, numberOfStorefiles=0, storefileUncompressedSizeMB=0, storefileSizeMB=0, memstoreSizeMB=0, storefileIndexSizeMB=0,</span></div><div class="line"><span class="text plain null-grammar">readRequestsCount=0, writeRequestsCount=0, rootIndexSizeKB=0, totalStaticIndexSizeKB=0, totalStaticBloomSizeKB=0, totalCompactingKVs=0, currentCompactedKVs=0, compactionProgressPct=NaN, completeSequenceId=-1, dataLocality=0.0</span></div><div class="line"><span class="text plain null-grammar">...</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
也可以登录web，来查看HBase的数据是否初始化成功</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
HbaseWeb : <a href="http://192.168.245.134:16010/master-status" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);">http://192.168.245.134:16010/master-status</a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127144710487-229643827.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="HbaseWeb" border="0" alt="HbaseWeb" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127144710971-1455199420.png" width="1230" height="977" style="border:0px none;display:inline;"></a></p>
<a name="yy03" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h1 id="3-pinpoint-collector" style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h1>
<h1 style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
3. 安装pinpoint-collector</h1>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<a name="yy0301" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 id="3-1-war-" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
3.1 部署war包</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
解压Tomcat，将Tomcat重命名移动到指定位置</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /home/pp_res/</span></div><div class="line"><span class="text plain null-grammar">tar -zxvf apache-tomcat-8.0.36.tar.gz</span></div><div class="line"><span class="text plain null-grammar">mv apache-tomcat-8.0.36/ /data/service/pp-col</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
修改pp-col的Tomcat的配置，主要修改端口，避免与pp-web的Tomcat的端口冲突。我在原本默认的端口前都加了1，下面是替换的shell命令。</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
【注意】最后一条是将tomcat的私有ip开放，需要将localhost替换成本机的ip，我本机的网卡是默认的，如果你本机的网卡不是eth0，需要进行相关的修改。或者直接用"vi"进去，修改localhost</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /data/service/pp-col/conf/</span></div><div class="line"><span class="text plain null-grammar">sed -i 's/port="8005"/port="18005"/g' server.xml</span></div><div class="line"><span class="text plain null-grammar">sed -i 's/port="8080"/port="18080"/g' server.xml</span></div><div class="line"><span class="text plain null-grammar">sed -i 's/port="8443"/port="18443"/g' server.xml</span></div><div class="line"><span class="text plain null-grammar">sed -i 's/port="8009"/port="18009"/g' server.xml</span></div><div class="line"><span class="text plain null-grammar">sed -i 's/redirectPort="8443"/redirectPort="18443"/g' server.xml</span></div><div class="line"><span class="text plain null-grammar">sed -i "s/localhost/`ifconfig eth0 | grep 'inet addr' | awk '{print $2}' | awk -F: '{print $2}'`/g" server.xml</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
部署pinpoint-collector.war包</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
【注意：如果没有unzip命令，可以 "yum install unzip" 】</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /home/pp_res/</span></div><div class="line"><span class="text plain null-grammar">rm -rf /data/service/pp-col/webapps/*</span></div><div class="line"><span class="text plain null-grammar">unzip pinpoint-collector-1.5.2.war -d /data/service/pp-col/webapps/ROOT</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
启动Tomcat</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /data/service/pp-col/bin/</span></div><div class="line"><span class="text plain null-grammar">./startup.sh</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
查看日志，是否成功启动</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">tail -f ../logs/catalina.out</span></div>
<a name="yy0302" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 id="3-2-" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
3.2 配置快速启动</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
配置快速启动需要修改pp-collector.init的路径( pp-collector在网盘里面有 )，可以"vi"进去，大概在18，24，27行处，修改相关的路径。我这边为了方便，直接就用替换的shell做了，如果路径与我的不一致，需要将路径修改成自己的路径。</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /home/pp_res</span></div><div class="line"><span class="text plain null-grammar">sed -i "s/JAVA_HOME=\/usr\/java\/default\//JAVA_HOME=\/usr\/java\/jdk17\//g" pp-collector.init</span></div><div class="line"><span class="text plain null-grammar">sed -i "s/CATALINA_HOME=\/data\/service\/pinpoint-collector\//CATALINA_HOME=\/data\/service\/pp-col\//g" pp-collector.init</span></div><div class="line"><span class="text plain null-grammar">sed -i "s/CATALINA_BASE=\/data\/service\/pinpoint-collector\//CATALINA_BASE=\/data\/service\/pp-col\//g" pp-collector.init</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
将文件赋予"执行"的权限，把它放到"init.d"中去。以后就可以restart快速重启了。</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">chmod 711 pp-collector.init</span></div><div class="line"><span class="text plain null-grammar">mv pp-collector.init /etc/init.d/pp-col</span></div><div class="line"><span class="text plain null-grammar"> </span></div><div class="line"><span class="text plain null-grammar"> </span></div><div class="line"><span class="text plain null-grammar"># 测试一下restart</span></div><div class="line"><span class="text plain null-grammar">[root@localhost pp_res]# /etc/init.d/pp-col restart</span></div><div class="line"><span class="text plain null-grammar">Stoping Tomcat</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_BASE:   /data/service/pp-col/</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_HOME:   /data/service/pp-col/</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_TMPDIR: /data/service/pp-col//temp</span></div><div class="line"><span class="text plain null-grammar">Using JRE_HOME:        /usr/java/jdk17/</span></div><div class="line"><span class="text plain null-grammar">Using CLASSPATH:       /data/service/pp-col//bin/bootstrap.jar:/data/service/pp-col//bin/tomcat-juli.jar</span></div><div class="line"><span class="text plain null-grammar"> </span></div><div class="line"><span class="text plain null-grammar">waiting for processes to exitStarting tomcat</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_BASE:   /data/service/pp-col/</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_HOME:   /data/service/pp-col/</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_TMPDIR: /data/service/pp-col//temp</span></div><div class="line"><span class="text plain null-grammar">Using JRE_HOME:        /usr/java/jdk17/</span></div><div class="line"><span class="text plain null-grammar">Using CLASSPATH:       /data/service/pp-col//bin/bootstrap.jar:/data/service/pp-col//bin/tomcat-juli.jar</span></div><div class="line"><span class="text plain null-grammar">Tomcat started.</span></div><div class="line"><span class="text plain null-grammar">Tomcat is running with pid: 22824</span></div><div class="line"><span class="text plain null-grammar"></span></div>
<a name="yy04" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h1 id="4-pinpoint-web" style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h1>
<h1 style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
4. 安装pinpoint-web</h1>
<a name="yy0401" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 id="4-1-war-" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
4.1 部署war包</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
解压Tomcat，将Tomcat重命名移动到指定位置</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /home/pp_res/</span></div><div class="line"><span class="text plain null-grammar">tar -zxvf apache-tomcat-8.0.36.tar.gz</span></div><div class="line"><span class="text plain null-grammar">mv apache-tomcat-8.0.36/ /data/service/pp-web</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
修改pp-web的Tomcat的配置，主要修改端口，避免与pp-col的Tomcat的端口冲突。我在原本默认的端口前都加了2，下面是替换的shell命令</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
【注意】最后一条是将tomcat的私有ip开放，需要将localhost替换成本机的ip，我本机的网卡是默认的，如果你本机的网卡不是eth0，需要进行相关的修改。或者直接用"vi"进去，修改localhost</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /data/service/pp-web/conf/</span></div><div class="line"><span class="text plain null-grammar">sed -i 's/port="8005"/port="28005"/g' server.xml</span></div><div class="line"><span class="text plain null-grammar">sed -i 's/port="8080"/port="28080"/g' server.xml</span></div><div class="line"><span class="text plain null-grammar">sed -i 's/port="8443"/port="28443"/g' server.xml</span></div><div class="line"><span class="text plain null-grammar">sed -i 's/port="8009"/port="28009"/g' server.xml</span></div><div class="line"><span class="text plain null-grammar">sed -i 's/redirectPort="8443"/redirectPort="28443"/g' server.xml</span></div><div class="line"><span class="text plain null-grammar">sed -i "s/localhost/`ifconfig eth0 | grep 'inet addr' | awk '{print $2}' | awk -F: '{print $2}'`/g" server.xml</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
部署pinpoint-collector.war包</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
【注意：如果没有unzip命令，可以 "yum install unzip" 】</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /home/pp_res/</span></div><div class="line"><span class="text plain null-grammar">rm -rf /data/service/pp-web/webapps/*</span></div><div class="line"><span class="text plain null-grammar">unzip pinpoint-web-1.5.2.war -d /data/service/pp-web/webapps/ROOT</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
查看war包是否解压成功</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">[root@localhost conf]# ll /data/service/pp-web/webapps/ROOT/WEB-INF/classes/</span></div><div class="line"><span class="text plain null-grammar">total 88</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root 2164 Apr  7  2016 applicationContext-cache.xml</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root 3649 Apr  7  2016 applicationContext-dao-config.xml</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root 1490 Apr  7  2016 applicationContext-datasource.xml</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root 6680 Apr  7  2016 applicationContext-hbase.xml</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root 1610 Apr  7  2016 applicationContext-websocket.xml</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root 6576 Apr  7  2016 applicationContext-web.xml</span></div><div class="line"><span class="text plain null-grammar">drwxrwxr-x. 2 root root 4096 Apr  7  2016 batch</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root  106 Apr  7  2016 batch.properties</span></div><div class="line"><span class="text plain null-grammar">drwxrwxr-x. 3 root root 4096 Apr  7  2016 com</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root  682 Apr  7  2016 ehcache.xml</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root 1001 Apr  7  2016 hbase.properties</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root  153 Apr  7  2016 jdbc.properties</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root 3338 Apr  7  2016 log4j.xml</span></div><div class="line"><span class="text plain null-grammar">drwxrwxr-x. 2 root root 4096 Apr  7  2016 mapper</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root 1420 Apr  7  2016 mybatis-config.xml</span></div><div class="line"><span class="text plain null-grammar">drwxrwxr-x. 3 root root 4096 Apr  7  2016 org</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root  630 Apr  7  2016 pinpoint-web.properties</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root  141 Apr  7  2016 project.properties</span></div><div class="line"><span class="text plain null-grammar">-rw-rw-r--. 1 root root 3872 Apr  7  2016 servlet-context.xml</span></div><div class="line"><span class="text plain null-grammar">drwxrwxr-x. 2 root root 4096 Apr  7  2016 sql</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
这里说明一下：</p>
<ul style="list-style:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"><li style="list-style:disc inside;">hbase.properties 配置我们pp-web从哪个数据源获取采集数据，这里我们只指定Hbase的zookeeper地址。</li><li style="list-style:disc inside;">jdbc.properties pp-web连接自身Mysql数据库的连接认证配置。</li><li style="list-style:disc inside;">sql目录 pp-web本身有些数据需要存放在MySQL数据库中，这里需要初始化一下表结构。</li><li style="list-style:disc inside;">pinpoint-web.properties 这里pp-web集群的配置文件，如果你需要pp-web集群的话。</li><li style="list-style:disc inside;">applicationContext-* .xml 这些文件在后续的调优工作中会用到。</li><li style="list-style:disc inside;">log4j.xml 日志相关配置。</li></ul><p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
启动Tomcat</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /data/service/pp-web/bin/</span></div><div class="line"><span class="text plain null-grammar">./startup.sh</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
查看日志，Tocmat是否启动成功</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">tail -f ../logs/catalina.out</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
日志中出现下面这句话，说明已经启动成功了</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">org.apache.catalina.startup.Catalina.start Server startup in 79531 ms</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
这时候我们可以访问一下这个地址，在浏览器中输入"<a>http://192.168.245.136:28080"，就会出现主页面了</a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
如果访问不了的话，关闭防火墙</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">[root@localhost conf]# /etc/init.d/iptables stop</span></div><div class="line"><span class="text plain null-grammar">iptables: Setting chains to policy ACCEPT: filter          [  OK  ]</span></div><div class="line"><span class="text plain null-grammar">iptables: Flushing firewall rules:                         [  OK  ]</span></div><div class="line"><span class="text plain null-grammar">iptables: Unloading modules:                               [  OK  ]</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127144711315-1500996901.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="pp-web" border="0" alt="pp-web" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127144711565-108467098.png" width="1353" height="708" style="border:0px none;display:inline;"></a></p>
<a name="yy0402" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 id="4-2-" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
4.2 配置快速启动</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
需要修改"pp-web.init"，与上面的步骤一致</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /home/pp_res</span></div><div class="line"><span class="text plain null-grammar">sed -i "s/JAVA_HOME=\/usr\/java\/default\//JAVA_HOME=\/usr\/java\/jdk17\//g" pp-web.init</span></div><div class="line"><span class="text plain null-grammar">sed -i "s/CATALINA_HOME=\/data\/service\/pinpoint-web\//CATALINA_HOME=\/data\/service\/pp-web\//g" pp-web.init</span></div><div class="line"><span class="text plain null-grammar">sed -i "s/CATALINA_BASE=\/data\/service\/pinpoint-web\//CATALINA_BASE=\/data\/service\/pp-web\//g" pp-web.init</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
将文件赋予"执行"的权限，把让放到"init.d"中去。以后就可以restart快速重启了。</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">chmod 711 pp-web.init</span></div><div class="line"><span class="text plain null-grammar">mv pp-web.init /etc/init.d/pp-web</span></div><div class="line"><span class="text plain null-grammar"> </span></div><div class="line"><span class="text plain null-grammar"> </span></div><div class="line"><span class="text plain null-grammar"># 测试一下restart</span></div><div class="line"><span class="text plain null-grammar">[root@localhost pp_res]# /etc/init.d/pp-web restart</span></div><div class="line"><span class="text plain null-grammar">Stoping Tomcat</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_BASE:   /data/service/pp-web/</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_HOME:   /data/service/pp-web/</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_TMPDIR: /data/service/pp-web//temp</span></div><div class="line"><span class="text plain null-grammar">Using JRE_HOME:        /usr/java/jdk17/</span></div><div class="line"><span class="text plain null-grammar">Using CLASSPATH:       /data/service/pp-web//bin/bootstrap.jar:/data/service/pp-web//bin/tomcat-juli.jar</span></div><div class="line"><span class="text plain null-grammar"> </span></div><div class="line"><span class="text plain null-grammar">waiting for processes to exitStarting tomcat</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_BASE:   /data/service/pp-web/</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_HOME:   /data/service/pp-web/</span></div><div class="line"><span class="text plain null-grammar">Using CATALINA_TMPDIR: /data/service/pp-web//temp</span></div><div class="line"><span class="text plain null-grammar">Using JRE_HOME:        /usr/java/jdk17/</span></div><div class="line"><span class="text plain null-grammar">Using CLASSPATH:       /data/service/pp-web//bin/bootstrap.jar:/data/service/pp-web//bin/tomcat-juli.jar</span></div><div class="line"><span class="text plain null-grammar">Tomcat started.</span></div><div class="line"><span class="text plain null-grammar">Tomcat is running with pid: 22703</span></div>
<a name="yy05" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h1 style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h1>
<h1 style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
5. 部署pp-agent采集监控数据</h1>
<a name="yy0501" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h1 id="5-pp-agent-" style="list-style-type:none;font-size:28px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h1>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
5.1 在测试系统中，部署pp-agent采集监控数据</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
部署采集器就很简单了，只需要加3句话就好了。我这边做一个测试的Tomcat，来模拟部署。</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
首先，先建立一个文件夹，放测试需要的包</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">mkdir /home/pp_test</span></div><div class="line"><span class="text plain null-grammar">cd /home/test</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
将测试需要的pp-agent拉到服务器上</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127144711846-669011609.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="pp-test" border="0" alt="pp-test" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127144712393-1983628158.png" width="943" height="769" style="border:0px none;display:inline;"></a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
查看包是否上传成功</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">[root@localhost pp_test]# ll</span></div><div class="line"><span class="text plain null-grammar">total 16820</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root 9277365 Nov  9 02:25 apache-tomcat-8.0.36.tar.gz</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root 6621915 Nov  9 02:25 pinpoint-agent-1.5.2.tar.gz</span></div><div class="line"><span class="text plain null-grammar">-rw-r--r--. 1 root root 1320206 Nov  9 02:25 test.war</span></div>
<a name="yy0502" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 id="5-1-tomcat-" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
5.2 配置模拟的Tomcat测试环境</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
为了方便观察，配置一个假的系统，解压Tomcat到指定目录</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /home/pp_test</span></div><div class="line"><span class="text plain null-grammar">mkdir /data</span></div><div class="line"><span class="text plain null-grammar">tar -zxvf apache-tomcat-8.0.36.tar.gz</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
配置localhost让外部可以访问</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /data/pp-test/conf/</span></div><div class="line"><span class="text plain null-grammar">sed -i "s/localhost/`ifconfig eth0 | grep 'inet addr' | awk '{print $2}' | awk -F: '{print $2}'`/g" server.xml</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
解压测试用的war包</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /home/pp_test/</span></div><div class="line"><span class="text plain null-grammar">rm -rf /data/pp-test/webapps/*</span></div><div class="line"><span class="text plain null-grammar">unzip test.war -d /data/pp-test/webapps/ROOT</span></div>
<a name="yy0503" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 id="5-2-pp-agent-" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
5.3 配置pp-agent采集器</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
解压pp-agent</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /home/pp_test</span></div><div class="line"><span class="text plain null-grammar">tar -zxvf pinpoint-agent-1.5.2.tar.gz</span></div><div class="line"><span class="text plain null-grammar">mv pinpoint-agent-1.5.2 /data/pp-agent</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
编辑配置文件</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /data/pp-agent/</span></div><div class="line"><span class="text plain null-grammar">vi pinpoint.config</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
主要修改IP，只需要指定到安装pp-col的IP就行了，安装pp-col启动后，自动就开启了9994，9995，9996的端口了。这里就不需要操心了，如果有端口需求，要去pp-col的配置文件("pp-col/webapps/ROOT/WEB-INF/classes/pinpoint-collector.properties")中，修改这些端口</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">profiler.collector.ip=192.168.245.136</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
修改测试项目下的tomcat启动文件"catalina.sh"，修改这个只要是为了监控测试环境的Tomcat，增加探针</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /data/pp-test/bin</span></div><div class="line"><span class="text plain null-grammar">vi catalina.sh</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
在20行增加如下字段</p>
<ol style="list-style:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"><li style="list-style-type:decimal;">第一行是pp-agent的jar包位置</li><li style="list-style-type:decimal;">第二行是agent的ID，这个ID是唯一的，我是用pp + 今天的日期命名的，只要与其他的项目的ID不重复就好了</li><li style="list-style-type:decimal;">第三行是采集项目的名字，这个名字可以随便取，只要各个项目不重复就好了</li></ol><pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">CATALINA_OPTS="$CATALINA_OPTS -javaagent:/data/pp-agent/pinpoint-bootstrap-1.5.2.jar"</span></div><div class="line"><span class="text plain null-grammar">CATALINA_OPTS="$CATALINA_OPTS -Dpinpoint.agentId=pp20161122"</span></div><div class="line"><span class="text plain null-grammar">CATALINA_OPTS="$CATALINA_OPTS -Dpinpoint.applicationName=MyTestPP</span></div>
<a name="yy0504" style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></a><span style="color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"></span>
<h2 id="5-3-tomcat" style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
5.4 监控Tomcat</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
配置好了。就可以开始监控了，我们启动测试用的Tomcat的服务器</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">cd /data/pp-test/bin/</span></div><div class="line"><span class="text plain null-grammar">./startup.sh</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
查看启动日志，确实Tomcat启动</p>
<pre class="editor-colors lang-linux" style="list-style-type:none;border:1px solid rgb(204,204,204);background:rgb(40,44,52);font-family:'Courier New', Courier, monospace;color:rgb(171,178,191);font-size:14px;"></pre><div class="line"><span class="text plain null-grammar">tail -f ../logs/catalina.out</span></div>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
启动了，我们就可以访问测试环境了</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127144712971-302014446.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="test" border="0" alt="test" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127144713284-1200738898.png" width="477" height="234" style="border:0px none;display:inline;"></a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127144713643-1533237063.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="test1" border="0" alt="test1" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127144714018-556631195.png" width="524" height="457" style="border:0px none;display:inline;"></a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
这时候我们在访问pp-web，可以发现它的下拉框中，多了一个app</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127144714456-1039292679.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="pp-testApp" border="0" alt="pp-testApp" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127144714893-1908781547.png" width="1006" height="474" style="border:0px none;display:inline;"></a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127144715425-1311072141.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="pp-testView" border="0" alt="pp-testView" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127144716362-1138847963.png" width="1339" height="670" style="border:0px none;display:inline;"></a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
因为我访问了两次，所以他显示有两条请求记录，可以在右上角的框查看详情。</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
【注意】鼠标点击右上角箭头位置，鼠标左键按住不动，拉框查看。我被这个坑，坑懵逼了，特此写清楚。</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127144716690-1717832338.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="pp-detail" border="0" alt="pp-detail" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127144717003-417295567.png" width="1350" height="669" style="border:0px none;display:inline;"></a></p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
 </p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
这时候就弹出了新页面，可以看到，我访问了一次主页，访问了一次test的servlet。而且详细信息都记录在下表中。</p>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
<a href="http://images2015.cnblogs.com/blog/626593/201611/626593-20161127144717315-226577854.png" rel="nofollow" style="text-decoration:none;color:rgb(255,115,0);"><img title="pp-code" border="0" alt="pp-code" src="https://images2015.cnblogs.com/blog/626593/201611/626593-20161127144718159-1266771902.png" width="1424" height="672" style="border:0px none;display:inline;"></a></p>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
 </h2>
<h2 style="list-style-type:none;font-size:21px;line-height:1.5;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;">
总结</h2>
<p style="list-style-type:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;">
到这里，整个部署过程就完了。值得要注意的地方：</p>
<ol style="list-style:none;color:rgb(68,68,68);font-family:Tahoma, Arial, '微软雅黑', sans-serif;font-size:14px;"><li style="list-style-type:decimal;">如果Hbase不是与pp-web, pp-col装在一台机器上，需要安装zookeeper，只要安装就好，确实2181端口启动就好。</li><li style="list-style-type:decimal;">如果zookeeper安装在独立机器上，这里需要修改一下pp-colletor 和 pp-web的配置文件pinpoint-collector.properties，pinpoint-web.properties，不然会导致俩个模块启动失败。</li><li style="list-style-type:decimal;">发现pinpoint还是有些缺陷，异步的操作监控不到，比如我写了个多线程来发送HttpClient4的请求，但是pinpoint监控不到。但是它介绍又说可以监控到Httpclient4的请求。现在都是分布式系统，异步拿数据再常见不过来，如果监控不到异步的操作，就很鸡肋了。看pp1.6会不会修复这个问题</li><li style="list-style-type:decimal;">在pp1.6部署，Hbase中的默认字段有增加，如果没有加上默认字段，取得的数据就会变得相当少了。</li></ol><br></div>
</blockquote>
            </div>
                </div>