---
layout:     post
title:      spark 之 Phoenix详解
---
<div id="article_content" class="article_content clearfix csdn-tracking-statistics" data-pid="blog" data-mod="popu_307" data-dsm="post">
								            <link rel="stylesheet" href="https://csdnimg.cn/release/phoenix/template/css/ck_htmledit_views-f76675cdea.css">
						<div class="htmledit_views" id="content_views">
                
<p>转自：http://www.cnblogs.com/laov/p/4137136.html</p>
<p></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">HBase，一个NoSQL数据库，可存储大量非关系型数据。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">HBase，可以用HBase shell进行操作，也可以用HBase Java api进行操作。HBase虽然是一个数据库，但是它的查询语句，很不太好用。要是能像使用Mysql等关系型数据库一样用sql语句操作HBase，那就很Perfect了。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span><span style="font-family:'Microsoft YaHei';">现有工具有很多Hive，Tez，Impala，Shark/Spark，Phoenix等。今天主要记录Phoenix。</span></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">phoenix，由saleforce.com开源的一个项目，后又捐给了Apache。它<span>相当于一个Java中间件，帮助开发者，像使用jdbc访问关系型数据库一些，访问NoSql数据库HBase。</span></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><img class="wp-more-tag mce-wp-more" title="阅读更多…" src="" alt="" style="border:0px;"></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">phoenix，操作的表及数据，存储在hbase上。phoenix只是需要和Hbase进行表关联起来。然后再用工具进行一些读或写操作。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">其实，<span>可以把Phoenix只看成一种代替HBase的语法的一个工具。虽然可以用java可以用jdbc来连接phoenix，然后操作HBase，但是在生产环境中，不可以用在OLTP中。</span>在线事务处理的环境中，需要低延迟，而Phoenix在查询HBase时，虽然做了一些优化，但延迟还是不小。所以依然是用在OLAT中，再将结果返回存储下来。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"> </span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><a href="http://phoenix.apache.org/" rel="nofollow" style="color:#000000;">Phoenix官网</a>上，对Phoenix讲解已经很屌了。如果英语好，可以看官网，更正式一些。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"> </span></p>
<h5 style="font-size:12px;color:rgb(51,51,51);font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Phoenix安装</span></h5>
<h6 style="font-size:11px;font-family:Verdana, Arial, Helvetica, sans-serif;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">1、<a href="http://phoenix.apache.org/download.html" rel="nofollow" style="color:#000000;">下载phoenix</a>。</span></h6>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">phoenix与HBase版本对应关系</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Phoenix 2.x - HBase 0.94.x</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Phoenix 3.x - HBase 0.94.x</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Phoenix 4.x - HBase 0.98.1+</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">我目前测试使用版本概况：</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Hadoop1.0.4</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">HBase0.94.18</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">所以我可以用phoenix2.x，phoenix3.x。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">官网download页面有</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><a href="http://www.weixuehao.com/wp-content/uploads/2014/11/image.png" rel="nofollow" style="color:#000000;"></a></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">我选用的是phoenix3.1.0版本。</span></p>
<h6 style="font-size:11px;font-family:Verdana, Arial, Helvetica, sans-serif;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">2、上传到主节点linux就ok了，解压缩</span></h6>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">tar –zxvf phoenix.tar.gz</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">pwd</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">/root/phoenix</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">ll phoenix</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><a href="http://www.weixuehao.com/wp-content/uploads/2014/11/image1.png" rel="nofollow" style="color:#000000;"></a></span>  </p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">phoenix目录结构可能会有点不同，主要是bin目录的位置，可能在hadoop1下，也可能直接在 /root/phoenix下。没关系，都差不多。</span></p>
<h6 style="font-size:11px;font-family:Verdana, Arial, Helvetica, sans-serif;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">3、拷贝一些文件</span></h6>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">既然用的hadoop1.x集群，那么我们使用phoenix目录下，hadoop1目录下的内容。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">①将hadoop1下，phoenix-core-3.x.jar拷贝到hadoop集群各个节点HBase的lib目录下。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">②重启一下HBase</span></p>
<h6 style="font-size:11px;font-family:Verdana, Arial, Helvetica, sans-serif;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">4、验证是否安成功</span></h6>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">在主节点上，切换到/root/phoenix/hadoop1/bin目录下</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">输入 ./sqlline.py master:2181</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><a href="http://www.weixuehao.com/wp-content/uploads/2014/11/image2.png" rel="nofollow" style="color:#000000;"></a></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">如果出现这个画面，那就是成功了。如果不成功，可能是zookeeper配置的有一些问题吧。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">好吧，先退出此界面，输入!quit回车然后就可以退出了。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">这个phoenix挺有意思，有一些命令需要输入叹号的！</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"> </span></p>
<h5 style="font-size:12px;color:rgb(51,51,51);font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">phoenix的使用</span></h5>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">mysql的话，可以CLI命令行的方式操作；可以通过用jdbc，在Java代码中访问；可以通过用SQLyog进行访问管理；</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">phoenix，怎么用呢？~可以看成是mysql。Phoenix可以在CLI下操作；可以用jdbc操作；可以用phoenix的一个客户端工具Squirrel 访问；</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">先说Squirrel吧，这个简单一些。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><a href="http://www.squirrelsql.org/" rel="nofollow" style="color:#000000;">Squirrel SQL Client</a>，是一个连接数据库的客户端工具。一般支持JDBC的数据库都可以用它来连接。（如Squirrel连接Mysql）</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">下载Squirrel SQL Client，解压缩就可以了。运行squirrel-sql.bat就出现了图形界面。</span></p>
<h6 style="font-size:11px;font-family:Verdana, Arial, Helvetica, sans-serif;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">这肯定要说怎样连Phoenix？</span></h6>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">①在Squirrel安装目录的lib下，添加几个jar包</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">a,phoenix-core-xxx.jar</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">b,phoenix-3.0-client.jar</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">c,hbase-0.94.18.jar</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">d,hadoop1.0.4.jar</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">e,hadoop-common-xxx.jar</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">②</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><img class="alignnone" src="https://img-blog.csdn.net/20140905150155281?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQva3V5dXlpbmd6aQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" width="965" height="596" style="border:0px;"></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">需要点击“Drivers”，将phoenix的驱动添加进去。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">③点击左上角 蓝色的 “ + ” 加号，添加</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><a href="http://www.weixuehao.com/wp-content/uploads/2014/11/image3.png" rel="nofollow" style="color:#000000;"></a></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">按上面的顺序，依次填写。第一步Name：随便写个名字，标记连接；第二步Example URL：相当于mysql的jdbc连接串，这里的alias写zookeeper的主机名称，端口号，可以写，可以不写，我一般不写；第三步选择Phoenix-core的jar包；第四步就是手动输入org.apache.phoenix.jdbc.PhoenixDriver。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">然后点击OK。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">④配置连接</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><a href="http://www.weixuehao.com/wp-content/uploads/2014/11/image4.png" rel="nofollow" style="color:#000000;"></a></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Name：为随便起的名称。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Driver：选中③中添加的phoenix驱动。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">URL：写如上内容，jdbc:phoenix:node1,node2,master等这里主要是zookeeper主机名。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">User Name：要连接的主机的用户名</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Password：要连接的主机的密码</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">点击Test可以进行测试，或点OK连接。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">连接完毕，启动后，就可以看到如下的效果了。这里我已经创建了几个表了，这些表都是存在于HBase上的。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><a href="http://www.weixuehao.com/wp-content/uploads/2014/11/image_thumb5.png" rel="nofollow" style="color:#000000;"></a></span></p>
<h6 style="font-size:11px;font-family:Verdana, Arial, Helvetica, sans-serif;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Squirrel的一些布局简介：</span></h6>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">1，用squirrel建立的一些连接</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">2，当前连接下，所有对象，包括主见系统表，普通表，视图。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">3，为表，这些表都是实际存在于zookeeper所管理的HBase上的。右键此表，可以对表进行管理。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">4，为视图。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">5，编写sql脚本的地方，可以输入脚本执行。脚本执行方式，在5上面有一个小人，选中sql，点击小人就可以执行了。或者按ctrl + enter键，执行。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">6，为选中的对象的一些基本信息，列信息，行数等。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">7，为sql执行的一些状态。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">下面在Squirrel中创建一个表</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">在Squirrel中创建表的过程主要是编写sql，进行执行。sql该怎么写，需要看phoenix驱动都支持什么效果。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">这需要看phoenix的官网了。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">需要注意的是phoenix是区分大小写的，自己定义的HBase中的 HTableName，ColumnFamily，以及字段Column，需要和Phoenix中保持一致。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">phoenix操作hbase，我们有两种方式，创建表，创建视图。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">这两种方式，有区别。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">比如，创建表的话，就可以对HBase进行插入，查询，删除操作。视图的话，一般就只可以进行查询操作</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">虽然看起来，表的功能，比视图更强大一些。但是就像是mysql等关系型数据库一样，删除表操作，会将表删掉。但是删除视图操作，却不会影响原始表的结构。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">因为使用phoenix，创建表后，会自动和hbase建立关联映射。当你使用phoenix删除和hbase之间的关系时，就会将hbase中的表也删掉了</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">所以用视图，会对原始的HBase表影响小一些。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">phoenix可以创建表，</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">若hbase中，不存在HTable：</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">create htablename (</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">pk VARCHAR primary key not null,</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">col1 VARCHAR null,</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">col2 VARCHAR null,</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">col3 VARCHAR null</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">)</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">create htablename2(</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">pk VARCHAR primary key null,</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">"cf"."col1" VARCHAR null,</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">"cf"."col2" VARCHAR null,</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">"cf2"."col3" VARCHAR null,</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">"cf2"."col4" VARCHAR null,</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">)</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">上面的SQL脚本，可以在SQuirreL中进行执行，执行过程中，如果出现错误，会在工具的下面进行提示。若成功后，就可以在HBase中看到这个表了。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">若Hbase中，已存在名为htablename3的HTable，那么SQuirrel是不会直接显示出hbase中这个已存在的表的，我们还需要额外做一些操作。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">在SQuirreL中进行执行，执行完毕后，就会将HBase的htablename3，映射到SQuirreL中。这样我们就可以在Java api中进行操作了。否则是不可以的。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">那么需要哪些具体操作呢？其实很简单，我当时没想到</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">就像创建表一样，使用Create table就可以了。就这样简单。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">不过这个语句怎么写呢？怎样对应呢？</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">create htablename3(</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">pk VARCHAR primary key null,       -------这句话直接写就可以了，这样的话，HBase中的RowKey转换成phoenix中的主键，列名就叫 pk。rowkey自动会和primary key进行对应。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">"cf"."col1" VARCHAR null,             -------将名为cf的columnFamily下，字段名为col1的字段，写在这里。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">"cf"."col2" VARCHAR null,            -------将名为cf的columnFamily下，字段名为col2的字段，写在这里。。。下面就以此类推</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">"cf2"."col3" VARCHAR null,</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">"cf2"."col4" VARCHAR null,</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">)</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">然后在SQuirreL中执行，然后就可以看到数据了。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">不过此时，可能还会有问题，乱码。 在SQuirrel中，主键以及一些包含汉字的字段，都是方块等乱码了。这个怎么解决？？？</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">创建试图</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">CREATE VIEW "heihei"</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">(pk VARCHAR primary key)</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">default_column_family = 'FM'</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">创建完成后，这里的“heihei” 是HBase中table的名称。然后定义一个主键，就可以了。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">创建视图</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">①CREATE VIEW "DAMAI" ( PK VARCHAR PRIMARY KEY) DEFAULT_COLUMN_FAMILY='FM'</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">这里双引号内的 “DAMAI” 和HBase中的表名是一样的，所以会自动关联。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><a href="http://www.weixuehao.com/wp-content/uploads/2014/11/image6.png" rel="nofollow" style="color:#000000;"></a></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">那么，如果想针对HBase中的一个表，建多个视图呢？</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">②第二种视图，可以在Phoenix table的基础上创建。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">CREATE VIEW my_VIEW (new_col VARCHAR,new_col2 VARCHAR) AS SELECT * FROM phoenix_Table WHERE ......</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">③第三种视图，是建立在视图之上，</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">CREATE VIEW my_VIEW_ON_VIEW AS SELECT * FROM MY_VIEW WHERE ......</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">所以说，在创建DAMAI视图的时候，可以将全部字段都包括进来。然后再在此视图基础上，创建其它视图。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">随着数据的增长，视图中可以看到的数据的条数，也在同步增加。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><a href="http://www.weixuehao.com/wp-content/uploads/2014/11/image7.png" rel="nofollow" style="color:#000000;"></a></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"> </span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">使用命令查看一下视图中的数据</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select * from damai   这时可以用大小写都行了。没有区分</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">查询结果现在，只有一列。看来是创建视图时，没有关联好其他列。没关系，删掉，重建。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"> </span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Phoenix中的<a href="http://phoenix.apache.org/language/index.html" rel="nofollow" style="color:#000000;">语法</a></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Phoenix中的<a href="http://phoenix.apache.org/language/datatypes.html" rel="nofollow" style="color:#000000;">数据类型</a></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">Phoenix中的<a href="http://phoenix.apache.org/language/functions.html" rel="nofollow" style="color:#000000;">方法</a></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">我自己使用过程中一些简单语句，如下：</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select * from shuju;</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select count(1) from shuju;</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select cmtid,count(1) as num from shuju group by cmtid order by num desc;</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select avg(TO_NUMBER(avgt)) from shuju;</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select cmtid,count(1) as num,avg(TO_NUMBER(avgt)) as avgt,avg(TO_NUMBER(loss)) as loss from shuju group by cmtid order by num desc;</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select acm,dtype,cmtid,count(1) as num,avg(TO_NUMBER(avgt)) as avgt,avg(TO_NUMBER(loss)) as loss</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">from shuju</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">group by acm,dtype,cmtid</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">order by num desc;</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select acm,dtype,porgcode,orgid,cmtid,count(1) as num,avg(TO_NUMBER(avgt)) as avgt,avg(TO_NUMBER(loss)) as loss</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">from shuju</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">group by acm,dtype,porgcode,orgid,cmtid</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">order by num desc;</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">where TO_DATE(ttime,'yyyyMMddHHmmss')=TO_DATE('20141125','yyyyMMdd')</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select ttime from shuju order by ttime desc;</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"> </span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">where TO_DATE(ttime,'yyyyMMddHHmmss')=TO_DATE('20141125','yyyyMMdd')</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"> </span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select TO_DATE(ttime,'yyyyMMddHHmmss') from shuju;</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select TO_DATE('20141125','yyyyMMdd') from shuju;</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">select (TO_DATE(ttime,'yyyyMMddHHmmss')=TO_DATE('20141125','yyyyMMdd')) as aaa from shuju order by aaa asc;</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"> </span></p>
<h6 style="font-size:11px;font-family:Verdana, Arial, Helvetica, sans-serif;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">用SHELL命令来操作phoenix</span></h6>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">用SHELL来操作phoenix，不太好用。无助的时候，你可以喊救命！So,Say Help Help Help</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">./sqlline.py master:2181</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">进入shell后，输入help</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">可以看到很多命令，前面都带了一个叹号。根据意思自己猜一猜功能，然后试一试效果，就可以了。不记录了。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"> </span></p>
<h6 style="font-size:11px;font-family:Verdana, Arial, Helvetica, sans-serif;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">用Phoenix Java api操作HBase</span></h6>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">这个过程就想是JDBC一样使用就可以了。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">①先将phoenix的 core.jar包 和 phoenix的client.jar 包放到lib里。</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">②创建连接，过程和mysql类似</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">public Connection GetConnection(){</span><br><span style="font-family:'Microsoft YaHei';">Connection cc = null;</span><br><span style="font-family:'Microsoft YaHei';">String driver = "org.apache.phoenix.jdbc.PhoenixDriver";</span><br><span style="font-family:'Microsoft YaHei';">//String url = "jdbc:phoenix:192.168.206.21:2181";</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">try {</span><br><span style="font-family:'Microsoft YaHei';">Class.forName(driver);</span><br><span style="font-family:'Microsoft YaHei';">} catch (ClassNotFoundException e) {</span><br><span style="font-family:'Microsoft YaHei';">e.printStackTrace();</span><br><span style="font-family:'Microsoft YaHei';">}</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">if (cc == null) {</span><br><span style="font-family:'Microsoft YaHei';">try {</span><br><span style="font-family:'Microsoft YaHei';">cc = DriverManager.getConnection(url);</span><br><span style="font-family:'Microsoft YaHei';">} catch (SQLException e) {</span><br><span style="font-family:'Microsoft YaHei';">e.printStackTrace();</span><br><span style="font-family:'Microsoft YaHei';">}</span><br><span style="font-family:'Microsoft YaHei';">}</span><br><span style="font-family:'Microsoft YaHei';">return cc;</span><br><span style="font-family:'Microsoft YaHei';">}</span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';"><a href="http://www.weixuehao.com/wp-content/uploads/2014/11/QQ%E6%88%AA%E5%9B%BE20141202101221.png" rel="nofollow" style="color:#000000;"></a></span></p>
<p style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:18px;background-color:rgb(204,232,207);">
<span style="font-family:'Microsoft YaHei';">OK 搞定了</span></p>
<br>            </div>
                </div>