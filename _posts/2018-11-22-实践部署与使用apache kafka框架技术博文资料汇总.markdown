---
layout:     post
title:      实践部署与使用apache kafka框架技术博文资料汇总
---
<div id="article_content" class="article_content clearfix csdn-tracking-statistics" data-pid="blog" data-mod="popu_307" data-dsm="post">
								            <link rel="stylesheet" href="https://csdnimg.cn/release/phoenix/template/css/ck_htmledit_views-f76675cdea.css">
						<div class="htmledit_views" id="content_views">
                
<p><span style="font-size:14px">前一篇Kafka框架设计来自英文原文（Kafka Architecture Design）的翻译及整理文章，很有借鉴性，本文是从一个企业使用Kafka框架的角度来记录及整理的Kafka框架的技术资料，也很有借鉴价值，为了便于阅读与分享，我将其整理一篇Blog。本文内容目录摘要如下：</span></p>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>1）apache kafka消息服务</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>2）kafka在zookeeper中存储结构<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>3）kafka log4j配置</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>4）kafka replication设计机制<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>5）apache kafka监控系列-监控指标</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>6）kafka.common.ConsumerRebalanceFailedException异常解决办法<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>7）kafak安装与使用</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>8）apache kafka中server.properties配置文件参数说明<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>9）apache kafka的consumer初始化时获取不到消息</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>10）Kafka Producer处理逻辑<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>11）apache kafka源代码工程环境搭建(IDEA)</strong></span></p>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>12）apache kafka监控系列-KafkaOffsetMonitor</strong></span></p>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>13）Kafka Controller设计机制</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>14）Kafka性能测试报告(虚拟机版)<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>15）apache kafka监控系列-kafka-web-console</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>16）apache kafka迁移与扩容工具用法<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>17）kafka LeaderNotAvailableException</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>18）apache kafka jmx监控指标参数<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>19）apache kafka性能测试命令使用和构建kafka-perf</strong></span></p>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>20）apache kafka源码构建打包</strong></span></p>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>21）Apache kafka客户端开发-java</strong></span></p>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>22） kafka broker内部架构</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>23）apache kafka源码分析走读-kafka整体结构分析<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>24）apache kafka源码分析走读-Producer分析</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>25）apache kafka性能优化架构分析<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>26）apache kafka源码分析走读-server端网络架构分析</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>27）apache kafka源码分析走读-ZookeeperConsumerConnector分析<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>28）kafka的ZkUtils类的java版本部分代码</strong></span></p>
<span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>29）kafka &amp; mafka client开发与实践<br>
</strong></span>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>30)   kafka文件系统设计那些事</strong></span></p>
<p><span style="font-family:Microsoft YaHei; font-size:14px; color:#006600"><strong>31）kafka的ZookeeperConsumer实现</strong></span></p>
<p><br>
</p>
<p>详细内容如下所示：</p>
<p></p>
<p><span style="font-size:24px; color:#ff0000"><strong>1）apache kafka消息服务</strong></span></p>
<p></p>
<h2 id="kafka消息服务-apachekafka参考" style="margin:10px 0px 0px; padding:0px; font-size:20px; font-weight:normal; line-height:1.5; border-bottom-color:rgb(46,61,84); font-family:Arial,sans-serif">
apache kafka参考</h2>
<p></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<a target="_blank" href="http://kafka.apache.org/documentation.html#brokerconfigs" rel="nofollow" class="external-link" style="color:rgb(50,108,166); text-decoration:none">http://kafka.apache.org/documentation.html</a></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(0,0,0); font-size:20px; line-height:1.5">消息队列分类：</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(0,0,0); font-size:20px; line-height:1.5"> </span><span style="color:rgb(0,0,0); font-size:16px; line-height:1.5625">点对点：</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
消息生产者生产消息发送到queue中，然后消息消费者从queue中取出并且消费消息。这里要注意：</p>
<ul style="font-size:14px; margin:10px 0px 0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<li>消息被消费以后，queue中不再有存储，所以消息消费者不可能消费到已经被消费的消息。</li><li>Queue支持存在多个消费者，但是对一个消息而言，只会有一个消费者可以消费。</li></ul>
<h3 id="kafka消息服务-发布/订阅" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t3" style="color:rgb(255,153,0)"></a>发布/订阅</h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
消息生产者（发布）将消息发布到topic中，同时有多个消息消费者（订阅）消费该消息。和点对点方式不同，发布到topic的消息会被所有订阅者消费。</p>
<h2 id="kafka消息服务-kafka消息队列调研" style="margin:30px 0px 0px; padding:0px; font-size:20px; font-weight:normal; line-height:1.5; border-bottom-color:rgb(46,61,84); font-family:Arial,sans-serif">
<a target="_blank" name="t4" style="color:rgb(255,153,0)"></a>kafka消息队列调研</h2>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
背景介绍</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(0,0,0)">kafka是最初由</span><span style="color:rgb(69,69,69)">Linkedin</span><span style="color:rgb(0,0,0)">公司开发，使用</span><span style="color:rgb(0,0,0)">Scala语言编写，</span>Kafka是一个分布式、分区的、多副本的、多订阅者的日志系统(分布式MQ系统)，可以用于web/nginx日志，搜索日志，监控日志，访问日志等等。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
kafka目前支持多种客户端语言：java，python，c++，php等等。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
</p>
<h3 id="kafka消息服务-总体结构：" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t5" style="color:rgb(255,153,0)"></a>总体结构：</h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<img src="https://img-blog.csdn.net/20140415105154875?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(0,0,0)"><span style="line-height:25px">kafka名词解释和工作方式：</span></span></p>
<ul style="font-size:14px; margin:10px 0px 0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<li>Producer ：消息生产者，就是向kafka broker发消息的客户端。</li><li>Consumer ：消息消费者，向kafka broker取消息的客户端</li><li>Topic ：咋们可以理解为一个队列。</li><li>Consumer Group （CG）：这是kafka用来实现一个topic消息的广播（发给所有的consumer）和单播（发给任意一个consumer）的手段。一个topic可以有多个CG。topic的消息会复制（不是真的复制，是概念上的）到所有的CG，但每个CG只会把消息发给该CG中的一个consumer。如果需要实现广播，只要每个consumer有一个独立的CG就可以了。要实现单播只要所有的consumer在同一个CG。用CG还可以将consumer进行自由的分组而不需要多次发送消息到不同的topic。</li><li>Broker ：一台kafka服务器就是一个broker。一个集群由多个broker组成。一个broker可以容纳多个topic。</li><li>Partition：为了实现扩展性，一个非常大的topic可以分布到多个broker（即服务器）上，一个topic可以分为多个partition，每个partition是一个有序的队列。partition中的每条消息都会被分配一个有序的id（offset）。kafka只保证按一个partition中的顺序将消息发给consumer，不保证一个topic的整体（多个partition间）的顺序。</li><li> Offset：kafka的存储文件都是按照offset.kafka来命名，用offset做名字的好处是方便查找。例如你想找位于2049的位置，只要找到2048.kafka的文件即可。当然the first offset就是00000000000.kafka</li></ul>
<h3 id="kafka消息服务-kafka特性：" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t6" style="color:rgb(255,153,0)"></a><span style="font-size:14px"> </span><span style="line-height:1.5625">kafka特性：</span></h3>
<ul style="font-size:14px; margin:10px 0px 0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<li>通过O(1)的磁盘数据结构提供消息的持久化，这种结构对于即使数以TB的消息存储也能够保持长时间的稳定性能。</li><li>高吞吐量：即使是非常普通的硬件kafka也可以支持每秒数十万的消息。</li><li><span style="line-height:1.4285715">支持同步和异步复制两种HA</span></li><li>Consumer客户端pull，随机读,利用sendfile系统调用，zero-copy ,批量拉数据</li><li>消费状态保存在客户端</li><li>消息存储顺序写</li><li>数据迁移、扩容对用户透明<span style="line-height:1.4285715"><br>
</span></li><li>支持Hadoop并行数据加载。</li><li>支持online和offline的场景。</li><li>持久化：通过将数据持久化到硬盘以及replication防止数据丢失。</li><li>scale out：无需停机即可扩展机器。</li><li>定期删除机制，支持设定partitions的segment file保留时间。</li></ul>
<h3 id="kafka消息服务-可靠性（一致性)" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t7" style="color:rgb(255,153,0)"></a>可靠性（一致性)</h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
kafka(MQ)要实现从producer到consumer之间的可靠的消息传送和分发。传统的MQ系统通常都是通过broker和consumer间的确认（ack）机制实现的，并在broker保存消息分发的状态。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
即使这样一致性也是很难保证的（参考原文）。kafka的做法是由consumer自己保存状态，也不要任何确认。这样虽然consumer负担更重，但其实更灵活了。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
因为不管consumer上任何原因导致需要重新处理消息，都可以再次从broker获得。</p>
<h3 id="kafka消息服务-kafak系统扩展性" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t8" style="color:rgb(255,153,0)"></a>kafak系统扩展性</h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
kafka使用zookeeper来实现动态的集群扩展，不需要更改客户端（producer和consumer）的配置。broker会在zookeeper注册并保持相关的元数据（topic，partition信息等）更新。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
而客户端会在zookeeper上注册相关的watcher。一旦zookeeper发生变化，客户端能及时感知并作出相应调整。这样就保证了添加或去除broker时，各broker间仍能自动实现负载均衡。</p>
<h3 id="kafka消息服务-kafka设计目标" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t9" style="color:rgb(255,153,0)"></a>kafka设计目标</h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
高吞吐量是其核心设计之一。</p>
<ul style="font-size:14px; margin:10px 0px 0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<li>数据磁盘持久化：消息不在内存中cache，直接写入到磁盘，充分利用磁盘的顺序读写性能。</li><li>zero-copy：减少IO操作步骤。</li><li>支持数据批量发送和拉取。</li><li>支持数据压缩。</li><li>Topic划分为多个partition，提高并行处理能力。</li></ul>
<h3 id="kafka消息服务-Producer负载均衡和HA机制" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t10" style="color:rgb(255,153,0)"></a>Producer负载均衡和HA机制</h3>
<ul style="font-size:14px; margin:10px 0px 0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<li>producer根据用户指定的算法，将消息发送到指定的partition。</li><li>存在多个partiiton，每个partition有自己的replica，每个replica分布在不同的Broker节点上。</li><li>多个partition需要选取出lead partition，lead partition负责读写，并由zookeeper负责fail over。</li><li>通过zookeeper管理broker与consumer的动态加入与离开。<br>
</li></ul>
<h3 id="kafka消息服务-Consumer的pull机制" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t11" style="color:rgb(255,153,0)"></a>Consumer的pull机制</h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
由于kafka broker会持久化数据，broker没有cahce压力，因此，consumer比较适合采取pull的方式消费数据，具体特别如下：</p>
<ul style="font-size:14px; margin:10px 0px 0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<li><span style="color:rgb(0,0,0)"><span style="line-height:25px">简化kafka设计，降低了难度。</span></span></li><li><span style="color:rgb(0,0,0)"><span style="line-height:25px">Consumer根据消费能力自主控制消息拉取速度。</span></span></li><li><span style="color:rgb(0,0,0)"><span style="line-height:25px">consumer根据自身情况自主选择消费模式，例如批量，重复消费，从制定partition或位置(offset)开始消费等.</span></span></li></ul>
<h3 id="kafka消息服务-Consumer与topic关系以及机制" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t12" style="color:rgb(255,153,0)"></a>Consumer与topic关系以及机制</h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
本质上kafka只支持Topic.每个consumer属于一个consumer group;反过来说,每个group中可以有多个consumer.对于Topic中的一条特定的消息,<br>
只会被订阅此Topic的每个group中的一个consumer消费,此消息不会发送给一个group的多个consumer;那么一个group中所有的consumer将会交错的消费整个Topic.<br>
如果所有的consumer都具有相同的group,这种情况和JMS queue模式很像;消息将会在consumers之间负载均衡.<br>
如果所有的consumer都具有不同的group,那这就是"发布-订阅";消息将会广播给所有的消费者.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="line-height:1.4285715">在kafka中,一个partition中的消息只会被group中的一个consumer消费(同一时刻);每个group中consumer消息消费互相独立;我们可以认为一个group是一个"订阅"者,</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
一个Topic中的每个partions,只会被一个"订阅者"中的一个consumer消费,不过一个consumer可以同时消费多个partitions中的消息.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
kafka只能保证一个partition中的消息被某个consumer消费时是顺序的.事实上,从Topic角度来说,当有多个partitions时,消息仍不是全局有序的.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(0,0,0)"><span style="line-height:25px"> </span></span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
通常情况下,一个group中会包含多个consumer,这样不仅可以提高topic中消息的并发消费能力,而且还能提高"故障容错"性,如果group中的某个consumer失效,</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
那么其消费的partitions将会有其他consumer自动接管.<span style="line-height:1.4285715">kafka的设计原理决定,对于一个topic,同一个group中不能有多于partitions个数的consumer同时消费,</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="line-height:1.4285715">否则将意味着某些consumer将无法得到消息.</span></p>
<h3 id="kafka消息服务-Producer均衡算法" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t13" style="color:rgb(255,153,0)"></a>Producer<span style="line-height:1.5625">均衡算法</span></h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
kafka集群中的任何一个broker,都可以向producer提供metadata信息,这些metadata中包含"集群中存活的servers列表"/"partitions leader列表"<br>
等信息(请参看zookeeper中的节点信息).当producer获取到metadata信心之后, producer将会和Topic下所有partition leader保持socket连接;<br>
消息由producer直接通过socket发送到broker,中间不会经过任何"路由层".事实上,消息被路由到哪个partition上,有producer客户端决定.<br>
比如可以采用"random""key-hash""轮询"等,如果一个topic中有多个partitions,那么在producer端实现"消息均衡分发"是必要的.<br>
在producer端的配置文件中,开发者可以指定partition路由的方式.</p>
<h3 id="kafka消息服务-Consumer均衡算法" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t14" style="color:rgb(255,153,0)"></a><strong>Consumer均衡算法</strong></h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
当一个group中,有consumer加入或者离开时,会触发partitions均衡.均衡的最终目的,是提升topic的并发消费能力.<br>
1) 假如topic1,具有如下partitions: P0,P1,P2,P3<br>
2) 加入group中,有如下consumer: C0,C1<br>
3) 首先根据partition索引号对partitions排序: P0,P1,P2,P3<br>
4) 根据consumer.id排序: C0,C1<br>
5) 计算倍数: M = [P0,P1,P2,P3].size / [C0,C1].size,本例值M=2(向上取整)<br>
6) 然后依次分配partitions: C0 = [P0,P1],C1=[P2,P3],即Ci = [P(i * M),P((i + 1) * M -1)]</p>
<h3 id="kafka消息服务-kafkabroker集群内broker之间replica机制" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t15" style="color:rgb(255,153,0)"></a><span style="font-size:14px">kafka broker集群内broker之间replica机制</span></h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
kafka中,replication策略是基于partition,而不是topic;kafka将每个partition数据复制到多个server上,任何一个partition有一个leader和多个follower(可以没有);</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
备份的个数可以通过broker配置文件来设定.leader处理所有的read-write请求,follower需要和leader保持同步.Follower就像一个"consumer",</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
消费消息并保存在本地日志中;leader负责跟踪所有的follower状态,如果follower"落后"太多或者失效,leader将会把它从replicas同步列表中删除.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
当所有的follower都将一条消息保存成功,此消息才被认为是"committed",那么此时consumer才能消费它,这种同步策略,就要求follower和leader之间必须具有良好的网络环境.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
即使只有一个replicas实例存活,仍然可以保证消息的正常发送和接收,只要zookeeper集群存活即可.(备注:不同于其他分布式存储,比如hbase需要"多数派"存活才行)</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
k<strong>afka判定一个follower存活与否的条件有2个</strong>:</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
1) follower需要和zookeeper保持良好的链接    </p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
2) 它必须能够及时的跟进leader,不能落后太多.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
如果同时满足上述2个条件,那么leader就认为此follower是"活跃的".如果一个follower失效(server失效)或者落后太多,</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
leader将会把它从同步列表中移除[备注:如果此replicas落后太多,<span style="line-height:1.4285715">它将会继续从leader中fetch数据,直到足够up-to-date,</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="line-height:1.4285715">然后再次加入到同步列表中;kafka不会更换replicas宿主!因为"同步列表"中replicas需要足够快,</span><span style="line-height:1.4285715">这样才能保证producer发布消息时接受到ACK的延迟较小。</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<strong>当leader失效时</strong>,需在followers中选取出新的leader,可能此时follower落后于leader,因此需要选择一个"up-to-date"的follower.kafka中leader选举并没有采用"投票多数派"的算法,</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
因为这种算法对于"网络稳定性"/"投票参与者数量"等条件有较高的要求,而且kafka集群的设计,还需要容忍N-1个replicas失效.对于kafka而言,</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
每个partition中所有的replicas信息都可以在zookeeper中获得,那么选举leader将是一件非常简单的事情.选择follower时需要兼顾一个问题,</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
就是新leader server上所已经承载的partition leader的个数,如果一个server上有过多的partition leader,意味着此server将承受着更多的IO压力.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
在选举新leader,需要考虑到"负载均衡",partition leader较少的broker将会更有可能成为新的leader.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
在整几个集群中,只要有一个replicas存活,那么此partition都可以继续接受读写操作.</p>
<h3 id="kafka消息服务-总结:" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t16" style="color:rgb(255,153,0)"></a><em>总结:</em> </h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
    1) Producer端直接连接broker.list列表,从列表中返回TopicMetadataResponse,该<span style="font-size:13.63636302948px">Metadata包含</span>Topic下每个partition leader建立socket连接并发送消息.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
    2) Broker端使用zookeeper用来注册broker信息,以及监控partition leader存活性.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
    3) Consumer端使用zookeeper用来注册consumer信息,其中包括consumer消费的partition列表等,同时也用来发现broker列表,并和partition leader建立socket连接,并获取消息.</p>
<h3 id="kafka消息服务-性能测试" style="margin:30px 0px 0px; padding:0px; font-size:16px; line-height:1.5625; font-family:Arial,sans-serif">
<a target="_blank" name="t17" style="color:rgb(255,153,0)"></a><span style="line-height:1.5625">性能测试</span></h3>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
目前我已经在虚拟机上做了性能测试。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
测试环境：cpu: 双核   内存 ：2GB   硬盘：60GB </p>
<div class="table-wrap" style="font-size:14px; margin:10px 0px 0px; padding:0px; overflow-x:auto; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<table class="confluenceTable tablesorter               " style="color:rgb(51,51,51); border-collapse:collapse; margin:0px; overflow-x:auto">
<thead>
<tr class="sortableHeader">
<th class="confluenceTh sortableHeader" style="border:1px solid rgb(221,221,221); padding:7px 15px 7px 10px; vertical-align:top; color:rgb(0,0,0); background-color:rgb(240,240,240)">
<div class="tablesorter-header-inner" style="margin:0px; padding:0px">测试指标</div>
</th>
<th class="confluenceTh sortableHeader" style="border:1px solid rgb(221,221,221); padding:7px 15px 7px 10px; vertical-align:top; color:rgb(0,0,0); background-color:rgb(240,240,240)">
<div class="tablesorter-header-inner" style="margin:0px; padding:0px">性能相关说明</div>
</th>
<th colspan="1" class="confluenceTh sortableHeader" style="border:1px solid rgb(221,221,221); padding:7px 15px 7px 10px; vertical-align:top; color:rgb(0,0,0); background-color:rgb(240,240,240)">
<div class="tablesorter-header-inner" style="margin:0px; padding:0px">结论</div>
</th>
</tr>
</thead>
<tbody>
<tr>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
消息堆积压力测试</td>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; background-color:transparent">
单个kafka broker节点测试，启动一个kafka broker和Producer，Producer不断向broker发送数据，</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; background-color:transparent">
直到broker堆积数据为18GB为止(停止Producer运行)。<span style="line-height:1.4285715">启动Consumer，不间断从broker获取数据，</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; background-color:transparent">
<span style="line-height:1.4285715">直到全部数据读取完成为止，</span><span style="line-height:1.4285715">最后查看Producer==</span><span style="line-height:1.4285715">Consumer数据</span><span style="line-height:1.4285715">，没有出现卡死或broker不响应现象</span></p>
</td>
<td colspan="1" class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; background-color:transparent">
数据大量堆积不会出现broker卡死</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; background-color:transparent">
或不响应现象</p>
</td>
</tr>
<tr>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
生产者速率</td>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
1.200byte/msg,4w/s左右。2.1KB/msg,1w/s左右</td>
<td colspan="1" class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
性能上是完全满足要求，其性能主要由磁盘决定</td>
</tr>
<tr>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
消费者速率</td>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
1.200byte/msg,4w/s左右。2.1KB/msg,1w/s左右</td>
<td colspan="1" class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
性能上是完全满足要求，其性能主要由磁盘决定</td>
</tr>
</tbody>
</table>
</div>
<br>
<span style="font-size:24px; color:#ff0000"><strong>2）kafka在zookeeper中存储结构</strong></span>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<span style="font-size:24px; color:rgb(51,51,255)"><img src="https://img-blog.csdn.net/20140923175837147?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"></span></blockquote>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<h1 style="margin:0px; padding:0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<a target="_blank" name="t1" style="color:rgb(255,153,0)"></a><span style="font-size:18px">1.topic注册信息</span></h1>
<p class="p1" style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
/brokers/topics/[topic] :</p>
<p class="p1" style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
存储某个topic的partitions所有分配信息</p>
<div class="table-wrap" style="font-size:14px; margin:10px 0px 0px; padding:0px; overflow-x:auto; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<table class="confluenceTable                            " style="color:rgb(51,51,51); border-collapse:collapse; margin:0px; overflow-x:auto">
<tbody>
<tr>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:18px">Schema:</span></code></div>
<div class="line number2 index1 alt1" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:14px"></span></code></div>
<span style="font-size:14px; color:rgb(51,102,255)">{<br>
    "version": "版本编号目前固定为数字1",<br>
    "partitions": {<br>
        "partitionId编号": [<br>
            同步副本组brokerId列表<br>
        ],<br>
        "partitionId编号": [<br>
            同步副本组brokerId列表<br>
        ],<br>
        .......<br>
    }<br>
}</span>
<div class="line number10 index9 alt1" style="margin:0px; padding:0px"><code class="java plain"></code></div>
<div class="line number11 index10 alt2" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:18px">Example:</span></code></div>
</div>
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<span style="font-size:14px">{<br>
<span style="white-space:pre"></span>"version": 1,<br>
<span style="white-space:pre"></span>"partitions": {<br>
<span style="white-space:pre"></span>"<span style="color:rgb(102,0,204)">0</span>": [<span style="color:rgb(51,51,255)">1, 2</span>],<br>
<span style="white-space:pre"></span>"<span style="color:rgb(102,0,204)">1</span>": [<span style="color:rgb(51,51,255)">2, 1</span>],<br>
<span style="white-space:pre"></span>"<span style="color:rgb(102,0,204)">2</span>": [<span style="color:rgb(51,51,255)">1, 2</span>],<br>
<span style="white-space:pre"></span>}<br>
}</span><br>
</div>
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<span style="font-size:14px">说明：紫红色为patitions编号，蓝色为<span style="color:rgb(0,0,0)">同步副本组brokerId列表</span></span></div>
</td>
</tr>
</tbody>
</table>
</div>
<h1 style="margin:10px 0px 0px; padding:0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<a target="_blank" name="t2" style="color:rgb(255,153,0)"></a><span style="font-size:18px">2.partition状态信息</span></h1>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="font-size:13.63636302948px">/brokers/topics/[topic]/partitions/[0...N]  </span><span style="font-size:13.63636302948px">其中[0..N]表示partition索引号</span><br>
</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
/brokers/topics/[topic]/partitions/[partitionId]/state</p>
<div class="table-wrap" style="font-size:14px; margin:10px 0px 0px; padding:0px; overflow-x:auto; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<table class="confluenceTable                            " style="color:rgb(51,51,51); border-collapse:collapse; margin:0px; overflow-x:auto">
<tbody>
<tr>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:18px">Schema:</span></code></div>
<div class="line number2 index1 alt1" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:14px"></span></code></div>
<span style="font-size:14px; color:rgb(51,102,255)">{<br>
<span style="white-space:pre"></span>"controller_epoch": 表示kafka集群中的中央控制器选举次数,<br>
<span style="white-space:pre"></span>"leader": 表示该partition选举leader的brokerId,<br>
<span style="white-space:pre"></span>"version": 版本编号默认为1,<br>
<span style="white-space:pre"></span>"leader_epoch": 该partition leader选举次数,<br>
<span style="white-space:pre"></span>"isr": [<span style="font-size:13.63636302948px">同步副本组brokerId列表</span>]<br>
}</span>
<div class="line number13 index12 alt2" style="margin:0px; padding:0px"><code class="java plain"></code></div>
<div class="line number14 index13 alt1" style="margin:0px; padding:0px"> </div>
<div class="line number15 index14 alt2" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:18px">Example:</span></code></div>
<div class="line number16 index15 alt1" style="margin:0px; padding:0px"><code class="java plain"></code></div>
<span style="font-size:14px">{<br>
<span style="color:rgb(51,102,255)"><span style="white-space:pre"></span>"controller_epoch": 1,<br>
<span style="white-space:pre"></span>"leader": 2,<br>
<span style="white-space:pre"></span>"version": 1,<br>
<span style="white-space:pre"></span>"leader_epoch": 0,<br>
<span style="white-space:pre"></span>"isr": [2, 1]</span><br>
}</span>
<div class="line number22 index21 alt1" style="margin:0px; padding:0px"><code class="java plain"></code></div>
</div>
</td>
</tr>
</tbody>
</table>
</div>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14.3999996185303px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
</p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a><span style="font-size:18px">3. Broker注册信息</span></h1>
<span style="font-family:Arial; font-size:14px; line-height:26px">/brokers/ids/[0...N]                 </span><span style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"></span>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14px; line-height:26px">
每个broker的配置文件中都需要指定一个数字类型的id(全局不可重复),此节点为临时<span style="color:rgb(51,51,51); font-family:Arial,sans-serif; font-size:13.63636302948px; line-height:20px">znode</span>(EPHEMERAL)</p>
<div class="syntaxhighlighter nogutter  java" style="font-size:14px; margin:0px; padding:0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<div class="table-wrap" style="margin:10px 0px 0px; padding:0px; overflow-x:auto">
<table class="confluenceTable                            " style="color:rgb(51,51,51); border-collapse:collapse; margin:0px; overflow-x:auto">
<tbody>
<tr>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:18px">Schema:</span></code></div>
<div class="line number2 index1 alt1" style="margin:0px; padding:0px"><code class="java plain"></code></div>
<span style="font-size:14px">{<br>
<span style="color:rgb(51,102,255)"><span style="white-space:pre"></span>"jmx_port": jmx端口号,<br>
<span style="white-space:pre"></span>"timestamp": kafka broker初始启动时的时间戳,<br>
<span style="white-space:pre"></span>"host": 主机名或ip地址,<br>
<span style="white-space:pre"></span>"version": 版本编号默认为1,<br>
<span style="white-space:pre"></span>"port": kafka broker的服务端端口号,由server.properties中参数port确定</span><br>
}</span>
<div class="line number8 index7 alt1" style="margin:0px; padding:0px"><code class="java plain"></code></div>
<div class="line number9 index8 alt2" style="margin:0px; padding:0px"> </div>
<div class="line number10 index9 alt1" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:18px">Example:</span></code></div>
<div class="line number11 index10 alt2" style="margin:0px; padding:0px"><code class="java plain"></code></div>
<span style="font-size:14px">{<br>
<span style="color:rgb(51,102,255)"><span style="white-space:pre"></span>"jmx_port": 6061,</span></span></div>
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<span style="font-size:14px"><span style="color:rgb(51,102,255)"><span style="white-space:pre"></span>"timestamp":"1403061899859"<br>
<span style="white-space:pre"></span>"version": 1,<br>
<span style="white-space:pre"></span>"host": "192.168.1.148",<br>
<span style="white-space:pre"></span>"port": 9092</span><br>
}</span></div>
</td>
</tr>
</tbody>
</table>
</div>
</div>
<h1 style="margin:10px 0px 0px; padding:0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<a target="_blank" name="t4" style="color:rgb(255,153,0)"></a><span style="font-size:18px">4. Controller epoch: </span></h1>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; font-family:Arial,sans-serif; line-height:20px">
/controller_epoch -&gt; int (epoch)   </p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(51,102,255)">此值为一个数字,kafka集群中第一个broker第一次启动时为1，以后只要集群中center controller中央控制器所在broker变更或挂掉，就会重新选举新的<span style="font-size:13.63636302948px">center controller，每次<span style="font-size:13.63636302948px">center controller变更</span><span style="font-size:13.63636302948px">controller_epoch值就会
 + 1;</span></span> </span></p>
<h1 style="margin:10px 0px 0px; padding:0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<a target="_blank" name="t5" style="color:rgb(255,153,0)"></a><span style="font-size:18px">5. Controller注册信息:</span></h1>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; font-family:Arial,sans-serif; line-height:20px">
/controller -&gt; int (broker id of the controller)  存储<span style="font-size:13.63636302948px">center controller中央控制器所在kafka broker的信息</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(51,102,255); font-size:13.63636302948px"></span></p>
<div class="line number1 index0 alt2" style="font-family:Arial; line-height:26px; color:rgb(51,51,51); font-size:11.8181819915771px; margin:0px; padding:0px">
<table class="confluenceTable                             " style="font-family:Arial,sans-serif; color:rgb(51,51,51); border-collapse:collapse; margin:0px; overflow-x:auto">
<tbody>
<tr>
<td class="confluenceTd" style="border-style:solid; border-color:rgb(221,221,221); padding:7px 10px; vertical-align:top">
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:18px">Schema:</span></code></div>
<div class="line number2 index1 alt1" style="margin:0px; padding:0px"><code class="java plain"></code></div>
<span style="font-size:14px">{</span><br>
<span style="font-size:14px; color:rgb(51,102,255)"><span style="white-space:pre"></span>"version": 版本编号默认为1,<br>
<span style="white-space:pre"></span>"brokerid": <span style="font-family:Arial,sans-serif; line-height:20px">kafka集群中broker唯一编号</span>,<br>
<span style="white-space:pre"></span>"timestamp": kafka broker<span style="font-family:Arial,sans-serif; line-height:20px">中央控制器变更时</span>的时间戳</span><br>
<span style="font-size:14px">}</span>
<div class="line number8 index7 alt1" style="margin:0px; padding:0px"><code class="java plain"></code></div>
<div class="line number9 index8 alt2" style="margin:0px; padding:0px"> </div>
<div class="line number10 index9 alt1" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:18px">Example:</span></code></div>
<div class="line number11 index10 alt2" style="margin:0px; padding:0px"><code class="java plain"></code></div>
<span style="font-size:14px"></span></div>
<span style="font-size:14px; color:rgb(51,102,255)">{<br>
<span style="white-space:pre"></span>"version": 1,<br>
<span style="white-space:pre"></span>"brokerid": 3,<br>
<span style="white-space:pre"></span>"timestamp": "1403061802981"<br>
}</span>
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<span style="font-size:14px"></span>
<div class="line number16 index15 alt1" style="margin:0px; padding:0px"><code class="java plain"></code></div>
</div>
</td>
</tr>
</tbody>
</table>
<br>
<br>
</div>
<div class="line number1 index0 alt2" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px; padding:0px">
<span style="font-size:24px"><span style="color:rgb(51,102,255)">Consumer and Consumer group概念: </span></span></div>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,51,51)"><span style="font-size:23.6363639831543px"><img src="https://img-blog.csdn.net/20141010151449039?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"></span></span></div>
</blockquote>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<span style="color:rgb(51,102,255)">a.每个consumer客户端被创建时,会向zookeeper注册自己的信息;<br>
</span><span style="color:rgb(51,102,255)">b.此作用主要是为了"负载均衡".<br>
</span><span style="color:rgb(51,102,255)">c.同一个Consumer Group中的Consumers，Kafka将相应Topic中的每个消息只发送给其中一个Consumer。<br>
</span><span style="color:rgb(51,102,255)">d.Consumer Group中的每个Consumer读取Topic的一个或多个Partitions，并且是唯一的Consumer；<br>
</span><span style="color:rgb(51,102,255)">e.一个Consumer group的多个consumer的所有线程依次有序地消费一个topic的所有partitions,如果Consumer group中所有consumer总线程大于partitions数量，则会出现空闲情况;</span>
<blockquote style="margin:0px 0px 0px 40px; border:none; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)">举例说明：</span></div>
</blockquote>
<blockquote style="margin:0px 0px 0px 40px; border:none; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)">kafka集群中创建一个topic为report-log   4 partitions 索引编号为0,1,2,3</span></div>
</blockquote>
<blockquote style="margin:0px 0px 0px 40px; border:none; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)">假如有目前有三个消费者node：注意--&gt;一个<span style="font-size:13.63636302948px">consumer中一个消费线程可以消费一个或多个partition.</span></span></div>
</blockquote>
<blockquote style="margin:0px 0px 0px 40px; border:none; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)">如果每个consumer创建一个consumer thread线程,各个node消费情况如下，node1消费索引编号为0,1分区，node2费索引编号为2,node3费索引编号为3</span></div>
</blockquote>
<blockquote style="margin:0px 0px 0px 40px; border:none; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)">如果每个consumer创建2个consumer thread线程，各个node消费情况如下(是从consumer node先后启动状态来确定的)，node1消费索引编号为0,1分区；node2费索引编号为2,3；node3为空闲状态</span></div>
</blockquote>
<span style="font-size:18px"><span style="color:rgb(255,0,0)">总结</span></span><span style="font-size:18px; color:rgb(51,102,255)">：<br>
</span><span style="color:rgb(51,102,255)">从以上可知，Consumer Group中各个consumer是根据先后启动的顺序有序消费一个topic的所有partitions的。</span>
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)">如果Consumer Group中<span style="font-size:13.63636302948px">所有</span>consumer的总线程数大于partitions数量，则可能consumer thread或consumer会出现空闲状态。</span></div>
</blockquote>
<div class="line number1 index0 alt2" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px; padding:0px">
<span style="color:rgb(51,102,255)"><br>
</span></div>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
</blockquote>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<span style="font-size:18px; color:rgb(0,153,0)"><strong>Consumer均衡算法</strong></span><br>
<span style="color:rgb(51,102,255)">当一个group中,有consumer加入或者离开时,会触发partitions均衡.均衡的最终目的,是提升topic的并发消费能力.</span><br>
<span style="color:rgb(51,102,255)">1) 假如topic1,具有如下partitions: P0,P1,P2,P3</span><br>
<span style="color:rgb(51,102,255)">2) 加入group中,有如下consumer: C0,C1</span><br>
<span style="color:rgb(51,102,255)">3) 首先根据partition索引号对partitions排序: P0,P1,P2,P3</span><br>
<span style="color:rgb(51,102,255)">4) 根据(consumer.id + '-'+ thread序号)排序: C0,C1</span><br>
<span style="color:rgb(51,102,255)">5) 计算倍数: M = [P0,P1,P2,P3].size / [C0,C1].size,本例值M=2(向上取整)</span><br>
<span style="color:rgb(51,102,255)">6) 然后依次分配partitions: C0 = [P0,P1],C1=[P2,P3],即Ci = [P(i * M),P((i + 1) * M -1)]</span></blockquote>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<h1 style="margin:10px 0px 0px; padding:0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<a target="_blank" name="t6" style="color:rgb(255,153,0)"></a><span style="font-size:18px">6. Consumer注册信息:</span></h1>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
每个consumer都有一个唯一的ID(<span style="color:rgb(51,51,51); font-family:Arial,sans-serif; font-size:13.63636302948px; line-height:20px">consumerId</span>可以通过配置文件指定,也可以由系统生成),此id用来标记消费者信息.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
/consumers/[groupId]/ids/[<span style="font-size:13.63636302948px">consumerIdString</span>]</p>
<div class="syntaxhighlighter nogutter  java" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px; padding:0px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial,sans-serif; line-height:20px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial,sans-serif; line-height:20px; color:rgb(51,51,51); background-color:transparent">
是一个临时的znode,此节点的值为请看<span style="font-family:Arial; line-height:26px"><span style="font-family:Arial,sans-serif; font-size:13.63636302948px; line-height:20px">consumerIdString</span>产生规则</span>,即表示此consumer目前所消费的topic + partitions列表.</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial,sans-serif; line-height:20px; color:rgb(51,51,51); background-color:transparent">
<span style="font-family:Arial; line-height:26px">consumerId产生规则：</span><br>
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
   String<strong><span style="color:rgb(51,102,255)">consumerUuid</span></strong> = null;<br>
    if(config.consumerId!=null &amp;&amp; config.consumerId)<br>
      consumerUuid = consumerId;<br>
    else {<br>
      String <span style="color:rgb(51,102,255)"><strong>uuid</strong></span> = UUID.randomUUID()<br>
      consumerUuid = "%s-%d-%s".format(<br>
        InetAddress.getLocalHost.getHostName, System.currentTimeMillis,<br>
        uuid.getMostSignificantBits().toHexString.substring(0,8));</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
     }<br>
     <span style="color:rgb(51,102,255)">String </span><span style="color:rgb(255,0,0)"><strong>consumerIdString</strong></span><span style="color:rgb(51,102,255)"> = config.groupId + "_" + consumerUuid;</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial,sans-serif; line-height:20px">
</p>
<div class="table-wrap" style="font-family:Arial,sans-serif; line-height:20px; color:rgb(51,51,51); margin:10px 0px 0px; padding:0px; overflow-x:auto">
<table class="confluenceTable                            " style="color:rgb(51,51,51); border-collapse:collapse; margin:0px; overflow-x:auto">
<tbody>
<tr>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:18px">Schema:</span></code></div>
<div class="line number2 index1 alt1" style="margin:0px; padding:0px"><code class="java plain"></code></div>
<span style="font-size:14px">{<br>
<span style="color:rgb(51,102,255)"><span style="white-space:pre"></span>"version": <span style="font-size:13.63636302948px">版本编号默认为1</span>,<br>
<span style="white-space:pre"></span>"subscription": { //订阅topic列表<br>
<span style="white-space:pre"></span>"topic名称": consumer中topic消费者线程数<br>
<span style="white-space:pre"></span>},<br>
<span style="white-space:pre"></span>"pattern": "static",<br>
<span style="white-space:pre"></span>"timestamp": "consumer启动时的时间戳"</span><br>
}</span>
<div class="line number7 index6 alt2" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:14px"></span></code></div>
<div class="line number8 index7 alt1" style="margin:0px; padding:0px"> </div>
<div class="line number9 index8 alt2" style="margin:0px; padding:0px"><code class="java plain"><span style="font-size:18px">Example:</span></code></div>
<div class="line number10 index9 alt1" style="margin:0px; padding:0px"><span style="font-size:14px">{<br>
<span style="color:rgb(51,102,255)"><span style="white-space:pre"></span>"version": 1,<br>
<span style="white-space:pre"></span>"subscription": {<br>
<span style="white-space:pre"></span>"open_platform_opt_push_plus1": 5<br>
<span style="white-space:pre"></span>},<br>
<span style="white-space:pre"></span>"pattern": "static",<br>
<span style="white-space:pre"></span>"timestamp": "1411294187842"</span><br>
}</span><br>
</div>
</div>
</td>
</tr>
<tr>
<td colspan="1" class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
<span style="font-size:14px; font-family:Arial,sans-serif; line-height:20px; background-color:transparent"> </span></td>
</tr>
</tbody>
</table>
</div>
</div>
<h1 style="margin:10px 0px 0px; padding:0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<a target="_blank" name="t7" style="color:rgb(255,153,0)"></a><span style="font-size:18px">7. Consumer owner:</span></h1>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(51,51,51)">/consumers/[groupId]/owners/[topic]/[partitionId] -&gt; </span><span style="color:rgb(51,51,51)">consumerIdString + threadId索引编号</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; font-family:Arial,sans-serif; line-height:20px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)">当consumer启动时,所触发的操作:</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,102,0)">a) 首先进行"Consumer Id注册";</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,102,0)">b) 然后在"Consumer id 注册"节点下注册一个watch用来监听当前group中其他consumer的"<strong>退出</strong>"和"<strong>加入</strong>";只要此znode path下节点列表变更,都会触发此group下consumer的负载均衡.(比如一个consumer失效,那么其他consumer接管partitions).</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,102,0)">c) 在"Broker id 注册"节点下,注册一个watch用来监听broker的存活情况;如果broker列表变更,将会触发所有的groups下的consumer重新balance.</span></p>
<h1 style="margin:10px 0px 0px; padding:0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<a target="_blank" name="t8" style="color:rgb(255,153,0)"></a><span style="font-size:18px">8. Consumer offset:</span></h1>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
/consumers/[groupId]/offsets/[topic]/[partitionId] -&gt; long (offset)</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; font-family:Arial,sans-serif; line-height:20px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,102,0)">用来跟踪每个consumer目前所消费的partition中最大的offset</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,102,0)">此znode为持久节点,可以看出offset跟group_id有关,以表明当消费者组(consumer group)中一个消费者失效,</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,102,0)">重新触发balance,其他consumer可以继续消费.</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14.3999996185303px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="font-size:18px">9. Re-assign partitions</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
/admin/reassign_partitions</p>
<div class="syntaxhighlighter nogutter  java" style="font-size:14px; margin:0px; padding:0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<div class="table-wrap" style="margin:10px 0px 0px; padding:0px; overflow-x:auto">
<table class="confluenceTable                            " style="color:rgb(51,51,51); border-collapse:collapse; margin:0px; overflow-x:auto">
<tbody>
<tr>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><code class="java plain">{</code></div>
<div class="line number2 index1 alt1" style="margin:0px; padding:0px"><code class="java spaces">  <span style="color:rgb(51,102,255)"> </span></code><span style="color:rgb(51,102,255)"><code class="java string">"fields"</code><code class="java plain">:[</code></span></div>
<div class="line number3 index2 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">      </code><code class="java plain">{</code></span></div>
<div class="line number4 index3 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java string">"name"</code><code class="java plain">:</code><code class="java string">"version"</code><code class="java plain">,</code></span></div>
<div class="line number5 index4 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java string">"type"</code><code class="java plain">:</code><code class="java string">"int"</code><code class="java plain">,</code></span></div>
<div class="line number6 index5 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java string">"doc"</code><code class="java plain">:</code><code class="java string">"version id"</code></span></div>
<div class="line number7 index6 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">      </code><code class="java plain">},</code></span></div>
<div class="line number8 index7 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">      </code><code class="java plain">{</code></span></div>
<div class="line number9 index8 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java string">"name"</code><code class="java plain">:</code><code class="java string">"partitions"</code><code class="java plain">,</code></span></div>
<div class="line number10 index9 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java string">"type"</code><code class="java plain">:{</code></span></div>
<div class="line number11 index10 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"type"</code><code class="java plain">:</code><code class="java string">"array"</code><code class="java plain">,</code></span></div>
<div class="line number12 index11 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"items"</code><code class="java plain">:{</code></span></div>
<div class="line number13 index12 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">               </code><code class="java string">"fields"</code><code class="java plain">:[</code></span></div>
<div class="line number14 index13 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                  </code><code class="java plain">{</code></span></div>
<div class="line number15 index14 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"name"</code><code class="java plain">:</code><code class="java string">"topic"</code><code class="java plain">,</code></span></div>
<div class="line number16 index15 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"type"</code><code class="java plain">:</code><code class="java string">"string"</code><code class="java plain">,</code></span></div>
<div class="line number17 index16 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"doc"</code><code class="java plain">:</code><code class="java string">"topic
 of the partition to be reassigned"</code></span></div>
<div class="line number18 index17 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                  </code><code class="java plain">},</code></span></div>
<div class="line number19 index18 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                  </code><code class="java plain">{</code></span></div>
<div class="line number20 index19 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"name"</code><code class="java plain">:</code><code class="java string">"partition"</code><code class="java plain">,</code></span></div>
<div class="line number21 index20 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"type"</code><code class="java plain">:</code><code class="java string">"int"</code><code class="java plain">,</code></span></div>
<div class="line number22 index21 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"doc"</code><code class="java plain">:</code><code class="java string">"the
 partition to be reassigned"</code></span></div>
<div class="line number23 index22 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                  </code><code class="java plain">},</code></span></div>
<div class="line number24 index23 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                  </code><code class="java plain">{</code></span></div>
<div class="line number25 index24 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"name"</code><code class="java plain">:</code><code class="java string">"replicas"</code><code class="java plain">,</code></span></div>
<div class="line number26 index25 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"type"</code><code class="java plain">:</code><code class="java string">"array"</code><code class="java plain">,</code></span></div>
<div class="line number27 index26 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"items"</code><code class="java plain">:</code><code class="java string">"int"</code><code class="java plain">,</code></span></div>
<div class="line number28 index27 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"doc"</code><code class="java plain">:</code><code class="java string">"a
 list of replica ids"</code></span></div>
<div class="line number29 index28 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                  </code><code class="java plain">}</code></span></div>
<div class="line number30 index29 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">               </code><code class="java plain">],</code></span></div>
<div class="line number31 index30 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java plain">}</code></span></div>
<div class="line number32 index31 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"doc"</code><code class="java plain">:</code><code class="java string">"an array
 of partitions to be reassigned to new replicas"</code></span></div>
<div class="line number33 index32 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java plain">}</code></span></div>
<div class="line number34 index33 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">      </code><code class="java plain">}</code></span></div>
<div class="line number35 index34 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">   </code><code class="java plain">]</code></span></div>
<div class="line number36 index35 alt1" style="margin:0px; padding:0px"><code class="java plain">}</code></div>
<div class="line number37 index36 alt2" style="margin:0px; padding:0px"> </div>
<div class="line number38 index37 alt1" style="margin:0px; padding:0px"><code class="java plain">Example:</code></div>
<div class="line number39 index38 alt2" style="margin:0px; padding:0px"><code class="java plain">{</code></div>
<div class="line number40 index39 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">  </code><code class="java string">"version"</code><code class="java plain">: </code><code class="java value">1</code><code class="java plain">,</code></span></div>
<div class="line number41 index40 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">  </code><code class="java string">"partitions"</code><code class="java plain">:</code></span></div>
<div class="line number42 index41 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">     </code><code class="java plain">[</code></span></div>
<div class="line number43 index42 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">        </code><code class="java plain">{</code></span></div>
<div class="line number44 index43 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"topic"</code><code class="java plain">: </code><code class="java string">"Foo"</code><code class="java plain">,</code></span></div>
<div class="line number45 index44 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"partition"</code><code class="java plain">: </code><code class="java value">1</code><code class="java plain">,</code></span></div>
<div class="line number46 index45 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"replicas"</code><code class="java plain">: [</code><code class="java value">0</code><code class="java plain">, </code><code class="java value">1</code><code class="java plain">, </code><code class="java value">3</code><code class="java plain">]</code></span></div>
<div class="line number47 index46 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">        </code><code class="java plain">}</code></span></div>
<div class="line number48 index47 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">     </code><code class="java plain">]            </code></span></div>
<div class="line number49 index48 alt2" style="margin:0px; padding:0px"><code class="java plain">}</code></div>
</div>
</td>
</tr>
</tbody>
</table>
</div>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; background-color:transparent">
 </p>
</div>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14.3999996185303px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="font-size:18px">10. Preferred replication election</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
/admin/preferred_replica_election</p>
<div class="syntaxhighlighter nogutter  java" style="font-size:14px; margin:0px; padding:0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; background-color:transparent">
 </p>
<div class="table-wrap" style="margin:10px 0px 0px; padding:0px; overflow-x:auto">
<table class="confluenceTable                            " style="color:rgb(51,51,51); border-collapse:collapse; margin:0px; overflow-x:auto">
<tbody>
<tr>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><code class="java plain">{</code></div>
<div class="line number2 index1 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">   </code><code class="java string">"fields"</code><code class="java plain">:[</code></span></div>
<div class="line number3 index2 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">      </code><code class="java plain">{</code></span></div>
<div class="line number4 index3 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java string">"name"</code><code class="java plain">:</code><code class="java string">"version"</code><code class="java plain">,</code></span></div>
<div class="line number5 index4 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java string">"type"</code><code class="java plain">:</code><code class="java string">"int"</code><code class="java plain">,</code></span></div>
<div class="line number6 index5 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java string">"doc"</code><code class="java plain">:</code><code class="java string">"version id"</code></span></div>
<div class="line number7 index6 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">      </code><code class="java plain">},</code></span></div>
<div class="line number8 index7 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">      </code><code class="java plain">{</code></span></div>
<div class="line number9 index8 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java string">"name"</code><code class="java plain">:</code><code class="java string">"partitions"</code><code class="java plain">,</code></span></div>
<div class="line number10 index9 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java string">"type"</code><code class="java plain">:{</code></span></div>
<div class="line number11 index10 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"type"</code><code class="java plain">:</code><code class="java string">"array"</code><code class="java plain">,</code></span></div>
<div class="line number12 index11 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"items"</code><code class="java plain">:{</code></span></div>
<div class="line number13 index12 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">               </code><code class="java string">"fields"</code><code class="java plain">:[</code></span></div>
<div class="line number14 index13 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                  </code><code class="java plain">{</code></span></div>
<div class="line number15 index14 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"name"</code><code class="java plain">:</code><code class="java string">"topic"</code><code class="java plain">,</code></span></div>
<div class="line number16 index15 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"type"</code><code class="java plain">:</code><code class="java string">"string"</code><code class="java plain">,</code></span></div>
<div class="line number17 index16 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"doc"</code><code class="java plain">:</code><code class="java string">"topic
 of the partition for which preferred replica election should be triggered"</code></span></div>
<div class="line number18 index17 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                  </code><code class="java plain">},</code></span></div>
<div class="line number19 index18 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                  </code><code class="java plain">{</code></span></div>
<div class="line number20 index19 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"name"</code><code class="java plain">:</code><code class="java string">"partition"</code><code class="java plain">,</code></span></div>
<div class="line number21 index20 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"type"</code><code class="java plain">:</code><code class="java string">"int"</code><code class="java plain">,</code></span></div>
<div class="line number22 index21 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                     </code><code class="java string">"doc"</code><code class="java plain">:</code><code class="java string">"the
 partition for which preferred replica election should be triggered"</code></span></div>
<div class="line number23 index22 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">                  </code><code class="java plain">}</code></span></div>
<div class="line number24 index23 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">               </code><code class="java plain">],</code></span></div>
<div class="line number25 index24 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java plain">}</code></span></div>
<div class="line number26 index25 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"doc"</code><code class="java plain">:</code><code class="java string">"an array
 of partitions for which preferred replica election should be triggered"</code></span></div>
<div class="line number27 index26 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">         </code><code class="java plain">}</code></span></div>
<div class="line number28 index27 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">      </code><code class="java plain">}</code></span></div>
<div class="line number29 index28 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">   </code><code class="java plain">]</code></span></div>
<div class="line number30 index29 alt1" style="margin:0px; padding:0px"><code class="java plain">}</code></div>
<div class="line number31 index30 alt2" style="margin:0px; padding:0px"> </div>
<div class="line number32 index31 alt1" style="margin:0px; padding:0px"><code class="java plain">例子:</code></div>
<div class="line number33 index32 alt2" style="margin:0px; padding:0px"> </div>
<div class="line number34 index33 alt1" style="margin:0px; padding:0px"><code class="java plain">{</code></div>
<div class="line number35 index34 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">  </code><code class="java string">"version"</code><code class="java plain">: </code><code class="java value">1</code><code class="java plain">,</code></span></div>
<div class="line number36 index35 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">  </code><code class="java string">"partitions"</code><code class="java plain">:</code></span></div>
<div class="line number37 index36 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">     </code><code class="java plain">[</code></span></div>
<div class="line number38 index37 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">        </code><code class="java plain">{</code></span></div>
<div class="line number39 index38 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"topic"</code><code class="java plain">: </code><code class="java string">"Foo"</code><code class="java plain">,</code></span></div>
<div class="line number40 index39 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"partition"</code><code class="java plain">: </code><code class="java value">1</code>         </span></div>
<div class="line number41 index40 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">        </code><code class="java plain">},</code></span></div>
<div class="line number42 index41 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">        </code><code class="java plain">{</code></span></div>
<div class="line number43 index42 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"topic"</code><code class="java plain">: </code><code class="java string">"Bar"</code><code class="java plain">,</code></span></div>
<div class="line number44 index43 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">            </code><code class="java string">"partition"</code><code class="java plain">: </code><code class="java value">0</code>         </span></div>
<div class="line number45 index44 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">        </code><code class="java plain">}</code></span></div>
<div class="line number46 index45 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">     </code><code class="java plain">]            </code></span></div>
<div class="line number47 index46 alt2" style="margin:0px; padding:0px"><code class="java plain">}</code></div>
</div>
</td>
</tr>
</tbody>
</table>
</div>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; background-color:transparent">
 </p>
</div>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14.3999996185303px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="font-size:18px">11. 删除topics</span><br>
/admin/delete_topics</p>
<div class="syntaxhighlighter nogutter  java" style="font-size:14px; margin:0px; padding:0px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<div class="table-wrap" style="margin:10px 0px 0px; padding:0px; overflow-x:auto">
<table class="confluenceTable                            " style="color:rgb(51,51,51); border-collapse:collapse; margin:0px; overflow-x:auto">
<tbody>
<tr>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><code class="java plain">Schema:</code></div>
<div class="line number2 index1 alt1" style="margin:0px; padding:0px"><code class="java plain">{ </code><span style="color:rgb(51,102,255)"><code class="java string">"fields"</code><code class="java plain">:</code></span></div>
<div class="line number3 index2 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">    </code><code class="java plain">[ {</code><code class="java string">"name"</code><code class="java plain">: </code><code class="java string">"version"</code><code class="java plain">, </code><code class="java string">"type"</code><code class="java plain">: </code><code class="java string">"int"</code><code class="java plain">, </code><code class="java string">"doc"</code><code class="java plain">: </code><code class="java string">"version
 id"</code><code class="java plain">},</code></span></div>
<div class="line number4 index3 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">      </code><code class="java plain">{</code><code class="java string">"name"</code><code class="java plain">: </code><code class="java string">"topics"</code><code class="java plain">,</code></span></div>
<div class="line number5 index4 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">       </code><code class="java string">"type"</code><code class="java plain">: { </code><code class="java string">"type"</code><code class="java plain">: </code><code class="java string">"array"</code><code class="java plain">, </code><code class="java string">"items"</code><code class="java plain">: </code><code class="java string">"string"</code><code class="java plain">, </code><code class="java string">"doc"</code><code class="java plain">: </code><code class="java string">"an
 array of topics to be deleted"</code><code class="java plain">}</code></span></div>
<div class="line number6 index5 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">      </code><code class="java plain">} ]</code></span></div>
<div class="line number7 index6 alt2" style="margin:0px; padding:0px"><code class="java plain">}</code></div>
<div class="line number8 index7 alt1" style="margin:0px; padding:0px"> </div>
<div class="line number9 index8 alt2" style="margin:0px; padding:0px"><code class="java plain">例子:</code></div>
<div class="line number10 index9 alt1" style="margin:0px; padding:0px"><code class="java plain">{</code></div>
<div class="line number11 index10 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">  </code><code class="java string">"version"</code><code class="java plain">: </code><code class="java value">1</code><code class="java plain">,</code></span></div>
<div class="line number12 index11 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">  </code><code class="java string">"topics"</code><code class="java plain">: [</code><code class="java string">"foo"</code><code class="java plain">, </code><code class="java string">"bar"</code><code class="java plain">]</code></span></div>
<div class="line number13 index12 alt2" style="margin:0px; padding:0px"><code class="java plain">}</code></div>
</div>
</td>
</tr>
</tbody>
</table>
</div>
</div>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
Topic配置</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
/config/topics/[topic_name]</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
例子</p>
<div class="syntaxhighlighter nogutter  java" style="font-family:Arial; font-size:14.3999996185303px; margin:0px; padding:0px; line-height:20px">
<div class="table-wrap" style="font-family:Arial,sans-serif; color:rgb(51,51,51); margin:10px 0px 0px; padding:0px; overflow-x:auto">
<table class="confluenceTable                            " style="color:rgb(51,51,51); border-collapse:collapse; margin:0px; overflow-x:auto">
<tbody>
<tr>
<td class="confluenceTd" style="border:1px solid rgb(221,221,221); padding:7px 10px; vertical-align:top">
<div class="container" title="Hint: double-click to select code" style="margin:0px; padding:0px">
<div class="line number1 index0 alt2" style="margin:0px; padding:0px"><code class="java plain">{</code></div>
<div class="line number2 index1 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">  </code><code class="java string">"version"</code><code class="java plain">: </code><code class="java value">1</code><code class="java plain">,</code></span></div>
<div class="line number3 index2 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">  </code><code class="java string">"config"</code><code class="java plain">: {</code></span></div>
<div class="line number4 index3 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">    </code><code class="java string">"config.a"</code><code class="java plain">: </code><code class="java string">"x"</code><code class="java plain">,</code></span></div>
<div class="line number5 index4 alt2" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">    </code><code class="java string">"config.b"</code><code class="java plain">: </code><code class="java string">"y"</code><code class="java plain">,</code></span></div>
<div class="line number6 index5 alt1" style="margin:0px; padding:0px"><span style="color:rgb(51,102,255)"><code class="java spaces">    </code><code class="java plain">...</code></span></div>
<div class="line number7 index6 alt2" style="margin:0px; padding:0px"><code class="java spaces">  </code><code class="java plain">}</code></div>
<div class="line number8 index7 alt1" style="margin:0px; padding:0px"><code class="java plain">}</code></div>
</div>
</td>
</tr>
</tbody>
</table>
</div>
</div>
<br>
<p><span style="font-size:24px; color:#ff0000"><strong>3）kafka log4j配置</strong></span></p>
<div class="syntaxhighlighter nogutter  java" style="font-family:Arial; font-size:14.3999996185303px; margin:0px; padding:0px; line-height:20px">
</div>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">kafka日志文件分为5种类型，依次为：controller,kafka-request,server,state-change,log-cleaner，不同类型log数据，写到不同文件中:</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px"></span></p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/24490817#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/24490817#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/312267" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/312267/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:545px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">kafka.logs.dir=logs  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.rootLogger=INFO, stdout  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.stdout=org.apache.log4j.ConsoleAppender  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.stdout.layout=org.apache.log4j.PatternLayout  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.stdout.layout.ConversionPattern=[%d] %p %m (%c)%n  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.kafkaAppender=org.apache.log4j.DailyRollingFileAppender  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.kafkaAppender.DatePattern=<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">'.'</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">yyyy-MM-dd-HH  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.kafkaAppender.File=${kafka.logs.dir}/server.log  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.kafkaAppender.layout=org.apache.log4j.PatternLayout  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.kafkaAppender.layout.ConversionPattern=[%d] %p %m (%c)%n  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.stateChangeAppender=org.apache.log4j.DailyRollingFileAppender  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.stateChangeAppender.DatePattern=<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">'.'</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">yyyy-MM-dd-HH  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.stateChangeAppender.File=${kafka.logs.dir}/state-change.log  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.stateChangeAppender.layout=org.apache.log4j.PatternLayout  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.stateChangeAppender.layout.ConversionPattern=[%d] %p %m (%c)%n  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.requestAppender=org.apache.log4j.DailyRollingFileAppender  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.requestAppender.DatePattern=<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">'.'</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">yyyy-MM-dd-HH  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.requestAppender.File=${kafka.logs.dir}/kafka-request.log  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.requestAppender.layout=org.apache.log4j.PatternLayout  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.requestAppender.layout.ConversionPattern=[%d] %p %m (%c)%n  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.cleanerAppender=org.apache.log4j.DailyRollingFileAppender  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.cleanerAppender.DatePattern=<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">'.'</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">yyyy-MM-dd-HH  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.cleanerAppender.File=log-cleaner.log  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.cleanerAppender.layout=org.apache.log4j.PatternLayout  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.cleanerAppender.layout.ConversionPattern=[%d] %p %m (%c)%n  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.controllerAppender=org.apache.log4j.DailyRollingFileAppender  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.controllerAppender.DatePattern=<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">'.'</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">yyyy-MM-dd-HH  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.controllerAppender.File=${kafka.logs.dir}/controller.log  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.controllerAppender.layout=org.apache.log4j.PatternLayout  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.appender.controllerAppender.layout.ConversionPattern=[%d] %p %m (%c)%n  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"># Turn on all our debugging info  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">#log4j.logger.kafka.producer.async.DefaultEventHandler=DEBUG, kafkaAppender  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">#log4j.logger.kafka.client.ClientUtils=DEBUG, kafkaAppender  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">#log4j.logger.kafka.perf=DEBUG, kafkaAppender  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">#log4j.logger.kafka.perf.ProducerPerformance$ProducerThread=DEBUG, kafkaAppender  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">#log4j.logger.org.I0Itec.zkclient.ZkClient=DEBUG  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.logger.kafka=INFO, kafkaAppender  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.logger.kafka.network.RequestChannel$=WARN, requestAppender  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.additivity.kafka.network.RequestChannel$=<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">#log4j.logger.kafka.network.Processor=TRACE, requestAppender  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">#log4j.logger.kafka.server.KafkaApis=TRACE, requestAppender  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">#log4j.additivity.kafka.server.KafkaApis=<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.logger.kafka.request.logger=WARN, requestAppender  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.additivity.kafka.request.logger=<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.logger.kafka.controller=TRACE, controllerAppender  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.additivity.kafka.controller=<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.logger.kafka.log.LogCleaner=INFO, cleanerAppender  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.additivity.kafka.log.LogCleaner=<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.logger.kafka.log.Cleaner=INFO, cleanerAppender  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.additivity.kafka.log.Cleaner=<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.logger.state.change.logger=TRACE, stateChangeAppender  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log4j.additivity.state.change.logger=<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span></span></li></ol>
</div>
<br>
<span style="font-size:24px; color:#ff0000"><strong>4）kafka replication设计机制</strong></span>
<p></p>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<span style="color:rgb(50,50,50); font-family:Arial,sans-serif; font-size:20px; line-height:1.5">概览:</span></blockquote>
<p></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(50,50,50)">其中一个broker被选举作为整个集群控制器，他将负责几个方面工作：</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(50,50,50)">1.管理或领导分区变化.</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(50,50,50)">2.create topic,delete topic</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(50,50,50)">3.replicas(执行复制计划，复制partition)</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(50,50,50)">集群控制器做出决定以后，操作信息或状态将永久注册并存储在zookeeper上，并且也可以通过RPC方式发送新的决定操作broker。控制器发布的决定来源真实，他将用于client请求路由和broker的重启或恢复状态。</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(50,50,50)">如果有一个新的broker加入或启动。controller会通过RPC调用发出新的决定。</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
潜在的优点：</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
1.当leader发生变化时，更容易集中到一个地方做调试(排除故障)。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
2.当leader发生变化时，ZK可以把读取/写状态信息成批广播到其他broker，因此当leader failover的时候会减少broker之间恢复的延迟时间。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
3.需要更少的监听器。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
4.使用更高效的RPC通信方式，代替在zookeeper中队列实现方式。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
潜在的缺点：</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
需要考虑controller failover</p>
<h2 id="kafkareplication设计机制-zookeeper中路径列表说明" style="margin:30px 0px 0px; padding:0px; font-size:20px; font-weight:normal; line-height:1.5; border-bottom-color:rgb(46,61,84); font-family:Arial,sans-serif">
<a target="_blank" name="t3" style="color:rgb(255,153,0)"></a>zookeeper中路径列表说明</h2>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
1.Controller path:存储当前controller信息.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
</p>
<pre><code class="language-java">/controller --&gt; {brokerid} (ephemeral; created by controller)</code></pre>
<p></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
2.Broker path:存储当前所有活着的brokers信息。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
</p>
<pre><code class="language-java">/brokers/ids/[broker_id] --&gt; host:port (ephemeral; created by admin)</code></pre>
<p></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
3.存储一个主题的所有分区副本任务。对于每一个副本，我们存储的副本指派一个broker ID。第一个副本是首选的复制品。注意，对于一个给定的分区，在一个broker上有至多一个副本。因此，broker ID可以作副本标识.</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
</p>
<pre><code class="language-java">/brokers/topics/[topic]/[partition_id]/leaderAndISR --&gt; {leader_epoc: epoc, leader: broker_id, ISR: {broker1, broker2}}
此路径被controller或leader修改，当前leader只修改ISR一部分信息。当更新path需要使用条件同步到zookeeper上。</code></pre>
<p></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
4.<span style="color:rgb(0,0,0)">LeaderAndISR path:存储一个分区leader and ISR</span></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
<span style="color:rgb(0,0,0)"></span></p>
<pre><code class="language-java">/brokers/topics/[topic]/[partition_id]/leaderAndISR --&gt; {leader_epoc: epoc, leader: broker_id, ISR: {broker1, broker2}}
此路径被controller或leader修改，当前leader只修改ISR一部分信息。当更新path需要使用条件同步到zookeeper上。</code></pre>5.分区分配path：当我们重新分配某些分区到不同的brokers时，此path会被使用。对于每个分区重新分配，他将会存储一个新副本列表和他们相应的brokers信息。
<p></p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
每当某个管理员操作如下命令成功后，且这个分区迁移到目标broker成功后，源broker上的分区会自动删除。</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
</p>
<pre><code class="language-java">/admin/partitions_add/[topic]/[partition_id] --&gt; {broker_id …} (created by admin)
/admin/partitions_remove/[topic]/[partition_id] (created by admin)</code></pre>
<p></p>
<h2 id="kafkareplication设计机制-kafka中专有词语解释：" style="margin:30px 0px 0px; padding:0px; font-size:20px; font-weight:normal; line-height:1.5; border-bottom-color:rgb(46,61,84); font-family:Arial,sans-serif">
<a target="_blank" name="t4" style="color:rgb(255,153,0)"></a>kafka中专有词语解释：</h2>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
AR(assign replicas):分配副本  ISR(in-sync replicas)：在同步中的副本</p>
<p style="margin-top:10px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-size:14px; color:rgb(51,51,51); font-family:Arial,sans-serif; line-height:20px">
</p>
<pre><code class="language-java">Replica {                                // 一个分区副本信息
  broker_id               : int
  partition               : Partition    //分区信息
  log                     : Log          //本地日志与副本关联信息
  hw                      : long         //最后被commit的message的offset信息
  leo                     : long         // 日志结尾offset
  isLeader                : Boolean      //是否为该副本的leader
}
  
Partition {                              //topic名称
  topic                   : string
  partition_id            : int
  leader                  : Replica      // 这个分区的leader副本
  ISR                     : Set[Replica] // 正在同步中的副本集合
  AR                      : Set[Replica] // 这个分区的所有副本分配集合
  LeaderAndISRVersionInZK : long         // version id of the LeaderAndISR path; used for conditionally update the LeaderAndISR path in ZK
}
  
LeaderAndISRRequest {
  request_type_id         : int16 // 当前request的版本
  version_id              : int16 // request的版本号
  client_id               : int32 // this can be the broker id of the controller
  ack_timeout             : int32 // the time in ms to wait for a response
  isInit                  : byte  // whether this is the first command issued by a controller
  leaderAndISRMap         : Map[(topic: String, partitionId: int32) =&gt; LeaderAndISR) // a map of LeaderAndISR
}
  
LeaderAndISR {
  leader                  : int32          // leader的broker编号
  leaderEpoc              : int32          // leader epoc, incremented on each leadership change
  ISR                     : Set[int32]     // 所有在ISR复制副本的broker集合
  zkVersion               : int64          // version of the LeaderAndISR path in ZK
}
  
LeaderAndISRResponse {
  version_id              : int16 // 当前request的版本
  responseMap             : Map[(topic: String, partitionId: int32) =&gt; int16) // error code表
}
  
StopReplicaRequest {
  request_type_id         : int16 // request id
  version_id              : int16 // 当前request的版本
  client_id               : int32 // this can be the broker id of the controller
  ack_timeout             : int32 // ack响应时间，单位为毫秒
  stopReplicaSet          : Set[(topic: String, partitionId: int)) // 需要停止的分区集合
}
  
StopReplicaResponse {
  version_id              : int16 // 当前request的版本
  responseMap             : Map[(topic: String, partitionId: int32) =&gt; int16) //error code表
}</code></pre><br>
<p></p>
<p><strong><span style="font-size:24px; color:#ff0000">5）apache kafka监控系列-监控指标</span></strong></p>
<p></p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><strong>1、监控目标</strong></h2>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a><span style="font-size:12px">    1.当系统可能或处于亚健康状态时及时提醒，预防故障发生</span></h2>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t4" style="color:rgb(255,153,0)"></a><span style="font-size:12px">    2.报警提示 a.短信方式 b.邮件</span></h2>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t5" style="color:rgb(255,153,0)"></a>2、监控内容</h2>
<p></p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong>2.1 机器监控</strong></p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
Kafka服务器指标</p>
<ol class="ol1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li2">CPU Load</li><li class="li2">Disk IO</li><li class="li2">Memory</li><li class="li2">磁盘log.dirs目录下数据文件大小,要有定时清除策略</li></ol>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong><span style="font-size:18px">2.2 JVM监控</span></strong></p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
主要监控JAVA的 GC time(垃圾回收时间)，JAVA的垃圾回收机制对性能的影响比较明显</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong>2.3 Kafka系统监控</strong></p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">1、Kafka总体监控</span></p>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li2">zookeeper上/XXX/broker/ids目录下节点数量</li><li class="li2">leader 选举频率</li></ul>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">2、Kafka Broker监控</span></p>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li2"><span style="font-size:12px">kafka集群中Broker列表,broker运行状况,包括node下线，活跃数量</span></li><li class="li2"><span style="font-size:12px">Broker是否提供服务</span></li><li class="li2"><span style="font-size:12px">数据流量  流入速度，流出速度 (message / byte)</span></li><li class="li2"><span style="font-size:12px">ISR 收缩频率</span></li></ul>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">3、Kafka Controller监控</span></p>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li2">controller存活数目</li></ul>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
4、Kafka Producer监控</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<ul style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li>producer数量，排队情况</li><li>请求响应时间</li><li>QPS/分钟</li></ul>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">5、Kafka Consumer监控</span></p>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li2">consumer队列中排队请求数</li><li class="li2">请求响应时间</li><li class="li2">最近一分钟平均每秒请求数</li></ul>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">6、Topic监控</span></p>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li2">数据量大小；</li><li class="li2">offset</li><li class="li2">数据流量 流入速度，流出速度 (message / byte)</li></ul>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">3.监控指标</span></p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t6" style="color:rgb(255,153,0)"></a><span style="font-size:14px">3.1 JVM监控</span></h2>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t7" style="color:rgb(255,153,0)"></a><span style="font-size:12px; font-weight:normal"><span style="white-space:pre"></span>a.通过JMX获取GC time</span></h2>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t8" style="color:rgb(255,153,0)"></a><span style="font-weight:normal; font-size:12px; white-space:pre"></span><span style="font-weight:normal; font-size:12px">b.jvm
 full gc次数</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-size:12px">        c.通过jmx监控kafka相关参数</span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-size:12px"><br>
</span></div>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong>3.2 kafka系统监控</strong></p>
<p class="p5" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong>监控数据获取方式</strong></p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
1、生存节点信息可以从zookeeper获取</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
2、除生存节点 和 </p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="white-space:pre"></span>a、Broker是否提供服务。</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="white-space:pre"></span>b、Topic数据量大小，</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="white-space:pre"></span>c、Topic的offset 外，其他数据都可以通过JMX获取</p>
<br>
<strong><span style="font-size:24px; color:#ff0000">6）kafka.common.ConsumerRebalanceFailedException异常解决办法</span></strong>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(255,102,102)">kafka.common.ConsumerRebalanceFailedException :log-push-record-consumer-group_mobile-pushremind02.lf.xxx.com-1399456594831-99f15e63 can't rebalance after 3 retries</span></p>
<span style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; color:rgb(255,102,102)"><span style="white-space:pre"></span>at kafka.consumer.ZookeeperConsumerConnector$ZKRebalancerListener.syncedRebalance(Unknown Source)<br>
<span style="white-space:pre"></span>at kafka.consumer.ZookeeperConsumerConnector.kafka$consumer$ZookeeperConsumerConnector$$reinitializeConsumer(Unknown Source)<br>
<span style="white-space:pre"></span>at kafka.consumer.ZookeeperConsumerConnector.consume(Unknown Source)<br>
<span style="white-space:pre"></span>at kafka.javaapi.consumer.ZookeeperConsumerConnector.createMessageStreams(Unknown Source)<br>
<span style="white-space:pre"></span>at com.xxx.mafka.client.consumer.DefaultConsumerProcessor.getKafkaStreams(DefaultConsumerProcessor.java:149)<br>
<span style="white-space:pre"></span>at com.xxx.mafka.client.consumer.DefaultConsumerProcessor.recvMessage(DefaultConsumerProcessor.java:63)<br>
<span style="white-space:pre"></span>at com.xxx.service.mobile.push.kafka.MafkaPushRecordConsumer.main(MafkaPushRecordConsumer.java:22)<br>
</span><span style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"></span>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(255,102,102)"><span style="white-space:pre"></span>at com.xxx.service.mobile.push.Bootstrap.main(Bootstrap.java:34)</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(255,102,102)"><br>
</span></p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t2" style="color:rgb(255,153,0)"></a>出现以上问题原因分析：</h2>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
同一个消费者组(consumer group)有多个consumer先后启动，就是一个消费者组内有多个consumer同时负载消费多个partition数据.</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
解决办法：</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
1.配置zk问题(kafka的consumer配置)</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,102,0)"><strong>zookeeper.session.timeout.ms=5000</strong></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,102,0)"><strong>zookeeper.connection.timeout.ms=10000</strong></span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(255,0,0)"><strong>zookeeper.sync.time.ms=2000</strong></span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,102,0)"><strong><br>
</strong></span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)">在使用高级API过程中，一般出现这个问题是zookeeper.sync.time.ms时间间隔配置过短，不排除有其他原因引起，但笔者遇到一般是这个原因。</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)">给大家解释一下原因：一个消费者组中(consumer数量&lt;partitions数量)每当有consumer发送变化，会触发负载均衡。第一件事就是释放当consumer资源</span><span style="color:rgb(51,102,255)">，无则免之，调用ConsumerFetcherThread关闭并释放当前kafka broker所有连接，释放当前消费的partitons，实际就是删除临时节点(/xxx/consumer/owners/topic-xxx/partitions[0-n]),所有同一个consumer
 group内所有consumer通过计算获取本consumer要消费的partitions，然后本consumer注册相应临时节点卡位，代表我拥有该partition的消费所有权，其他consumer不能使用。</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)"><br>
</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)">如果大家理解上面解释，下面就更容易了，当consumer调用Rebalance时，它是按照时间间隔和最大次数采取<span style="font-size:13.63636302948px">失败</span>重试原则，每当获取partitions失败后会重试获取。举个例子，假如某个公司有个会议，B部门在某个时间段预订该会议室，但是时间到了去会议室看时，发现A部门还在使用。这时B部门只有等待了，每隔一段时间去询问一下。如果时间过于频繁，则会议室一直会处于占用状态，如果时间间隔设置长点，可能去个2次，A部门就让出来了。</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)"><br>
</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)">同理，当新consumer加入重新触发rebalance时，已有(</span><span style="color:rgb(255,0,0)">old</span><span style="color:rgb(51,102,255)">)的consumer会重新计算并释放占用partitions，但是会消耗一定处理时间，此时新(</span><span style="color:rgb(255,0,0)">new</span><span style="color:rgb(51,102,255)">)consumer去抢占该partitions很有可能就会失败。我们假设设置足够old
 consumer释放资源的时间，就不会出现这个问题。</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)"><br>
</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px; color:rgb(0,153,0)">zookeeper.sync.time.ms时间设置过短就会导致</span><span style="font-size:18px; color:rgb(0,153,0)">old consumer还没有来得及释放资源，new consumer重试失败多次到达阀值就退出了。</span><br>
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px; color:rgb(0,153,0)"><br>
</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px; color:rgb(0,153,0)"><span style="font-size:18.1818180084229px">zookeeper.sync.time.ms设置时间阀值，要考虑网络环境，服务器性能等因素在内综合衡量。</span><br>
</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px; color:rgb(0,102,0)"><strong><br>
</strong></span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,102,0)"><span style="font-weight:bold">kafka zk节点存储，请参考：<span style="font-family:'Microsoft YaHei'; color:rgb(51,51,51)"><span style="line-height:30px"><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/23744675" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">kafka在zookeeper中存储结构</a></span></span></span></span></p>
<br>
<p><span style="font-size:24px; color:#ff0000"><strong>7）kafak安装与使用</strong></span></p>
<p></p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px">kafak安装与使用</h1>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a>1.前言</h2>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
学习kafka的基础是先把kafka系统部署起来，然后简单的使用它，从直观上感觉它，然后逐步的深入了解它。<br>
本文介绍了kafka部署方法，包括配置，安装和简单的使用。<br>
</p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t4" style="color:rgb(255,153,0)"></a>2.kafka下载和安装</h2>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
kafka版本一直在更新，且每次更新，变化均比较大，如配置文件有改动，kafka 0.7到0.8.1版本变化很大，包括加入，支持集群内复制，支持多个数据目录，请求处理改为异步，实现partition动态管理，基于时间的日志段删除<br>
</p>
<h3 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t5" style="color:rgb(255,153,0)"></a>2.1下载地址：</h3>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
https://www.apache.org/dyn/closer.cgi?path=/kafka/0.8.1.1/kafka_2.10-0.8.1.1.tgz。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
kafka目录结构</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
如 图-1</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140504170822953" alt="" style="border:none; max-width:100%"><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
说明:涂黑部分为我自己创建文件夹</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<table cellspacing="0" cellpadding="0" style="color:rgb(0,0,0); font-family:Arial; font-size:14.3999996185303px; line-height:26px; border-collapse:collapse">
<tbody>
<tr>
<td valign="top" style="width:63px; height:9px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">目录</span></p>
</td>
<td valign="top" style="width:469px; height:9px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">说明</span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:63px; height:11px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">bin</span></p>
</td>
<td valign="top" style="width:469px; height:11px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">操作</span><span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">kafka</span><span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">的可执行脚本，还包含</span><span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">windows</span><span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">下脚本</span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:63px; height:12px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">config</span></p>
</td>
<td valign="top" style="width:469px; height:12px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">配置文件所在目录</span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:63px; height:11px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">libs</span></p>
</td>
<td valign="top" style="width:469px; height:11px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">依赖库目录</span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:63px; height:11px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">logs</span></p>
</td>
<td valign="top" style="width:469px; height:11px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">日志数据目录，目录</span><span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">kafka</span><span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">把</span><span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">server</span><span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">端日志分为</span><span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">5</span><span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">种类型，分为</span><span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">:server,request,state</span><span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">，</span><span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">log-cleaner</span><span style="font-size:10px; font-family:'Heiti SC Light'; letter-spacing:0px">，</span><span style="font-size:10px; font-family:Helvetica; letter-spacing:0px">controller</span></p>
</td>
</tr>
</tbody>
</table>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<h3 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t6" style="color:rgb(255,153,0)"></a>2.1 安装以及启动kafka</h3>
<h4 style="margin:0px; padding:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<a target="_blank" name="t7" style="color:rgb(255,153,0)"></a>步骤1：</h4>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">lizhitao@localhost:~$ tar -xzf kafka_2.10-0.8.1.1.tgz<br>
lizhitao@localhost:~$ cd kafka_2.10-0.8.1.1.tgz<br>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><br>
</div>
<h4 style="margin:0px; padding:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<a target="_blank" name="t8" style="color:rgb(255,153,0)"></a>步骤2：</h4>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"> 配置zookeeper(假设您已经安装了zookeeper,如果没有安装，请再网上搜索安装方法)</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">进入kafka安装工程根目录编辑 vim config/server.properties  修改属性zookeeper.connect=ip:8081,ip2:8082</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><br>
</div>
<h4 style="margin:0px; padding:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<a target="_blank" name="t9" style="color:rgb(255,153,0)"></a>步骤3：</h4>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">kafka最为重要三个配置依次为：broker.id、log.dir、zookeeper.connect</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">kafka server端config/server.properties参数说明和解释如下:</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/25667831" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">server.properties配置属性说明</a><br>
<pre style="white-space:pre-wrap; word-wrap:break-word; font-size:17px; font-family:'courier new',courier,monospace; color:rgb(51,51,51); background-color:rgb(255,255,255)"></pre>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">根据属性说明完成配置</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">broker.id = 1</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">port = 9092</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"></div>
<h4 style="margin:0px; padding:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<a target="_blank" name="t10" style="color:rgb(255,153,0)"></a>步骤4： 启动服务</h4>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">cd kafka-0.8.1</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
lizhitao@localhost:~$ bin/kafka-server-start.sh config/server.properties</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
[2014-04-16 15:01:47,028] INFO Verifying properties (kafka.utils.VerifiableProperties)</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
[2014-04-16 15:01:47,051] INFO Property socket.send.buffer.bytes is overridden to 1048576 (kafka.utils.VerifiableProperties)</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
...</p>
<h4 style="margin:0px; padding:0px"><a target="_blank" name="t11" style="color:rgb(255,153,0)"></a>步骤5：创建topic</h4>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong>lizhitao@localhost:~$ bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test</strong></p>
<h4 style="margin:0px; padding:0px"><a target="_blank" name="t12" style="color:rgb(255,153,0)"></a>步骤6：验证topic是否创建成功</h4>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong>lizhitao@localhost:~$ bin/kafka-topics.sh --list --zookeeper localhost:2181</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
test</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
Alternatively, instead of manually creating topics you can also configure your brokers to auto-create topics when a non-existent topic is published to.</p>
步骤7：发送一些消息验证，在console模式下，启动producer
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong>bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong>This is a message</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong>This is another message</strong></p>
步骤7:启动一个consumer
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong>lizhitao@localhost:~$ bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic test --from-beginning</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
This is a message</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
This is another message</p>
<h2 style="margin:0px; padding:0px"><a target="_blank" name="t13" style="color:rgb(255,153,0)"></a>3.配置kafka集群模式，需要由多个broker组成</h2>
<h3 style="margin:0px; padding:0px"><a target="_blank" name="t14" style="color:rgb(255,153,0)"></a>步骤1：</h3>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong>因为需要在同一个目录（config）下配置多个server.properties，操作步骤如下：</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong></strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-weight:bold">lizhitao@localhost:~$ </span><strong>cp config/server.properties config/server-1.properties</strong> </p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong></strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; display:inline!important">
<span style="font-weight:bold">lizhitao@localhost:~$ </span>cp config/server.properties config/server-2.properties</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong></strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; display:inline!important">
</p>
<h3 style="margin:0px; padding:0px"><a target="_blank" name="t15" style="color:rgb(255,153,0)"></a>步骤2：</h3>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
需要编辑并设置如下文件属性：</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
config/server-1.properties:</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
    broker.id=1</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
    port=9093</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
    log.dir=/tmp/kafka-logs-1</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
 </p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
config/server-2.properties:</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
    broker.id=2</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
    port=9094</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
    log.dir=/tmp/kafka-logs-2</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong></strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
启动服务</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-weight:bold">lizhitao@localhost:~$ </span><strong>bin/kafka-server-start.sh config/server-1.properties &amp;</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
...</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-weight:bold">lizhitao@localhost:~$ </span><strong>bin/kafka-server-start.sh config/server-2.properties &amp;</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
...</p>
<h3 style="margin:0px; padding:0px"><a target="_blank" name="t16" style="color:rgb(255,153,0)"></a>步骤3：</h3>
创建topic
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong>lizhitao@localhost:~$ bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 3 --partitions 1 --topic my-replicated-topic</strong></p>
.....
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
topic created success....</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
<strong>lizhitao@localhost:~$ bin/kafka-topics.sh --describe --zookeeper localhost:2181 --topic my-replicated-topic</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
Topic:my-replicated-topic     PartitionCount:1    ReplicationFactor:3Configs:</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
Topic: my-replicated-topic     Partition: 0Leader: 1Replicas: 1,2,0Isr: 1,2,0</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
描述topic中分区，同步副本情况</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
<strong>lizhitao@localhost:~$ bin/kafka-topics.sh --describe --zookeeper localhost:2181 --topic test</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
Topic:test PartitionCount:1 ReplicationFactor:1Configs:</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
Topic: test Partition: 0 Leader: 0Replicas: 0Isr: 0</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
</p>
<h3 style="margin:0px; padding:0px"><a target="_blank" name="t17" style="color:rgb(255,153,0)"></a>步骤4：作为生产者发送消息</h3>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
<strong>lizhitao@localhost:~$ bin/kafka-console-producer.sh --broker-list localhost:9092 --topic my-replicated-topic</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
...</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
my test message 1</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
my test message 2</p>
<h3 style="margin:0px; padding:0px"><a target="_blank" name="t18" style="color:rgb(255,153,0)"></a><strong>步骤5：消费topic数据</strong></h3>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
<strong>lizhitao@localhost:~$ bin/kafka-console-consumer.sh --zookeeper localhost:2181 --from-beginning --topic my-replicated-topic</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
...</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
my test message 1</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
my test message 2</p>
<h3 style="margin:0px; padding:0px"><a target="_blank" name="t19" style="color:rgb(255,153,0)"></a>步骤6：</h3>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
检查consumer offset位置</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-weight:bold">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong>lizhitao@localhost:~$ bin/kafka-run-class.sh kafka.tools.ConsumerOffsetChecker --zkconnect localhost:2181 --group test</strong></p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
Group           Topic                          Pid Offset          logSize         Lag             Owner</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
my-group        my-topic                       0   0               0               0               test_jkreps-mn-1394154511599-60744496-0</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
my-group        my-topic                       1   0               0               0               test_jkreps-mn-1394154521217-1a0be913-0</p>
</div>
<span style="font-size:24px; color:#ff0000"><strong>8）apache kafka中server.properties配置文件参数说明</strong></span>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
每个kafka broker中配置文件server.properties默认必须配置的属性如下：</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/25667831#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/25667831#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/341853" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/341853/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:564px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">broker.id=</span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">num.network.threads=<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">2</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">num.io.threads=<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">8</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">socket.send.buffer.bytes=<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1048576</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">socket.receive.buffer.bytes=<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1048576</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">socket.request.max.bytes=<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">104857600</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log.dirs=/tmp/kafka-logs  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">num.partitions=<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">2</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log.retention.hours=<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">168</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log.segment.bytes=<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">536870912</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log.retention.check.interval.ms=<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">60000</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">log.cleaner.enable=<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">zookeeper.connect=localhost:<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">2181</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">zookeeper.connection.timeout.ms=<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1000000</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li></ol>
</div>
<br style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">server.properties中所有配置参数说明(解释)如下列表：</span><br style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<table cellspacing="0" cellpadding="0" style="color:rgb(0,0,0); font-family:Arial; font-size:14.3999996185303px; line-height:26px; border-collapse:collapse">
<tbody>
<tr>
<td valign="top" style="width:175px; height:12px; border-style:solid; border-width:1px; border-color:rgb(33,33,33) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Heiti SC Light'; letter-spacing:0px"><span style="font-size:14px">参数</span></span></p>
</td>
<td valign="top" style="width:381px; height:12px; border-style:solid; border-width:1px; border-color:rgb(33,33,33) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">说明</span><span style="font-family:Helvetica; letter-spacing:0px">(</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">解释</span><span style="font-family:Helvetica; letter-spacing:0px">)</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:28px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">broker.id =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">0</span></span></p>
</td>
<td valign="top" style="width:381px; height:28px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">每一个</span><span style="font-family:'Courier New'; letter-spacing:0px">broker</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">在集群中的唯一表示，要求是正数。当该服务器的</span><span style="font-family:'Courier New'; letter-spacing:0px">IP</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">地址发生改变时，</span><span style="font-family:'Courier New'; letter-spacing:0px">broker.id</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">没有变化，则不会影响</span><span style="font-family:'Courier New'; letter-spacing:0px">consumers</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的消息情况</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Courier New'; letter-spacing:0px"><span style="font-size:14px">log.dirs=/data/kafka-logs</span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">kafka</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">数据的存放地址，多个地址的话用逗号分割,多个目录分布在不同磁盘上可以提高读写性能  </span><span style="font-family:'Courier New'; letter-spacing:0px">/data/kafka-logs-</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，</span><span style="font-family:'Courier New'; letter-spacing:0px">/data/kafka-logs-</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">2</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:15px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">port =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">9092</span></span></p>
</td>
<td valign="top" style="width:381px; height:15px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:Helvetica; letter-spacing:0px">broker server</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">服务端口</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">message.max.bytes =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">6525000</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Heiti SC Light'; letter-spacing:0px"><span style="font-size:14px">表示消息体的最大大小，单位是字节</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">num.network.threads =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">4</span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">broker</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">处理消息的最大线程数，一般情况下不需要去修改</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:15px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">num.io.threads =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">8</span></span></p>
</td>
<td valign="top" style="width:381px; height:15px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">broker</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">处理磁盘</span><span style="font-family:'Courier New'; letter-spacing:0px">IO</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的线程数</span><span style="font-family:'Courier New'; letter-spacing:0px"></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，数值应该大于你的硬盘数</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">background.threads =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">4</span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Heiti SC Light'; letter-spacing:0px"><span style="font-size:14px">一些后台任务处理的线程数，例如过期消息文件的删除等，一般情况下不需要去做修改</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:43px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">queued.max.requests =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">500</span></span></p>
</td>
<td valign="top" style="width:381px; height:43px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">等待</span><span style="font-family:'Courier New'; letter-spacing:0px">IO</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">线程处理的请求队列最大数，若是等待</span><span style="font-family:'Courier New'; letter-spacing:0px">IO</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的请求超过这个数值，那么会停止接受外部消息，应该是一种自我保护机制。</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:46px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Courier New'; letter-spacing:0px"><span style="font-size:14px">host.name</span></span></p>
</td>
<td valign="top" style="width:381px; height:46px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">broker</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的主机地址，若是设置了，那么会绑定到这个地址上，若是没有，会绑定到所有的接口上，并将其中之一发送到</span><span style="font-family:'Courier New'; letter-spacing:0px">ZK</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，一般不设置</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">socket.send.buffer.bytes=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">100</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">socket</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的发送缓冲区，</span><span style="font-family:'Courier New'; letter-spacing:0px">socket</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的调优参数</span><span style="font-family:'Courier New'; letter-spacing:0px">SO_SNDBUFF</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">socket.receive.buffer.bytes =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">100</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">socket</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的接受缓冲区，</span><span style="font-family:'Courier New'; letter-spacing:0px">socket</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的调优参数</span><span style="font-family:'Courier New'; letter-spacing:0px">SO_RCVBUFF</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:63px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">socket.request.max.bytes =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">100</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span></span></p>
</td>
<td valign="top" style="width:381px; height:63px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">socket</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">请求的最大数值，防止</span><span style="font-family:'Courier New'; letter-spacing:0px">serverOOM</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，</span><span style="font-family:'Courier New'; letter-spacing:0px">message.max.bytes</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">必然要小于</span><span style="font-family:'Courier New'; letter-spacing:0px">socket.request.max.bytes</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，会被</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">创建时的指定参数覆盖</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.segment.bytes =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的分区是以一堆</span><span style="font-family:'Courier New'; letter-spacing:0px">segment</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">文件存储的，这个控制每个</span><span style="font-family:'Courier New'; letter-spacing:0px">segment</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的大小，会被</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">创建时的指定参数覆盖</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:46px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.roll.hours =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">24</span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">7</span></span></p>
</td>
<td valign="top" style="width:381px; height:46px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">这个参数会在日志</span><span style="font-family:'Courier New'; letter-spacing:0px">segment</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">没有达到</span><span style="font-family:'Courier New'; letter-spacing:0px">log.segment.bytes</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">设置的大小，也会强制新建一个</span><span style="font-family:'Courier New'; letter-spacing:0px">segment</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">会被</span><span style="font-family:'Courier New'; letter-spacing:0px"> topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">创建时的指定参数覆盖</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:46px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Courier New'; letter-spacing:0px"><span style="font-size:14px">log.cleanup.policy = delete</span></span></p>
</td>
<td valign="top" style="width:381px; height:46px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">日志清理策略</span><span style="font-family:'Courier New'; letter-spacing:0px"></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">选择有：</span><span style="font-family:'Courier New'; letter-spacing:0px">delete</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">和</span><span style="font-family:'Courier New'; letter-spacing:0px">compact</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">主要针对过期数据的处理，或是日志文件达到限制的额度，会被</span><span style="font-family:'Courier New'; letter-spacing:0px"> topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">创建时的指定参数覆盖</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:92px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.retention.minutes=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">3</span><span style="font-family:'Courier New'; letter-spacing:0px">days</span></span></p>
</td>
<td valign="top" style="width:381px; height:92px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">数据存储的最大时间</span><span style="font-family:'Courier New'; letter-spacing:0px"></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">超过这个时间</span><span style="font-family:'Courier New'; letter-spacing:0px"></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">会根据</span><span style="font-family:'Courier New'; letter-spacing:0px">log.cleanup.policy</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">设置的策略处理数据，也就是消费端能够多久去消费数据</span></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.retention.bytes</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">和</span><span style="font-family:'Courier New'; letter-spacing:0px">log.retention.minutes</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">任意一个达到要求，都会执行删除，会被</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">创建时的指定参数覆盖</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:79px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.retention.bytes=-</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1</span></span></p>
</td>
<td valign="top" style="width:381px; height:79px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">每个分区的最大文件大小，一个</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的大小限制</span><span style="font-family:'Courier New'; letter-spacing:0px"> = </span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">分区数</span><span style="font-family:'Courier New'; letter-spacing:0px">*log.retention.bytes</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">。</span><span style="font-family:'Courier New'; letter-spacing:0px">-</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">没有大小限</span><span style="font-family:'Courier New'; letter-spacing:0px">log.retention.bytes</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">和</span><span style="font-family:'Courier New'; letter-spacing:0px">log.retention.minutes</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">任意一个达到要求，都会执行删除，会被</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">创建时的指定参数覆盖</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.retention.check.interval.ms=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">5</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">minutes</span></span></p>
</td>
<td valign="top" style="width:381px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">文件大小检查的周期时间，是否处罚</span><span style="font-family:'Courier New'; letter-spacing:0px"> log.cleanup.policy</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">中设置的策略</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.cleaner.enable=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,102,153)"><strong>false</strong></span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Heiti SC Light'; letter-spacing:0px"><span style="font-size:14px">是否开启日志压缩</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.cleaner.threads =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)"> 2</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Heiti SC Light'; letter-spacing:0px"><span style="font-size:14px">日志压缩运行的线程数</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Courier New'; letter-spacing:0px"><span style="font-size:14px">log.cleaner.io.max.bytes.per.second=None</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Heiti SC Light'; letter-spacing:0px"><span style="font-size:14px">日志压缩时候处理的最大大小</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:48px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.cleaner.dedupe.buffer.size=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">500</span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span></span></p>
</td>
<td valign="top" style="width:381px; height:48px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">日志压缩去重时候的缓存空间</span><span style="font-family:'Courier New'; letter-spacing:0px"></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，在空间允许的情况下，越大越好</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.cleaner.io.buffer.size=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">512</span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">日志清理时候用到的</span><span style="font-family:'Courier New'; letter-spacing:0px">IO</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">块大小</span><span style="font-family:'Courier New'; letter-spacing:0px"></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">一般不需要修改</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.cleaner.io.buffer.load.factor =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">0.9</span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">日志清理中</span><span style="font-family:'Courier New'; letter-spacing:0px">hash</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">表的扩大因子</span><span style="font-family:'Courier New'; letter-spacing:0px"></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">一般不需要修改</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.cleaner.backoff.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">15000</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Heiti SC Light'; letter-spacing:0px"><span style="font-size:14px">检查是否处罚日志清理的间隔</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.cleaner.min.cleanable.ratio=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">0.5</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">日志清理的频率控制，越大意味着更高效的清理，同时会存在一些空间上的浪费，会被</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">创建时的指定参数覆盖</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:60px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.cleaner.delete.retention.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">day</span></span></p>
</td>
<td valign="top" style="width:381px; height:60px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">对于压缩的日志保留的最长时间，也是客户端消费消息的最长时间，同</span><span style="font-family:'Courier New'; letter-spacing:0px">log.retention.minutes</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的区别在于一个控制未压缩数据，一个控制压缩后的数据。会被</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">创建时的指定参数覆盖</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.index.size.max.bytes =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">10</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span></span></p>
</td>
<td valign="top" style="width:381px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">对于</span><span style="font-family:'Courier New'; letter-spacing:0px">segment</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">日志的索引文件大小限制，会被</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">创建时的指定参数覆盖</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:46px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.index.interval.bytes =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">4096</span></span></p>
</td>
<td valign="top" style="width:381px; height:46px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">当执行一个</span><span style="font-family:'Courier New'; letter-spacing:0px">fetch</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">操作后，需要一定的空间来扫描最近的</span><span style="font-family:'Courier New'; letter-spacing:0px">offset</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">大小，设置越大，代表扫描速度越快，但是也更好内存，一般情况下不需要搭理这个参数</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:114px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Courier New'; letter-spacing:0px"><span style="font-size:14px">log.flush.interval.messages=None</span></span></p>
</td>
<td valign="top" style="width:381px; height:114px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">文件</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(255,38,0)">”sync”</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">到磁盘之前累积的消息条数</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">因为磁盘</span><span style="font-family:'Courier New'; letter-spacing:0px">IO</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">操作是一个慢操作</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">但又是一个</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(255,38,0)">”</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px; color:rgb(255,38,0)">数据可靠性</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(255,38,0)">"</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的必要手段</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">所以此参数的设置</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">需要在</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(255,38,0)"><strong>"</strong></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px; color:rgb(255,38,0)"><strong>数据可靠性</strong></span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(255,38,0)"><strong>"</strong></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">与</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(200,37,6)">"</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px; color:rgb(200,37,6)">性能</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(200,37,6)">"</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">之间做必要的权衡</span><span style="font-family:'Courier New'; letter-spacing:0px">.</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">如果此值过大</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">将会导致每次</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(4,51,255)">"fsync"</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的时间较长</span><span style="font-family:'Courier New'; letter-spacing:0px">(IO</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">阻塞</span><span style="font-family:'Courier New'; letter-spacing:0px">)</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">如果此值过小</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">将会导致</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(255,38,0)"><strong>"fsync"</strong></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的次数较多</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">这也意味着整体的</span><span style="font-family:'Courier New'; letter-spacing:0px">client</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">请求有一定的延迟</span><span style="font-family:'Courier New'; letter-spacing:0px">.</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">物理</span><span style="font-family:'Courier New'; letter-spacing:0px">server</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">故障</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">将会导致没有</span><span style="font-family:'Courier New'; letter-spacing:0px">fsync</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的消息丢失</span><span style="font-family:'Courier New'; letter-spacing:0px">.</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.flush.scheduler.interval.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">3000</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Heiti SC Light'; letter-spacing:0px"><span style="font-size:14px">检查是否需要固化到硬盘的时间间隔</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:49px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Courier New'; letter-spacing:0px"><span style="font-size:14px">log.flush.interval.ms = None</span></span></p>
</td>
<td valign="top" style="width:381px; height:49px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">仅仅通过</span><span style="font-family:'Courier New'; letter-spacing:0px">interval</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">来控制消息的磁盘写入时机</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">是不足的</span><span style="font-family:'Courier New'; letter-spacing:0px">.</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">此参数用于控制</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(255,38,0)"><strong>"fsync"</strong></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的时间间隔</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">如果消息量始终没有达到阀值</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">但是离上一次磁盘同步的时间间隔达到阀值</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">也将触发</span><span style="font-family:'Courier New'; letter-spacing:0px">.</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.delete.delay.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">60000</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">文件在索引中清除后保留的时间</span><span style="font-family:'Courier New'; letter-spacing:0px"></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">一般不需要去修改</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">log.flush.offset.checkpoint.interval.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">60000</span></span></p>
</td>
<td valign="top" style="width:381px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">控制上次固化硬盘的时间点，以便于数据恢复</span><span style="font-family:'Courier New'; letter-spacing:0px"></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">一般不需要去修改</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">auto.create.topics.enable =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(4,51,255)"><strong>true</strong></span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">是否允许自动创建</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，若是</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,102,153)"><strong>false</strong></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，就需要通过命令创建</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(4,51,255)"><strong>default</strong></span><span style="font-family:'Courier New'; letter-spacing:0px">.replication.factor =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1</span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">是否允许自动创建</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，若是</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,102,153)"><strong>false</strong></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，就需要通过命令创建</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">num.partitions =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1</span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">每个</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的分区个数，若是在</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">创建时候没有指定的话</span><span style="font-family:'Courier New'; letter-spacing:0px"></span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">会被</span><span style="font-family:'Courier New'; letter-spacing:0px">topic</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">创建时的指定参数覆盖</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:15px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Helvetica; min-height:14px">
</p>
</td>
<td valign="top" style="width:381px; height:15px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Helvetica; min-height:14px">
</p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:46px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">以下是</span><span style="font-family:'Courier New'; letter-spacing:0px">kafka</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">中</span><span style="font-family:'Courier New'; letter-spacing:0px">Leader,replicas</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">配置参数</span></span></p>
</td>
<td valign="top" style="width:381px; height:46px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Helvetica; min-height:14px">
</p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">controller.socket.timeout.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">30000</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">partition leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">与</span><span style="font-family:'Courier New'; letter-spacing:0px">replicas</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">之间通讯时</span><span style="font-family:'Courier New'; letter-spacing:0px">,socket</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的超时时间</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">controller.message.queue.size=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">10</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">partition leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">与</span><span style="font-family:'Courier New'; letter-spacing:0px">replicas</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">数据同步时</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">消息的队列尺寸</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:49px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">replica.lag.time.max.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">10000</span></span></p>
</td>
<td valign="top" style="width:381px; height:49px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">replicas</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">响应</span><span style="font-family:'Courier New'; letter-spacing:0px">partition leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的最长等待时间，若是超过这个时间，就将</span><span style="font-family:'Courier New'; letter-spacing:0px">replicas</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">列入</span><span style="font-family:'Courier New'; letter-spacing:0px">ISR(in-sync
 replicas)</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，并认为它是死的，不会再加入管理中</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:146px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">replica.lag.max.messages =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">4000</span></span></p>
</td>
<td valign="top" style="width:381px; height:146px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">如果</span><span style="font-family:'Courier New'; letter-spacing:0px">follower</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">落后与</span><span style="font-family:'Courier New'; letter-spacing:0px">leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">太多</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">将会认为此</span><span style="font-family:'Courier New'; letter-spacing:0px">follower[</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">或者说</span><span style="font-family:'Courier New'; letter-spacing:0px">partition relicas]</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">已经失效</span></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">##</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">通常</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">在</span><span style="font-family:'Courier New'; letter-spacing:0px">follower</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">与</span><span style="font-family:'Courier New'; letter-spacing:0px">leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">通讯时</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">因为网络延迟或者链接断开</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">总会导致</span><span style="font-family:'Courier New'; letter-spacing:0px">replicas</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">中消息同步滞后</span></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">##</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">如果消息之后太多</span><span style="font-family:'Courier New'; letter-spacing:0px">,leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">将认为此</span><span style="font-family:'Courier New'; letter-spacing:0px">follower</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">网络延迟较大或者消息吞吐能力有限</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">将会把此</span><span style="font-family:'Courier New'; letter-spacing:0px">replicas</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">迁移</span></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">##</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">到其他</span><span style="font-family:'Courier New'; letter-spacing:0px">follower</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">中</span><span style="font-family:'Courier New'; letter-spacing:0px">.</span></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">##</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">在</span><span style="font-family:'Courier New'; letter-spacing:0px">broker</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">数量较少</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">或者网络不足的环境中</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">建议提高此值</span><span style="font-family:'Courier New'; letter-spacing:0px">.</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">replica.socket.timeout.ms=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">30</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1000</span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">follower</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">与</span><span style="font-family:'Courier New'; letter-spacing:0px">leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">之间的</span><span style="font-family:'Courier New'; letter-spacing:0px">socket</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">超时时间</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">replica.socket.receive.buffer.bytes=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">64</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span></span></p>
</td>
<td valign="top" style="width:381px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">复制时候的</span><span style="font-family:'Courier New'; letter-spacing:0px">socket</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">缓存大小</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">replica.fetch.max.bytes =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(85,85,85)"></span><span style="font-family:'Courier New'; letter-spacing:0px">*</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1024</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">replicas</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">每次获取数据的最大大小</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">replica.fetch.wait.max.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">500</span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">replicas</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">同</span><span style="font-family:'Courier New'; letter-spacing:0px">leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">之间通信的最大等待时间，失败了会重试</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">replica.fetch.min.bytes =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">fetch</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的最小数据尺寸</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">如果</span><span style="font-family:'Courier New'; letter-spacing:0px">leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">中尚未同步的数据不足此值</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">将会阻塞</span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">直到满足条件</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">num.replica.fetchers=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">1</span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">进行复制的线程数，增大这个数值会增加</span><span style="font-family:'Courier New'; letter-spacing:0px">follower</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的</span><span style="font-family:'Courier New'; letter-spacing:0px">IO</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:48px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">replica.high.watermark.checkpoint.interval.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">5000</span></span></p>
</td>
<td valign="top" style="width:381px; height:48px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">每个</span><span style="font-family:'Courier New'; letter-spacing:0px">replica</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">检查是否将最高水位进行固化的频率</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">controlled.shutdown.enable =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,102,153)"><strong>false</strong></span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">是否允许控制器关闭</span><span style="font-family:'Courier New'; letter-spacing:0px">broker ,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">若是设置为</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,102,153)"><strong>true</strong></span><span style="font-family:'Courier New'; letter-spacing:0px">,</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">会关闭所有在这个</span><span style="font-family:'Courier New'; letter-spacing:0px">broker</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">上的</span><span style="font-family:'Courier New'; letter-spacing:0px">leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">，并转移到其他</span><span style="font-family:'Courier New'; letter-spacing:0px">broker</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">controlled.shutdown.max.retries =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">3</span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Heiti SC Light'; letter-spacing:0px"><span style="font-size:14px">控制器关闭的尝试次数</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">controlled.shutdown.retry.backoff.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">5000</span></span></p>
</td>
<td valign="top" style="width:381px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Heiti SC Light'; letter-spacing:0px"><span style="font-size:14px">每次关闭尝试的时间间隔</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">leader.imbalance.per.broker.percentage =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">10</span></span></p>
</td>
<td valign="top" style="width:381px; height:47px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的不平衡比例，若是超过这个数值，会对分区进行重新的平衡</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:48px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">leader.imbalance.check.interval.seconds =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">300</span></span></p>
</td>
<td valign="top" style="width:381px; height:48px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">检查</span><span style="font-family:'Courier New'; letter-spacing:0px">leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">是否不平衡的时间间隔</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:'Courier New'; letter-spacing:0px"><span style="font-size:14px">offset.metadata.max.bytes</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Heiti SC Light'; letter-spacing:0px">客户端保留</span><span style="font-family:'Courier New'; letter-spacing:0px">offset</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">信息的最大空间大小</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:29px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">kafka</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">中</span><span style="font-family:'Courier New'; letter-spacing:0px">zookeeper</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">参数配置</span></span></p>
</td>
<td valign="top" style="width:381px; height:29px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Helvetica; min-height:14px">
</p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:48px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">zookeeper.connect = localhost:</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">2181</span></span></p>
</td>
<td valign="top" style="width:381px; height:48px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">zookeeper</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">集群的地址，可以是多个，多个之间用逗号分割</span><span style="font-family:'Courier New'; letter-spacing:0px">hostname1:port1,hostname2:port2,hostname3:port3</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">zookeeper.session.timeout.ms=</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">6000</span></span></p>
</td>
<td valign="top" style="width:381px; height:32px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">ZooKeeper</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的最大超时时间，就是心跳的间隔，若是没有反映，那么认为已经死了，不易过大</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(0,0,0) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">zookeeper.connection.timeout.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">6000</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(0,0,0) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">ZooKeeper</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">的连接超时时间</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:175px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(0,0,0) rgb(33,33,33) rgb(33,33,33); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">zookeeper.sync.time.ms =</span><span style="font-family:'Courier New'; letter-spacing:0px; color:rgb(0,153,0)">2000</span></span></p>
</td>
<td valign="top" style="width:381px; height:31px; border-style:solid; border-width:1px; border-color:rgb(0,0,0) rgb(33,33,33) rgb(33,33,33) rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span style="font-family:'Courier New'; letter-spacing:0px">ZooKeeper</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">集群中</span><span style="font-family:'Courier New'; letter-spacing:0px">leader</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">和</span><span style="font-family:'Courier New'; letter-spacing:0px">follower</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">之间的同步实际那</span></span></p>
</td>
</tr>
</tbody>
</table>
<p><span style="font-size:24px; color:#ff0000"><strong>9）apache kafka的consumer初始化时获取不到消息</strong></span></p>
<p></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">问题</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
发现一个问题，如果使用的是一个高级的kafka接口 那么默认的情况下如果某个topic没有变化 则consumer消费不到消息 比如某个消息生产了2w条，此时producer不再生产消息，然后另外一个consumer启动，此时拿不到消息.</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-family:SimSun"><span style="font-size:18px">原因解释</span>：</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
auto.offset.reset：如果zookeeper没有offset值或offset值超出范围。那么就给个初始的offset。有smallest、largest、anything可选，分别表示给当前最小的offset、当前最大的offset、抛异常。默认largest</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
默认值:auto.offset.reset=largest</p>
<span style="font-size:24px; color:#ff0000"><strong>10）Kafka Producer处理逻辑</strong></span>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">Kafka Producer处理逻辑</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
Kafka Producer产生数据发送给Kafka Server，具体的分发逻辑及负载均衡逻辑，全部由producer维护。</p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t1" style="color:rgb(255,153,0)"></a>Kafka结构图</h2>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140523114111625?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center" alt="" style="border:none; max-width:100%"></p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t2" style="color:rgb(255,153,0)"></a>Kafka Producer默认调用逻辑</h2>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140523114138265" alt="" style="border:none; max-width:100%"></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
默认Partition逻辑</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong>1、没有key时的分发逻辑</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
每隔 topic.metadata.refresh.interval.ms 的时间，随机选择一个partition。这个时间窗口内的所有记录发送到这个partition。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
发送数据出错后也会重新选择一个partition</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong>2、根据key分发</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
对key求hash，然后对partition数量求模</p>
<table cellspacing="0" cellpadding="0" style="color:rgb(0,0,0); font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<tbody>
<tr>
<td valign="baseline" class="td1">
<p class="p5" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
Utils.abs(key.hashCode) % numPartitions</p>
</td>
</tr>
</tbody>
</table>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
如何获取Partition的leader信息(元数据)</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
决定好发送到哪个Partition后，需要明确该Partition的leader是哪台broker才能决定发送到哪里。</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong>具体实现位置</strong></p>
<table cellspacing="0" cellpadding="0" style="color:rgb(0,0,0); font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<tbody>
<tr>
<td valign="baseline" class="td1">
<p class="p5" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
kafka.client.ClientUtils#fetchTopicMetadata</p>
</td>
</tr>
</tbody>
</table>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong> 实现方案</strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
1、从broker获取Partition的元数据。由于Kafka所有broker存有所有的元数据，所以任何一个broker都可以返回所有的元数据</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
2、broker选取策略：将broker列表随机排序，从首个broker开始访问，如果出错，访问下一个</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
3、出错处理：出错后向下一个broker请求元数据</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong>注意</strong></p>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li1">Producer是从broker获取元数据的，并不关心zookeeper。</li><li class="li1">broker发生变化后，producer获取元数据的功能不能动态变化。</li><li class="li1">获取元数据时使用的broker列表由producer的配置中的 metadata.broker.list 决定。该列表中的机器只要有一台正常服务，producer就能获取元数据。</li><li class="li1">获取元数据后，producer可以写数据到非 metadata.broker.list 列表中的broker</li></ul>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
错误处理</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
producer的send函数默认没有返回值。出错处理有EventHandler实现。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
DefaultEventHandler的错误处理如下：</p>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li1">获取出错的数据</li><li class="li6"><span class="s1">等待一个间隔时间，由配置 </span>retry.backoff.ms 决定这段时间长短</li><li class="li6">重新获取元数据</li><li class="li6">重新发送数据</li></ul>
<p class="p6" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span class="s1">出错重试次数由配置 </span>message.send.max.retries 决定</p>
<p class="p6" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
所有重试全部失败时，DefaultEventHandler会抛出异常。代码如下</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<pre><code class="language-java">if(outstandingProduceRequests.size &gt;0) {
  producerStats.failedSendRate.mark()
  val correlationIdEnd = correlationId.get()
  error("Failed to send requests for topics %s with correlation ids in [%d,%d]"
    .format(outstandingProduceRequests.map(_.topic).toSet.mkString(","),
    correlationIdStart, correlationIdEnd-1))
  thrownewFailedToSendMessageException("Failed to send messages after "+ config.messageSendMaxRetries +" tries.",null)
}</code></pre><br>
<br>
<p><span style="font-size:24px; color:#ff0000"><strong>11）apache kafka源代码工程环境搭建(IDEA)</strong></span></p>
<p></p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px">1.<a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/26875463" rel="nofollow" style="color:rgb(0,0,0); text-decoration:none; font-family:'Microsoft YaHei'; font-size:20px; line-height:30px">gradle安装</a></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/26875463" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none"><span style="font-size:18px">gradle安装</span></a><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a>2.下载apache kafka源代码</h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><a target="_blank" href="https://archive.apache.org/dist/kafka/0.8.1/kafka-0.8.1-src.tgz" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">apache kafka下载</a><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t4" style="color:rgb(255,153,0)"></a>3.用gradle构建产生IDEA工程文件</h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="color:rgb(255,0,0)"><strong>先装好idea的scala插件，不然构建时就会自动下载，由于没有国内镜像，速度会很慢。</strong></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="color:rgb(51,102,255)">lizhitao@users-MacBook-Pro:~/Downloads/kafka_2.10-0.8.1$</span> gradle idea<br>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">如果是eclipse工程，执行:gradle eclipse</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">生成IDEA工程文件如下:</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><img src="https://img-blog.csdn.net/20140524232649546" alt="" style="border:none; max-width:100%"><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t5" style="color:rgb(255,153,0)"></a><span style="font-size:14px">4.项目导入到IDEA工程中</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">File--&gt;Open</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><img src="https://img-blog.csdn.net/20140524233201312" alt="" style="border:none; max-width:100%"><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t6" style="color:rgb(255,153,0)"></a><span style="font-size:14px">5.IDEA中查看源码工程</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><img src="https://img-blog.csdn.net/20140524233527218" alt="" style="border:none; max-width:100%"><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t7" style="color:rgb(255,153,0)"></a><span style="font-size:14px">6.Kafka启动时，参数设置</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/24991799" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none"><span style="font-family:KaiTi_GB2312; font-size:24px; color:rgb(0,102,0)">配置server.properties</span></a><br>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><img src="https://img-blog.csdn.net/20140524233845781" alt="" style="border:none; max-width:100%"><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t8" style="color:rgb(255,153,0)"></a><span style="font-size:24px">7.log4j.properties文件路径设置</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">启动kafka server很奇怪，log4j.properties文件找不到，报如下错误。</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="color:rgb(255,0,0)"><strong>log4j:WARN No appenders could be found for logger (kafka.utils.VerifiableProperties).<br>
log4j:WARN Please initialize the log4j system properly.</strong></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">只有把log4j.properties放置到src/main/scala路径下，才能找到文件,然后运行程序，正确输出日志信息。输出如下所示</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><img src="https://img-blog.csdn.net/20140524234413765" alt="" style="border:none; max-width:100%"><br>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><pre><code class="language-java">[2014-05-24 23:45:31,965] INFO Verifying properties (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,009] INFO Property broker.id is overridden to 9 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,009] INFO Property log.cleaner.enable is overridden to false (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,009] INFO Property log.dirs is overridden to /Users/lizhitao/kafka-logs (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,009] INFO Property log.retention.check.interval.ms is overridden to 60000 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,010] INFO Property log.retention.hours is overridden to 168 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,010] INFO Property log.segment.bytes is overridden to 536870912 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,010] INFO Property num.io.threads is overridden to 8 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,010] INFO Property num.network.threads is overridden to 2 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,010] INFO Property num.partitions is overridden to 2 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,010] INFO Property port is overridden to 9092 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,010] INFO Property socket.receive.buffer.bytes is overridden to 1048576 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,011] INFO Property socket.request.max.bytes is overridden to 104857600 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,011] INFO Property socket.send.buffer.bytes is overridden to 1048576 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,011] INFO Property zookeeper.connect is overridden to 192.168.2.225:2181,192.168.2.225:2182,192.168.2.225:2183 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,011] INFO Property zookeeper.connection.timeout.ms is overridden to 1000000 (kafka.utils.VerifiableProperties)  
[2014-05-24 23:45:32,032] INFO [Kafka Server 9], starting (kafka.server.KafkaServer)  
[2014-05-24 23:45:32,036] INFO [Kafka Server 9], Connecting to zookeeper on 192.168.2.225:2181,192.168.2.225:2182,192.168.2.225:2183 (kafka.server.KafkaServer)  
[2014-05-24 23:45:32,045] INFO Starting ZkClient event thread. (org.I0Itec.zkclient.ZkEventThread)  
[2014-05-24 23:45:32,370] INFO Client environment:zookeeper.version=3.3.3-1203054, built on 11/17/2011 05:47 GMT (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,370] INFO Client environment:host.name=192.168.2.104 (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,370] INFO Client environment:java.version=1.7.0_55 (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,370] INFO Client environment:java.vendor=Oracle Corporation (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,370] INFO Client environment:java.home=/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,370] INFO Client environment:java.class.path=/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/lib/ant-javafx.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/lib/dt.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/lib/javafx-doclet.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/lib/javafx-mx.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/lib/jconsole.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/lib/sa-jdi.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/lib/tools.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/charsets.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/deploy.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/htmlconverter.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/javaws.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/jce.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/jfr.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/jfxrt.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/jsse.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/management-agent.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/plugin.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/resources.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/rt.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/ext/dnsns.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/ext/localedata.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/ext/sunec.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/ext/sunjce_provider.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/ext/sunpkcs11.jar:/Library/Java/JavaVirtualMachines/jdk1.7.0_55.jdk/Contents/Home/jre/lib/ext/zipfs.jar:/Users/lizhitao/mt_wp/open_source/kafka-platform/kafka-0.8.1-src/out/production/core:/Users/lizhitao/.gradle/caches/modules-2/files-2.1/org.scala-lang/scala-library/2.8.0/95bf967bf2e0a26727736228bba3451f4dd3e5b9/scala-library-2.8.0.jar:/Users/lizhitao/.gradle/caches/modules-2/files-2.1/org.apache.zookeeper/zookeeper/3.3.4/6471e17c92181da9e143559c4c4779925a5e6eb0/zookeeper-3.3.4.jar:/Users/lizhitao/.gradle/caches/modules-2/files-2.1/com.101tec/zkclient/0.3/dedcf2b53fb742adba7080ac3aed781694ba616e/zkclient-0.3.jar:/Users/lizhitao/.gradle/caches/modules-2/files-2.1/com.yammer.metrics/metrics-core/2.2.0/f82c035cfa786d3cbec362c38c22a5f5b1bc8724/metrics-core-2.2.0.jar:/Users/lizhitao/.gradle/caches/modules-2/files-2.1/com.yammer.metrics/metrics-annotation/2.2.0/62962b54c490a95c0bb255fa93b0ddd6cc36dd4b/metrics-annotation-2.2.0.jar:/Users/lizhitao/.gradle/caches/modules-2/files-2.1/net.sf.jopt-simple/jopt-simple/3.2/d625f12ba08083c8c16dcedd5396ec730e9e77ab/jopt-simple-3.2.jar:/Users/lizhitao/.gradle/caches/modules-2/files-2.1/org.xerial.snappy/snappy-java/1.0.5/10cb4550360a0ec6b80f09a5209d00b6058e82bf/snappy-java-1.0.5.jar:/Users/lizhitao/.gradle/caches/modules-2/files-2.1/log4j/log4j/1.2.15/f0a0d2e29ed910808c33135a3a5a51bba6358f7b/log4j-1.2.15.jar:/Users/lizhitao/.gradle/caches/modules-2/files-2.1/org.slf4j/slf4j-api/1.7.2/81d61b7f33ebeab314e07de0cc596f8e858d97/slf4j-api-1.7.2.jar:/Applications/IntelliJ IDEA 12.app/lib/idea_rt.jar (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,370] INFO Client environment:java.library.path=/Users/lizhitao/Library/Java/Extensions:/Library/Java/Extensions:/Network/Library/Java/Extensions:/System/Library/Java/Extensions:/usr/lib/java:. (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,370] INFO Client environment:java.io.tmpdir=/var/folders/pn/qjf0v4k52mq965jxjd72hlx00000gp/T/ (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,370] INFO Client environment:java.compiler=&lt;NA&gt; (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,370] INFO Client environment:os.name=Mac OS X (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,370] INFO Client environment:os.arch=x86_64 (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,371] INFO Client environment:os.version=10.9.2 (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,371] INFO Client environment:user.name=lizhitao (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,371] INFO Client environment:user.home=/Users/lizhitao (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,371] INFO Client environment:user.dir=/Users/lizhitao/mt_wp/open_source/kafka-platform/kafka-0.8.1-src (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,372] INFO Initiating client connection, connectString=192.168.2.225:2181,192.168.2.225:2182,192.168.2.225:2183 sessionTimeout=6000 watcher=org.I0Itec.zkclient.ZkClient@6e739617 (org.apache.zookeeper.ZooKeeper)  
[2014-05-24 23:45:32,387] INFO Opening socket connection to server /192.168.2.225:2181 (org.apache.zookeeper.ClientCnxn)  
[2014-05-24 23:45:32,393] ERROR Unable to open socket to 192.168.2.225/192.168.2.225:2181 (org.apache.zookeeper.ClientCnxn)</code></pre></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">通过如上7步后就可以正确启动kafka程序，进行相关debug，并研究其源代码了。</div>
<br>
<p></p>
<p><span style="font-size:24px; color:#ff0000"><strong>12）apache kafka监控系列-KafkaOffsetMonitor</strong></span></p>
<p></p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><span style="font-size:14px">概览</span></h1>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
最近kafka server消息服务上线了，基于jmx指标参数也写到zabbix中了，但总觉得缺少点什么东西，可视化可操作的界面。zabbix中数据比较分散，不能集中看整个集群情况。或者一个cluster中broker列表，自己写web-console比较耗时耗力，用原型工具画了一些管理界面东西，关键自己也不前端方面技术，这方面比较薄弱。这不开源社区提供了kafka的web管理平台KafkaOffsetMonitor.就迅速拿过来运行。大家不要着急，马上娓娓道来。</p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t2" style="color:rgb(255,153,0)"></a><span style="font-size:24px">说明：</span></h2>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14px; line-height:26px">
这个应用程序来实时监控你kafka服务的consumer以及他们在partition中的offset(偏移)。 </p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14px; line-height:26px">
你可以浏览当前的消费者组，每个topic的所有partition的消费情况都可以一览无余。这其实是很有用得，从这里你很快知道每个partition的message是否很快被消费(没有阻塞)。他能指导你(kafka producer和consumer)优化代码。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14px; line-height:26px">
这个web管理平台保留的partition offset和consumer滞后的历史数据，所以你可以很轻易了解这几天consumer消费情况。 </p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a><span style="font-size:14px">KafkaOffsetMonitor功能：</span></h2>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
1.从标题都可以看出来，Kafka Offset Monitor，是对consumer消费情况进行监控,并能列出每个consumer offset,滞后数据。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
2.消费者组列表</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
3.每个topic的所有parition列表(topic,pid,offset,logSize,lag,owner)</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
4.查看topic的历史消费信息.</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
虽然功能覆盖面不全，但是很实用。</p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t4" style="color:rgb(255,153,0)"></a><span style="font-size:14px">1.下载</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">github官网下载</div>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<a target="_blank" href="https://github.com/quantifind/KafkaOffsetMonitor/releases/download/v0.2.0/KafkaOffsetMonitor-assembly-0.2.0.jar" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">KafkaOffsetMonitor</a><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
百度云下载(网速快)</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<a target="_blank" href="http://pan.baidu.com/s/1kT5KeQ7" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">百度云KafkaOffsetMonitor下载</a><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(255,0,0)"><strong>说明</strong></span>:<span style="color:rgb(51,102,255)"><strong>百度云下载为修改版本，因为KafkaOffsetMonitor中有些资源文件(css,js)是访问外网的，特别是有访问google资源，大家都懂的，经常不能访问。建议下载修改版</strong></span></p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t5" style="color:rgb(255,153,0)"></a>2.安装</h2>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
KafkaOffsetMonitor运行比较简单，因为所有运行文件，资源文件，jar文件都打包到KafkaOffsetMonitor-assembly-0.2.0.jar了，直接运行就可以，这种方式太棒了。既不用编译也不用配置，呵呵，也不是绝对不配置。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
a.新建一个目录kafka-offset-console,然后把jar拷贝到该目录下.</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
b.新建脚本，因为您可能不是一个kafka集群。用脚本可以启动多个</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
lizhitao@users-MacBook-Pro:   vim mobile_start_en.sh</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
#!/bin/bash<br>
java -Xms512M -Xmx512M -Xss1024K -XX:PermSize=256m -XX:MaxPermSize=512m -cp KafkaOffsetMonitor-assembly-0.2.0.jar \<br>
     com.quantifind.kafka.offsetapp.OffsetGetterWeb \<br>
     --zk 192.168.2.101:2181,192.168.2.102:2182,192.168.2.103:2181<strong><span style="color:rgb(255,0,0)">/config/mobile/xxx</span></strong> \               <br>
     --port 8086 \<br>
     --refresh 10.seconds \<br>
     --retain 7.days 1&gt;mobile-logs/stdout.log 2&gt;mobile-logs/stderr.log &amp;</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
注意:<strong><span style="color:rgb(255,0,0)">/config/mobile/xxx</span></strong>  表示zk的根目录,需要手工创建,也可以不设置</p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t6" style="color:rgb(255,153,0)"></a>3.运行</h2>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
lizhitao@users-MacBook-Pro:  chmod +x mobile_start_en.sh<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
lizhitao@users-MacBook-Pro:  ./mobile_start_en.sh<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
serving resources from: jar:file:/opt/xxx/kafka-offset-console/KafkaOffsetMonitor-assembly-0.2.0.jar!/offsetapp<br>
</p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t7" style="color:rgb(255,153,0)"></a><span style="font-size:14px">6 演示截图：</span></h2>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px; color:rgb(51,51,255)"><strong>消费者组列表</strong></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140527175834468?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px; color:rgb(51,51,255)"><strong>topic的所有partiton消费情况列表</strong></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px; color:rgb(51,51,255)"><strong><img src="https://img-blog.csdn.net/20140610141405750?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</strong></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px; color:rgb(51,51,255)"><strong>kafka正在运行的topic</strong></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140527180437343?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px; color:rgb(51,51,255)"><strong>kafka集群中topic列表</strong></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140527181108015?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px; color:rgb(51,51,255)">kafka集群中broker列表</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140527180940312?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</p>
<div><br>
</div>
<br>
<p><span style="font-size:24px; color:#ff0000"><strong>13）Kafka Controller设计机制</strong></span></p>
<p></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span class="s1">在kafka集群中，其中一个broker server作为中央控制器，</span>负责管理分区和副本状态并执行管理着这些分区的重新分配。下面说明如何通过中央控制器操作分区和副本的状态。</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
名词解释：</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
isr：同步副本组</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
OfflinePartitionLeaderSelector:分区下线后新的领导者选举</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
OAR：老的分配副本</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong>PartitionStateChange：</strong></p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
其有效状态如下:</p>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li1"><span class="s1">NonExistentPartition:  </span>这种状态表明该分区从来没有创建过或曾经创建过后来又删除了。</li><li class="li1">NewPartition：创建分区后,分区处于NewPartition状态。在这种状态下,分区副本应该分配给它,但还没有领导者/同步复制组。</li><li class="li1">OnlinePartition：一旦一个分区领导者被选出，就会为在线分区状态。</li><li class="li1">OfflinePartition：如果分区领导者成功选举后,当领导者分区崩溃或挂了,分区状态转变下线分区状态。</li></ul>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
其有效的状态转移如下：</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
NonExistentPartition -&gt; NewPartition</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
       1.群集中央控制器根据计算规则，从zk中读取分区信息，创建新分区和副本。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
NewPartition -&gt; OnlinePartition</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
       1.分配第一个活着的副本作为分区领导者,并且该分区所有副本作为一个同步复制组,写领导者和同步副本组数据到zk中。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
       2.对于这个分区,发送LeaderAndIsr请求给每一个副本分区和并发送UpdateMetadata请求到每个活者的broker server。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
OnlinePartition,OfflinePartition -&gt; OnlinePartition</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
       1.对于这个分区，需要选择新的领导者和同步副本组，一个副本组要接受LeaderAndIsr请求，最后写领导者和同步副本组信息到zk中。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
               a.OfflinePartitionLeaderSelector:新领导者=存活副本(最好是在isr);新isr =存活isr如果不是空或恰好为新领导者，否则;正在接受中副本=存活已分配副本。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
              b.ReassignedPartitionLeaderSelector:新领导者=存活分区重新分配副本;新isr =当前isr;正在接受中副本=重新分配副本</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span class="s2">              c.</span>PreferredReplicaPartitionLeaderSelector:新领导这=第一次分配副本(如果在isr);新isr =当前isr;接受副本=分配副本</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span class="s1">              d.</span>ControlledShutdownLeaderSelector:新领导者=当前副本在isr中且没有被关闭,新isr =当前isr -关闭副本;接受副本=存活已分配副本。</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span class="s2">     2.</span>对于这个分区,发送LeaderAndIsr请求给每一个接收副本和UpdateMetadata请求到每个broker server</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     NewPartition,OnlinePartition -&gt; OfflinePartition</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     1.这只不过标识该分区为下线状态</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     OfflinePartition -&gt; NonExistentPartition</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     1.这只不过标识该分区为不存在分区状态</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong>ReplicaStateChange:</strong></p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
有效状态如下：</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span class="s1">     1.NewReplica：</span>当创建topic或分区重新分配期间副本被创建。在这种状态下,副本只能成为追随者变更请求状态。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span class="s1">     2.OnlineReplica：</span>一旦此分区一个副本启动且部分分配副本,他将处于在线副本状态。在这种状态下,它可以成为领导者或成为跟随者状态变更请求。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span class="s1">     3.OfflineReplica：</span>每当broker server副本宕机或崩溃发生时,如果一个副本崩溃或挂了,它将变为此状态。</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     4.NonExistentReplica：<span class="s2">如果一个副本被删除了,它将变为此状态。</span></p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
有效状态转移如下:</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     NonExistentReplica - - &gt; NewReplica</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     1.使用当前领导者和isr分区发送LeaderAndIsr请求到新副本和UpdateMetadata请求给每一个存活borker</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     NewReplica - &gt; OnlineReplica</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     1.添加新的副本到副本列表中</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
      OnlineReplica,OfflineReplica - &gt; OnlineReplica</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     1.使用当前领导者和isr分区发送LeaderAndIsr请求到新副本和UpdateMetadata请求给每一个存活borker</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
      NewReplica,OnlineReplica - &gt; OfflineReplica</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     1.发送StopReplicaRequest到相应副本(w / o删除)</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
     2.从isr和发送LeaderAndIsr请求重删除此副本(isr)领导者副本和UpdateMetadata分区每个存活broker。</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span class="s2">     </span>OfflineReplica - &gt; NonExistentReplica</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
    1.发送StopReplicaRequest到副本(删除)</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong>KafkaController操作:</strong></p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
当新建topic时:</p>
<ol class="ol1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li3">调用方法onNewPartitionCreation</li></ol>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
当创建新分区时:</p>
<ol class="ol1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li3">创建新分区列表 -&gt; 调用方法NewPartition</li><li class="li3">创建所有新分区副本 -&gt; 调用方法NewReplica</li><li class="li3">新分区在线列表 -&gt; 调用方法OnlinePartition</li><li class="li3">新分区所有在线副本 -&gt; OnlineReplica</li></ol>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
当broker失败或挂掉时:</p>
<ol class="ol1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li3">当前broker所有领导者分区为下线分区 -&gt; 调用方法OfflinePartition</li><li class="li3">下线和在线分区列表 -&gt; OnlinePartition (使用下线分区领导者选举)</li><li class="li3">在broker上所有fail副本 -&gt; OfflineReplica</li></ol>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
当broker启动时:</p>
<ol class="ol1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li3">发送UpdateMetadate请求给新启动broker的所有分区。</li><li class="li3">新启动broker的分区副本-&gt; OnlineReplica</li><li class="li3">下线和在线分区列表 -&gt; OnlinePartition (使用下线分区领导者选举)</li><li class="li1">当新的broker启动时，对于所有分区副本，系统会调用方法onPartitionReassignment执行未完成的分区分配。</li></ol>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
当分区重新分配时: (OAR: 老的分配副本; RAR:每当重新分配副本会有新的副本组)</p>
<ol class="ol1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li3">用OAR + RAR副本组修改并分配副本列表.</li><li class="li3">当处于OAR + RAR时，发送LeaderAndIsr请求给每个副本。</li><li class="li3">副本处于RAR - OAR  -&gt; 调用方法NewReplica</li><li class="li3">等待直到新的副本加入isr中</li><li class="li3">副本处于RAR  -&gt; 调用方法OnlineReplica</li><li class="li3">设置AR to RAR并写到内存中</li><li class="li3">send LeaderAndIsr request 给一个潜在领导者 (如果当前领导者不在RAR中)和一个被分配的副本列表(使用RAR) 和相同sir到每个处于RAR的broker中。</li><li class="li3">replicas in OAR - RAR -&gt; Offline (强制这些副本从isr重剔除)</li><li class="li3">replicas in OAR - RAR -&gt; NonExistentReplica (强制这些副本被删除)</li><li class="li3">在zk上修改重分配副本到RAR中。</li><li class="li3">在zk上修改 /admin/reassign_partitions路径，并删除此分区</li><li class="li1">选举领导者后,副本和isr信息变化,所以重新发送更新元数据请求给每一个broker。</li></ol>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
例如, if OAR = {1, 2, 3} and RAR = {4,5,6}, 在zk上重分配副本和领导者/is<span class="s2">这些值可能经历以下转化。</span></p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
AR                  leader/isr</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
{1,2,3}            1/{1,2,3}           (初始化状态)</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
{1,2,3,4,5,6}   1/{1,2,3}           (step 2)</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
{1,2,3,4,5,6}   1/{1,2,3,4,5,6}  (step 4)</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
{1,2,3,4,5,6}   4/{1,2,3,4,5,6}  (step 7)</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
{1,2,3,4,5,6}   4/{4,5,6}           (step 8)</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
{4,5,6}            4/{4,5,6}           (step 10)</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
注意,当只有一个地方我们能存储OAR持久化数据，必须用RAR在zk修改AR节点数据,这样,如果控制器在这一步之前崩溃,我们仍然可以恢复。</p>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
当中央控制器failover时:</p>
<ol class="ol1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li3">replicaStateMachine.startup():
<ol class="ol2">
<li class="li3">从任何下线副本或上线副本中初始化每个副本</li><li class="li3">每个副本 -&gt; OnlineReplica (强制LeaderAndIsr请求发送到每个副本)</li></ol>
</li><li class="li3">partitionStateMachine.startup():
<ol class="ol2">
<li class="li3">从新建分区中初始化每个分区, 下线或上线分区</li><li class="li3">each OfflinePartition and NewPartition -&gt; OnlinePartition (强制领导者选举)</li></ol>
</li><li class="li3">恢复分区分配</li><li class="li3">恢复领导者选举</li></ol>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
当发送首选副本选举时:</p>
<ol class="ol1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li3">影响分区列表 -&gt; 调用方法OnlinePartition (with PreferredReplicaPartitionLeaderSelector)</li></ol>
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
关闭broker:</p>
<ol class="ol1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li3">在关闭broker中对于每个分区如果是领导者分区 -&gt; 调用方法OnlinePartition (ControlledShutdownPartitionLeaderSelector)</li><li class="li3">在关闭broker中每个副本是追随者,将发送StopReplica请求 (w/o deletion)</li><li class="li3">在关闭broker中每个副本是追随者 -&gt; 调用方法OfflineReplica (强制从同步副本组中删除副本)</li></ol>
<br>
<span style="font-size:24px; color:#ff0000"><strong>14）Kafka性能测试报告(虚拟机版)</strong></span>
<p></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)">测试方法</span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)">在其他虚拟机上使用 Kafka 自带 kafka-producer-perf-test.sh 脚本进行测试 Kafka 写入性能</span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)">尝试使用 kafka-simple-consumer-perf-test.sh 脚本测试 Kafka Consumer 性能，但由于获取到的数据不靠谱，放弃这个测试方法</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)">性能数据</span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,102,255)">注：Gzip 和 Snappy 的传输速度 MB/S 是通过压缩前数据计算的，压缩后的实际传输量并没有超过百兆网卡上限</span></p>
<table cellspacing="0" cellpadding="0" class="t1        " style="color:rgb(0,0,0); font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<tbody>
<tr>
<td valign="top" class="td1">
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong><span style="font-size:14px">单条消息大小</span></strong></p>
</td>
<td valign="top" class="td2">
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong><span style="font-size:14px">batch size/条</span></strong></p>
</td>
<td valign="top" class="td3">
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong><span style="font-size:14px">线程数</span></strong></p>
</td>
<td valign="top" class="td4">
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong><span style="font-size:14px">压缩方式</span></strong></p>
</td>
<td valign="top" class="td5">
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong><span style="font-size:14px">传输速度 MB/S</span></strong></p>
</td>
<td valign="top" class="td6">
<p class="p3" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong><span style="font-size:14px">传输速度 Message/S</span></strong></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1000 (avg 500)</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">不压缩</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">11.1513 (约为百兆网卡上线)</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">23369.8916</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1000 (avg 500)</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Gzip</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">14.0450</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">29425.1878</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1000 (avg 500)</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Snappy</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">32.2064</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">67471.7850</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~100（avg 50）</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">不压缩</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">5.3654</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">111399.5121</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~100（avg 50）</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Gzip</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">2.6479</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">54979.4926</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~100（avg 50）</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Snappy</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">4.4217</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">91836.6410</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1800 (avg 900) 仿线上数据量大小</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">不压缩</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">11.0518 (约为百兆网卡上线)</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">12867.3632</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1800 (avg 900) 仿线上数据量大小</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Gzip</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">17.3944</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">20261.3717</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1800 (avg 900) 仿线上数据量大小</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Snappy</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">31.0658</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">36174.2150</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">以下数据为第二天测试数据</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"> </span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"> </span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"> </span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"> </span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"> </span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~100（avg 50）</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">不压缩</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">1.8482</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">38387.7159</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~100（avg 50）</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Gzip</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">1.3591</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">28219.0930</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~100（avg 50）</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Snappy</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">2.0213</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">41979.7658</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~100（avg 50）</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">50</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">不压缩</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">2.0900</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">43402.7778</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~100（avg 50）</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">50</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Gzip</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">1.4639</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">30387.7477</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~100（avg 50）</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">50</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Snappy</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">2.0871</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">43323.8021</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1000 (avg 500)</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">不压缩</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">9.8287</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">20594.3530</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1000 (avg 500)</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Gzip</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">13.0659</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">27386.0058</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1000 (avg 500)</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">10</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Snappy</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">20.1827</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">42265.4269</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1000 (avg 500)</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">1</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">不压缩</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">7.0980</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">14885.6041</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1000 (avg 500)</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">1</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Gzip</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">7.4438</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">15587.7356</span></p>
</td>
</tr>
<tr>
<td valign="top" class="td7">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">0~1000 (avg 500)</span></p>
</td>
<td valign="top" class="td8">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">200</span></p>
</td>
<td valign="top" class="td9">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">1</span></p>
</td>
<td valign="top" class="td10">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">Snappy</span></p>
</td>
<td valign="top" class="td11">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">15.3256</span></p>
</td>
<td valign="top" class="td12">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">32088.3070</span></p>
</td>
</tr>
</tbody>
</table>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,153,0)">测试结论</span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,153,0)">1、线上的实际message平均大小略小于1k，在这种情况下(对应 0~1800 的test case)，虚拟机可以应对每秒上万条写入请求。测试环境下，网络带宽是其瓶颈。通过压缩可以绕过瓶颈，Snappy算法可以处理36000+条请求每秒</span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,153,0)">2、在使用小数据进行测试时，Kafka每秒可以处理10万条左右数据，网络和IO都不是瓶颈，说明Kafka在虚拟机上处理写入请求的上限约为10万条每秒。</span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,153,0)">3、第二天的测试在相同条件下与第一天差距很大(0~100 大小数据，10线程，batch size 200)，第二天在不压缩情况下只有第一天的三分之一的处理能力，snappy压缩情况下也只有二分之一处理能力，说明虚拟机的性能不够稳定。</span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,153,0)">4、生产者线程数对比，说明在网络和IO及Kafka处理能力没有达到瓶颈时，更多的线程能够增加写入速度，但是增长不明显。</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,153,0)">测试推论</span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,153,0)">1、虚拟机上的Kafka最高也可以处理10万条请求，物理机的处理能力强得多，应当超过10万条每秒的处理能力。对应线上平均数据大小接近1K，处理数据流量能力不会低于100MB/S，接近千兆网卡上限。说明物理机上，在遇到网络带宽瓶颈前，Kafka性能应当不会是瓶颈。</span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,153,0)">2、虚拟机测试是在单topic 单replication 的情况下测试的。无法确定在多个replication时性能下降情况。从网上查找看，性能下降不是很明显。</span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(0,153,0)">3、从测试看，虚拟机的性能能够承担线上请求。但虚拟机性能不稳定，需要非常谨慎。</span></p>
<br>
<p><span style="font-size:24px; color:#ff0000"><strong>15）apache kafka监控系列-kafka-web-console</strong></span></p>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,51,51); font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; font-size:15px; line-height:25.5px">Kafka Web Console是kafka的开源web监控程序.</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(51,51,51)"><span style="font-size:15px; line-height:25.5px">功能介绍如下:</span></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<ul style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(51,51,51)"><span style="font-size:15px; line-height:25.5px">brokers列表</span></span></li><li><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(51,51,51)"><span style="font-size:15px; line-height:25.5px">连接kafka的zk集群列表</span></span></li><li><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(51,51,51)"><span style="font-size:15px; line-height:25.5px">所有topic列表，操作相应topic可以浏览查看相应message生产和消费流量图.</span></span></li></ul>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t1" style="color:rgb(255,153,0)"></a><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(51,51,51)"><span style="font-size:15px; line-height:25.5px">1.下载Kafka
 Web Console</span></span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(51,51,51)"><span style="font-size:15px; line-height:25.5px"><a target="_blank" href="https://github.com/claudemamo/kafka-web-console/archive/master.zip" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">Kafka
 Web Console</a><br>
</span></span></div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t2" style="color:rgb(255,153,0)"></a><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; font-size:14px; color:rgb(51,51,51)">2.安装sbt</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(51,51,51)">a. centos  : yum install sbt</span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(51,51,51)">b. ubuntu : apt-get install sbt   </span></div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; font-size:14px; color:rgb(51,51,51)">3.配置<span style="font-size:15px; line-height:25.5px">Kafka
 Web Console</span></span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(51,51,51)"><span style="font-size:15px; line-height:25.5px">a.增加数据库依赖包(mysql)，解压kafka-web-console.tar.gz,进入目录cd
 kafka-web-console</span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(51,51,51)"><span style="font-size:15px; line-height:25.5px">编辑文件vim
 build.sbt </span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(51,51,51)"><span style="font-size:15px; line-height:25.5px">增加mysql配置：</span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><pre><code class="language-java">......
libraryDependencies ++= Seq(
  jdbc,
  cache,
  "org.squeryl" % "squeryl_2.10" % "0.9.5-6",
  "com.twitter" % "util-zk_2.10" % "6.11.0",
  "com.twitter" % "finagle-core_2.10" % "6.15.0",
  "org.apache.kafka" % "kafka_2.10" % "0.8.1",
  "org.quartz-scheduler" % "quartz" % "2.2.1",
  "mysql" % "mysql-connector-java" % "5.1.9"
    exclude("javax.jms", "jms")
    exclude("com.sun.jdmk", "jmxtools")
    exclude("com.sun.jmx", "jmxri")
)
.......</code></pre></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<h2 style="margin:0px; padding:0px"><a target="_blank" name="t4" style="color:rgb(255,153,0)"></a><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px"><span style="font-size:14px">4.配置mysql的jdbc驱动</span></span></span></h2>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px">vim application.conf</span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px">增加代码如下:</span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px"></span></span><pre><code class="language-java">.......  
db.default.driver=com.mysql.jdbc.Driver  
db.default.url="jdbc:mysql://192.168.2.105:3306/mafka?useUnicode=true&amp;characterEncoding=UTF8&amp;connectTimeout=5000&amp;socketTimeout=10000"  
db.default.user=xxx  
db.default.password=xxx  
.......  </code></pre><br>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<h2 style="margin:0px; padding:0px"><a target="_blank" name="t5" style="color:rgb(255,153,0)"></a><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px"><span style="font-size:14px">5.执行sql语句(如下绿色选框所示)</span></span></span></h2>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px"><img src="https://img-blog.csdn.net/20140628213633390?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</span></span>
<h2 style="margin:0px; padding:0px"><a target="_blank" name="t6" style="color:rgb(255,153,0)"></a><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px"><span style="font-size:14px">6.编译</span></span></span></h2>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px">lizhitao@localhost:~$ sbt package<br>
</span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px">打包编译时会从官网上下载很多jar，由于网络原因，所以很慢，需要耐心等待。</span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px">注意:下载的jar是隐藏的，<span style="color:rgb(255,0,0)"><strong>在cd
  ~/.ivy2 目录(相应子目录)下可以看到所有jar.</strong></span></span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; color:rgb(255,0,0)"><span style="line-height:25.5px"><strong>ivy2所有jar包百度云下载</strong></span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px"><a target="_blank" href="http://pan.baidu.com/s/1gdgQqqB" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">ivy2所有jar包下载</a><br>
</span></span></div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t7" style="color:rgb(255,153,0)"></a><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; font-size:14px"><span style="line-height:25.5px">7.运行</span></span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px">lizhitao@localhost:~$ sbt run<br>
</span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px"><img src="https://img-blog.csdn.net/20140628214559562?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</span></span></div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t8" style="color:rgb(255,153,0)"></a><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; font-size:14px"><span style="line-height:25.5px">8.浏览访问</span></span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'"><span style="line-height:25.5px">访问地址: http://ip:9000/</span></span></div>
<br>
<span style="font-size:24px; color:#ff0000"><strong>16）apache kafka迁移与扩容工具用法</strong></span>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
参考官网site:https://cwiki.apache.org/confluence/display/KAFKA/Replication+tools#Replicationtools-6.ReassignPartitionsTool<br>
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">说明:</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
当我们对kafka集群扩容时，需要满足2点要求:</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<ol style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li>将指定topic迁移到集群内新增的node上。</li><li>将topic的指定partition迁移到新增的node上。</li></ol>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t2" style="color:rgb(255,153,0)"></a><span style="font-size:14px">1. 迁移topic到新增的node上</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">假如现在一个kafka集群运行三个broker，broker.id依次为101,102,103,后来由于业务数据突然暴增，需要新增三个broker,broker.id依次为104,105,106.目的是要把push-token-topic迁移到新增node上。脚本(json格式)如下所示:</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><pre><code class="language-java">lizhitao@localhost:$  ./bin/kafka-reassign-partitions.sh --zookeeper 192.168.2.225:2183/config/mobile/mq/mafka
--topics-to-move-json-file  migration-push-token-topic.json  --broker-list  "104,105,106"  --generate</code></pre>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 脚本migration-push-token-topic.json文件内容如下:</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<pre><code class="language-java">{
"topics":
[
{
"topic": "push-token-topic"
}
],
"version":1
}</code></pre>
<p></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
生成分配partitions的json脚本：</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<pre><code class="language-java">Current partition replica assignment
{"version":1,"partitions":[{"topic":"cluster-switch-topic","partition":10,"replicas":[8]},{"topic":"cluster-switch-topic","partition":5,"replicas":[4]},{"topic":"cluster-switch-topic","partition":3,"replicas":[5]},{"topic":"cluster-switch-topic","partition":4,"replicas":[5]},{"topic":"cluster-switch-topic","partition":9,"replicas":[5]},{"topic":"cluster-switch-topic","partition":1,"replicas":[5]},{"topic":"cluster-switch-topic","partition":11,"replicas":[4]},{"topic":"cluster-switch-topic","partition":7,"replicas":[5]},{"topic":"cluster-switch-topic","partition":2,"replicas":[4]},{"topic":"cluster-switch-topic","partition":0,"replicas":[4]},{"topic":"cluster-switch-topic","partition":6,"replicas":[4]},{"topic":"cluster-switch-topic","partition":8,"replicas":[4]}]}</code></pre>
<p></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
重新分配parttions的json脚本如下：</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<pre><code class="language-java">migration-topic-cluster-switch-topic.json 
 {"version":1,"partitions":[{"topic":"cluster-switch-topic","partition":10,"replicas":[5]},{"topic":"cluster-switch-topic","partition":5,"replicas":[4]},{"topic":"cluster-switch-topic","partition":4,"replicas":[5]},{"topic":"cluster-switch-topic","partition":3,"replicas":[4]},{"topic":"cluster-switch-topic","partition":9,"replicas":[4]},{"topic":"cluster-switch-topic","partition":1,"replicas":[4]},{"topic":"cluster-switch-topic","partition":11,"replicas":[4]},{"topic":"cluster-switch-topic","partition":7,"replicas":[4]},{"topic":"cluster-switch-topic","partition":2,"replicas":[5]},{"topic":"cluster-switch-topic","partition":0,"replicas":[5]},{"topic":"cluster-switch-topic","partition":6,"replicas":[5]},{"topic":"cluster-switch-topic","partition":8,"replicas":[5]}]}

lizhitao@localhost:$   bin/kafka-reassign-partitions.sh --zookeeper 192.168.2.225:2183/config/mobile/mq/mafka01 --reassignment-json-file migration-topic-cluster-switch-topic.json --execute</code></pre>
<p></p>
<h2 style="margin:0px; padding:0px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a>2.topic修改(replicats-factor)副本个数</h2>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<pre><code class="language-java">lizhitao@localhost:$ ./bin/kafka-reassign-partitions.sh --zookeeper   192.168.2.225:2183/config/mobile/mq/mafka
--reassignment-json-file  replicas-update-push-token-topic.json  --execute</code></pre>
<p></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
假如初始时push-token-topic为一个副本，为了提高可用性，需要改为2副本模式。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
脚本replicas-push-token-topic.json文件内容如下:<br>
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<pre><code class="language-java">{
        "partitions":
                [
                {
                        "topic": "log.mobile_nginx",
                        "partition": 0,
                        "replicas": [101,102,104]
                },
                {
                        "topic": "log.mobile_nginx",
                        "partition": 1,
                        "replicas": [102,103,106]
                },
{
"topic": "xxxx",
"partition": 数字,
"replicas": [数组]
}                
],             
        "version":1
}</code></pre>
<p></p>
<h2 style="margin:0px; padding:0px"><a target="_blank" name="t4" style="color:rgb(255,153,0)"></a>3.topic的分区扩容用法</h2>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
a.先扩容分区数量，脚本如下:</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
例如:push-token-topic初始分区数量为12，目前到增加到15个</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<pre><code class="language-java">lizhitao@localhost:$ ./bin/kafka-topics.sh --zookeeper 192.168.2.225:2183/config/mobile/mq/mafka  --alter   --partitions 15   --topic   push-token-topic</code></pre>
<p></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
b.设置topic分区副本</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
</p>
<pre><code class="language-java">lizhitao@localhost:$ ./bin/kafka-reassign-partitions.sh --zookeeper  192.168.2.225:2183/config/mobile/mq/mafka
--reassignment-json-file partitions-extension-push-token-topic.json  --execute</code></pre>
<p></p>
</div>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
脚本partitions-extension-push-token-topic.json文件内容如下:</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<pre><code class="language-java">{  
        "partitions":  
                [  
                {  
                        "topic": "push-token-topic",  
                        "partition": 12,  
                        "replicas": [101,102]  
                },  
                {  
                        "topic": "push-token-topic",  
                        "partition": 13,  
                        "replicas": [103,104]  
                },  
                {  
                        "topic": "push-token-topic",  
                        "partition": 14,  
                        "replicas": [105,106]  
                }  
                ],               
        "version":1  
} </code></pre>
<p></p>
<p><span style="font-size:24px; color:#ff0000"><strong>17）kafka LeaderNotAvailableException</strong></span></p>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
经常producer和consumer会包如下异常</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px; color:rgb(255,0,0)">LeaderNotAvailableException</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">原因:</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px"><span style="white-space:pre"></span>1.其中该分区所在的broker挂了，如果是多副本，该分区所在broker恰好为leader</span></p>
<br>
<span style="font-size:24px; color:#ff0000"><strong>18）apache kafka jmx监控指标参数</strong></span>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,51,51); font-family:'Source Sans Pro',sans-serif; font-size:17px; line-height:30.3333358764648px">Kafka使用Yammer Metrics来监控server和client指标数据。</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,51,51); font-family:'Source Sans Pro',sans-serif; font-size:17px; line-height:30.3333358764648px">JMX监控指标参数列表如下:</span></p>
<table class="data-table         " style="color:rgb(0,0,0); font-family:Arial; font-size:14.3999996185303px; line-height:26px; border:1px solid rgb(169,169,169); border-collapse:collapse; width:1000px">
<tbody>
<tr>
<th style="border:1px solid rgb(136,136,136); padding:2px; background-color:rgb(204,204,204)">
<span style="font-size:10px">参数</span></th>
<th style="border:1px solid rgb(136,136,136); padding:2px; background-color:rgb(204,204,204)">
<span style="font-size:10px">Mbean名称</span></th>
<th style="border:1px solid rgb(136,136,136); padding:2px; background-color:rgb(204,204,204)">
<span style="font-size:10px">说明</span></th>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Message in rate</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="AllTopicsMessagesInPerSec",type="BrokerTopicMetrics"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">所有topic消息(进出)流量</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Byte in rate</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="AllTopicsBytesInPerSec",type="BrokerTopicMetrics"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"><br>
</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Request rate</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.network":name="{Produce|Fetch-consumer|Fetch-follower}-RequestsPerSec",type="RequestMetrics"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"><br>
</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Byte out rate</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="AllTopicsBytesOutPerSec",type="BrokerTopicMetrics"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"><br>
</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Log flush rate and time</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.log":name="LogFlushRateAndTimeMs",type="LogFlushStats"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"><br>
</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"># of under replicated partitions (|ISR| &lt; |all replicas|)</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="UnderReplicatedPartitions",type="ReplicaManager"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">0</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Is controller active on broker</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.controller":name="ActiveControllerCount",type="KafkaController"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">only one broker in the cluster should have 1</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Leader election rate</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.controller":name="LeaderElectionRateAndTimeMs",type="ControllerStats"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">non-zero when there are broker failures</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Unclean leader election rate</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.controller":name="UncleanLeaderElectionsPerSec",type="ControllerStats"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">0</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Partition counts</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="PartitionCount",type="ReplicaManager"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">mostly even across brokers</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Leader replica counts</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="LeaderCount",type="ReplicaManager"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">mostly even across brokers</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">ISR shrink rate</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="ISRShrinksPerSec",type="ReplicaManager"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">If a broker goes down, ISR for some of the partitions will shrink. When that broker is up again, ISR will be expanded once the replicas are fully caught up. Other than that,
 the expected value for both ISR shrink rate and expansion rate is 0.</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">ISR expansion rate</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="ISRExpandsPerSec",type="ReplicaManager"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">See above</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Max lag in messages btw follower and leader replicas</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="([-.\w]+)-MaxLag",type="ReplicaFetcherManager"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">副本消息滞后数量</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Lag in messages per follower replica</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="([-.\w]+)-ConsumerLag",type="FetcherLagMetrics"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">副本消息滞后数量</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Requests waiting in the producer purgatory</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="PurgatorySize",type="ProducerRequestPurgatory"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"><br>
</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Requests waiting in the fetch purgatory</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.server":name="PurgatorySize",type="FetchRequestPurgatory"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"><br>
</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Request total time</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.network":name="{Produce|Fetch-Consumer|Fetch-Follower}-TotalTimeMs",type="RequestMetrics"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"><br>
</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Time the request waiting in the request queue</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.network":name="{Produce|Fetch-Consumer|Fetch-Follower}-QueueTimeMs",type="RequestMetrics"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"><br>
</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Time the request being processed at the leader</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.network":name="{Produce|Fetch-Consumer|Fetch-Follower}-LocalTimeMs",type="RequestMetrics"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"><br>
</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Time the request waits for the follower</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.network":name="{Produce|Fetch-Consumer|Fetch-Follower}-RemoteTimeMs",type="RequestMetrics"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"><br>
</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">Time to send the response</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px">"kafka.network":name="{Produce|Fetch-Consumer|Fetch-Follower}-ResponseSendTimeMs",type="RequestMetrics"</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px"><span style="font-size:10px"><br>
</span></td>
</tr>
<tr>
<td style="border:1px solid rgb(136,136,136); padding:2px; color:rgb(51,51,51); font-family:'Source Sans Pro',sans-serif; line-height:30.3333358764648px">
<span style="font-size:10px">Number of messages the consumer lags behind the producer by</span></td>
<td style="border:1px solid rgb(136,136,136); padding:2px; color:rgb(51,51,51); line-height:30.3333358764648px">
<span style="font-family:'Microsoft YaHei'"><span style="font-size:10px">"kafka.consumer":name="([-.\w]+)-MaxLag",type="ConsumerFetcherManager"</span></span></td>
</tr>
</tbody>
</table>
<br>
<p><span style="font-size:24px; color:#ff0000"><strong>19）apache kafka性能测试命令使用和构建kafka-perf</strong></span></p>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
本来想用kafka官方提供的工具做性能测试的。但事与愿违，当我执行官方提供的kafka测试脚本，却报错没有找到ProducerPerformance，后来浏览一些代码文件，才发现没有把perf性能测试程序打包到kafka_2.x.0-0.8.x.x.jar发行版本中。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
现在来教您如何打包做测试。</p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t0" style="color:rgb(255,153,0)"></a><span style="font-size:14px">1.准备工作：</span></h1>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/26875463" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">安装gradle</a><br>
</p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t1" style="color:rgb(255,153,0)"></a><span style="font-size:14px">2.下载kafka源代码</span></h1>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<a target="_blank" href="https://archive.apache.org/dist/kafka/0.8.1/kafka-0.8.1-src.tgz" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">kafka-0.8.1源代码</a><br>
</p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t2" style="color:rgb(255,153,0)"></a><span style="font-size:14px">3.编译kafka-perf_2.x-0.8.1.x.jar</span></h1>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:14.3999996185303px; background-color:rgb(255,255,255)"><strong><span style="color:#009900">编译注意事项：默认情况下是编译为2.8.0版本，也可以指定版本编译。目前编译高版本的kafka-perf(2.8.0以上版本)是由问题的，因为build.gradle配置参数有问题(版本不同，会报如下错误，<a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/37311565" rel="nofollow" style="text-decoration:none">版本不兼容错误</a>)，如果要构建高版本kafka-perf多版本修改内容如下：</span></strong></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
下载<a target="_blank" href="http://pan.baidu.com/s/1pJM73QF" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">build.gradle</a>   替换掉<span style="font-size:14.3999996185303px">kafka-0.8.1.1-src根目录下文件即可</span><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:14.3999996185303px">编译构建执行命令：</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:14.3999996185303px"></span></p>
<pre><code class="language-java">gradle jar   			默认生成2.8.0版本的kafka和kafka-perf的jar
gradle jar_core_2_8_0		生成2.8.0版本的kafka的jar
gradle jar_core_2_8_2		生成2.8.2版本的kafka的jar
gradle jar_core_2_9_1		生成2.9.1版本的kafka的jar
gradle jar_core_2_9_2		生成2.9.2版本的kafka的jar
gradle jar_core_2_10_1		生成2.10.1版本的kafka的jar
gradle perf:jar			生成2.8.0版本的kafka和kafka-perf的jar
gradle perf_2_9_1		生成2.9.1版本的kafka和kafka-perf的jar
gradle perf_2_10_1		生成2.10.1版本的kafka和kafka-perf的jar
gradle -PscalaVersion=2.8.0 jar			编译scala 2.8.0版本编译所有jar
gradle -PscalaVersion=2.8.2 jar			编译scala 2.8.2版本编译所有jar
gradle -PscalaVersion=2.9.1 jar			编译scala 2.9.1版本编译所有jar
gradle -PscalaVersion=2.10.1 jar		编译scala 2.10.1版本编译所有jar</code></pre><br>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
如果不想编译jar，可以直接下载：<a target="_blank" href="http://download.csdn.net/detail/lizhitao/7637693" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">kafka-perf_2.x.x-0.8.1.jar</a> </p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<pre><code class="language-java">lizhitao@users-MacBook-Pro:~/mt_wp/tmp$ cd kafka-0.8.1.1-src
lizhitao@users-MacBook-Pro:~/mt_wp/tmp/kafka-0.8.1.1-src$gradle jar
lizhitao@users-MacBook-Pro:~/mt_wp/tmp/kafka-0.8.1.1-src$gradle perf:jar
The TaskContainer.add() method has been deprecated and is scheduled to be removed in Gradle 2.0. Please use the create() method instead.
Building project 'core' with Scala version 2.8.0
Building project 'perf' with Scala version 2.8.0
:core:compileJava UP-TO-DATE
:core:compileScala
/Users/lizhitao/mt_wp/tmp/kafka-0.8.1.1-src/core/src/main/scala/kafka/admin/AdminUtils.scala:243: non variable type-argument String in type pattern scala.collection.Map[String,_] is unchecked since it is eliminated by erasure
        case Some(map: Map[String, _]) =&gt;
                       ^
/Users/lizhitao/mt_wp/tmp/kafka-0.8.1.1-src/core/src/main/scala/kafka/admin/AdminUtils.scala:246: non variable type-argument String in type pattern scala.collection.Map[String,String] is unchecked since it is eliminated by erasure
            case Some(config: Map[String, String]) =&gt;
                              ^
/Users/lizhitao/mt_wp/tmp/kafka-0.8.1.1-src/core/src/main/scala/kafka/api/LeaderAndIsrResponse.scala:66: non variable type-argument String in type pattern (String, Int) is unchecked since it is eliminated by erasure
    for ((key:(String, Int), value) &lt;- responseMap) {
              ^
/Users/lizhitao/mt_wp/tmp/kafka-0.8.1.1-src/core/src/main/scala/kafka/utils/Utils.scala:363: non variable type-argument V in type pattern List[V] is unchecked since it is eliminated by erasure
        case Some(l: List[V]) =&gt; m.put(k, v :: l)
                     ^
four warnings found
:core:processResources UP-TO-DATE
:core:classes
:core:copyDependantLibs UP-TO-DATE
:core:jar UP-TO-DATE
:perf:compileJava UP-TO-DATE
:perf:compileScala
:perf:processResources UP-TO-DATE
:perf:classes
:perf:jar UP-TO-DATE

BUILD SUCCESSFUL
Total time: 54.41 secs</code></pre>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
编译jar包目录如下：</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
a. kafka_2.x-0.8.1.1.jar<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
kafka-0.8.1.1-src/core/build<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140706113819609?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
b.<span style="font-size:14.3999996185303px">kafka-perf_2.x-</span><span style="font-size:14.3999996185303px">0.8.1.x.jar</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:14.3999996185303px">kafka-0.8.1.1-src/perf/build/libs<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:14.3999996185303px"><img src="https://img-blog.csdn.net/20140706114029468?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:14.3999996185303px">kafka多版本jar：</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:14.3999996185303px"><br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:14.3999996185303px"><img src="https://img-blog.csdn.net/20140706114152265?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</span></p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a><span style="font-size:14px"><span style="font-size:14.3999996185303px">4. kafka性能测试命令用法：</span></span></h1>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t4" style="color:rgb(255,153,0)"></a><span style="font-size:14.3999996185303px">4.1 创建topic</span></h2>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:14.3999996185303px"></span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
bin/kafka-topics.sh --zookeeper 192.168.2.225:2182,192.168.2.225:2183/config/mobile/mq/mafka02 --create --topic test-rep-one --partitions 6 --replication-factor 1</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<br>
</p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t5" style="color:rgb(255,153,0)"></a><span style="font-size:14.3999996185303px"><strong>4.2 kafka-producer-perf-test.sh</strong>中参数说明：</span></h2>
<div><span style="font-size:14.3999996185303px"></span><pre><code class="language-java">messages		生产者发送总的消息数量
message-size		每条消息大小
batch-size		每次批量发送消息的数量
topics			生产者发送的topic
threads			生产者使用几个线程同时发送
broker-list		安装kafka服务的机器ip:port列表
producer-num-retries	一个消息失败发送重试次数
request-timeout-ms	一个消息请求发送超时时间</code></pre><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t6" style="color:rgb(255,153,0)"></a><span style="font-size:14.3999996185303px"><strong>4.3 bin/kafka-consumer-perf-test.sh</strong>中参数说明：</span></h2>
<div><span style="font-size:14.3999996185303px"></span><pre><code class="language-java">zookeeperzk		配置
messages		消费者消费消息总数量
topic			消费者需要消费的topic
threads			消费者使用几个线程同时消费
group			消费者组名称
socket-buffer-sizesocket	缓冲大小
fetch-size		每次向kafka broker请求消费大小
consumer.timeout.ms	消费者去kafka broker拿去一条消息超时时间</code></pre></div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t7" style="color:rgb(255,153,0)"></a>4.4 生产者发送数据：</h2>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<pre><code class="language-java">lizhitao@users-MacBook-Pro:~/mt_wp/tmp/kafka-0.8.1.1-src$ bin/kafka-producer-perf-test.sh --messages 5000000 --message-size 5000  --batch-size 5000 --topics test-rep-one --threads 8 --broker-list mobile-esb03:9092,mobile-esb04:9092,mobile-esb05:9092
start.time, end.time, compression, message.size, batch.size, total.data.sent.in.MB, MB.sec, total.data.sent.in.nMsg, nMsg.sec
[2014-07-06 12:52:36,139] WARN Property reconnect.interval is not valid (kafka.utils.VerifiableProperties)
SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
SLF4J: Defaulting to no-operation (NOP) logger implementation
SLF4J: See http://www.slf4j.org/codes.html#StaticLoggerBinder for further details.
[2014-07-06 12:52:36,199] WARN Property reconnect.interval is not valid (kafka.utils.VerifiableProperties)
[2014-07-06 12:52:36,202] WARN Property reconnect.interval is not valid (kafka.utils.VerifiableProperties)
[2014-07-06 12:52:36,204] WARN Property reconnect.interval is not valid (kafka.utils.VerifiableProperties)
[2014-07-06 12:52:36,206] WARN Property reconnect.interval is not valid (kafka.utils.VerifiableProperties)
[2014-07-06 12:52:36,207] WARN Property reconnect.interval is not valid (kafka.utils.VerifiableProperties)
[2014-07-06 12:52:36,209] WARN Property reconnect.interval is not valid (kafka.utils.VerifiableProperties)
[2014-07-06 12:52:36,214] WARN Property reconnect.interval is not valid (kafka.utils.VerifiableProperties)</code></pre>
<p></p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t8" style="color:rgb(255,153,0)"></a>4.5 消费者消费数据</h2>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<pre><code class="language-java">lizhitao@users-MacBook-Pro:~/mt_wp/tmp/kafka-0.8.1.1-src$ bin/kafka-consumer-perf-test.sh --zookeeper
192.168.2.225:2182,192.168.2.225:2183/config/mobile/mq/mafka02 --messages 50000000 --topic test-rep-one --threads 1
start.time, end.time, fetch.size, data.consumed.in.MB, MB.sec, data.consumed.in.nMsg, nMsg.sec
SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
SLF4J: Defaulting to no-operation (NOP) logger implementation
SLF4J: See http://www.slf4j.org/codes.html#StaticLoggerBinder for further details.</code></pre>
<p></p>
<p><span style="font-size:24px; color:#ff0000"><strong>20）apache kafka源码构建打包</strong></span></p>
<p></p>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<h1 style="margin:0px; padding:0px; color:rgb(51,51,51)"><span style="font-size:14px">准备工作：</span></h1>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; color:rgb(51,51,51)">
<a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/26875463" rel="nofollow" style="color:rgb(51,102,153); text-decoration:none">安装gradle</a></p>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t2" style="color:rgb(255,153,0)"></a>1.构建kafka的jar并运行</h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-size:12px">打包</span>kafka-0.8.1.1下所有jar，包括core,perf,clients等。</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">lizhitao@users-MacBook-Pro:~/mt_wp/tmp/kafka-0.8.1.1-src$ gradle jar<br>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><img src="https://img-blog.csdn.net/20140708161948281?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a><span style="font-size:14px">2.构建源代码jar</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">lizhitao@users-MacBook-Pro:~/mt_wp/tmp/kafka-0.8.1.1-src$ gradle srcJar<br>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><img src="https://img-blog.csdn.net/20140708171106718?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t4" style="color:rgb(255,153,0)"></a><span style="font-size:14px">3.运行序列化测试</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">lizhitao@users-MacBook-Pro:~/mt_wp/tmp/kafka-0.8.1.1-src$ gradle -Dtest.single=RequestResponseSerializationTest core:test<br>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><img src="https://img-blog.csdn.net/20140708171635609?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t5" style="color:rgb(255,153,0)"></a><span style="font-size:14px">4.gradle任务列表</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">lizhitao@users-MacBook-Pro:~/mt_wp/tmp/kafka-0.8.1.1-src$ gradle tasks<br>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><img src="https://img-blog.csdn.net/20140708175041234?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t6" style="color:rgb(255,153,0)"></a>5.构建所有jar，包括tasks中各个版本jar</h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">lizhitao@users-MacBook-Pro:~/mt_wp/tmp/kafka-0.8.1.1-src$ gradle jarAll<br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t7" style="color:rgb(255,153,0)"></a>6.指定构建jar包版本</h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">lizhitao@users-MacBook-Pro:~/mt_wp/tmp/kafka-0.8.1.1-src$ gradle <span style="color:rgb(51,51,51); font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; line-height:25.5px">-PscalaVersion=2.10.1
 jar</span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="color:rgb(51,51,51); font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; line-height:25.5px">7.发布文件到maven仓库</span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="color:rgb(51,51,51); font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; line-height:25.5px"><span style="font-size:13.63636302948px">lizhitao@users-MacBook-Pro:~/mt_wp/tmp/kafka-0.8.1.1-src$
 gradle uploadArchivesAll</span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="color:rgb(51,51,51); font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; line-height:25.5px"><span style="font-size:13.63636302948px">编辑文件<span style="font-family:Consolas,'Liberation Mono',Menlo,Courier,monospace; font-size:12px; line-height:20.3999996185303px; background-color:rgb(248,248,248)">~/.gradle/gradle.properties，增加如下内容：</span></span></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="color:rgb(51,51,51); font-family:Helvetica,arial,freesans,clean,sans-serif,'Segoe UI Emoji','Segoe UI Symbol'; line-height:25.5px"><span style="font-size:13.63636302948px"><span style="font-family:Consolas,'Liberation Mono',Menlo,Courier,monospace; font-size:12px; line-height:20.3999996185303px; background-color:rgb(248,248,248)"></span></span></span>
<pre style="white-space:pre-wrap; word-wrap:normal; overflow:auto; font-family:Consolas,'Liberation Mono',Menlo,Courier,monospace; font-size:13px; margin-top:15px; margin-bottom:15px; border:1px solid rgb(221,221,221); line-height:19px; padding:6px 10px; color:rgb(51,51,51); background-color:rgb(248,248,248)"><code style="font-family:Consolas,'Liberation Mono',Menlo,Courier,monospace; font-size:12px; margin:0px; border:none; padding:0px; word-wrap:normal; display:inline; line-height:inherit; background:transparent">mavenUrl=
mavenUsername=
mavenPassword=
signing.keyId=
signing.password=
signing.secretKeyRingFile=</code></pre>
</div>
<p></p>
<p><span style="font-size:24px; color:#ff0000"><strong>21）Apache kafka客户端开发-java</strong></span></p>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
1.依赖包</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
        &lt;dependency&gt;<br>
            &lt;groupId&gt;org.apache.kafka&lt;/groupId&gt;<br>
            &lt;artifactId&gt;kafka_2.10&lt;/artifactId&gt;<br>
            &lt;version&gt;0.8.1&lt;/version&gt;<br>
        &lt;/dependency&gt;<br>
</p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t0" style="color:rgb(255,153,0)"></a><span style="font-size:14px">2.producer程序开发例子</span></h1>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t1" style="color:rgb(255,153,0)"></a><span style="font-size:14px">2.1 producer参数说明</span></h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<div><code style="font-family:Consolas,'Liberation Mono',Menlo,Courier,monospace; font-size:12px; margin:0px; border:none; padding:0px; word-wrap:normal; display:inline; line-height:inherit; background:transparent"></code>
<pre style="white-space:pre-wrap; word-wrap:normal; margin-top:15px; overflow:auto; font-family:Consolas,'Liberation Mono',Menlo,Courier,monospace; font-size:13px; border:1px solid rgb(221,221,221); line-height:19px; padding:6px 10px; color:rgb(51,51,51); margin-bottom:0px!important; background-color:rgb(248,248,248)"><code style="font-family:Consolas,'Liberation Mono',Menlo,Courier,monospace; font-size:12px; margin:0px; border:none; padding:0px; word-wrap:normal; display:inline; line-height:inherit; background:transparent">#指定kafka节点列表，用于获取metadata，不必全部指定
metadata.broker.list=192.168.2.105:9092,192.168.2.106:9092
# 指定分区处理类。默认kafka.producer.DefaultPartitioner，表通过key哈希到对应分区
#partitioner.class=com.meituan.mafka.client.producer.CustomizePartitioner
 
# 是否压缩，默认0表示不压缩，1表示用gzip压缩，2表示用snappy压缩。压缩后消息中会有头来指明消息压缩类型，故在消费者端消息解压是透明的无需指定。
compression.codec=none
  
# 指定序列化处理类(mafka client API调用说明--&gt;3.序列化约定wiki)，默认为kafka.serializer.DefaultEncoder,即byte[]
serializer.class=com.meituan.mafka.client.codec.MafkaMessageEncoder
# serializer.class=kafka.serializer.DefaultEncoder
# serializer.class=kafka.serializer.StringEncoder
# 如果要压缩消息，这里指定哪些topic要压缩消息，默认empty，表示不压缩。
#compressed.topics=
 
########### request ack ###############
# producer接收消息ack的时机.默认为0. 
# 0: producer不会等待broker发送ack 
# 1: 当leader接收到消息之后发送ack 
# 2: 当所有的follower都同步消息成功后发送ack. 
request.required.acks=0 
# 在向producer发送ack之前,broker允许等待的最大时间 
# 如果超时,broker将会向producer发送一个error ACK.意味着上一次消息因为某种 
# 原因未能成功(比如follower未能同步成功) 
request.timeout.ms=10000
########## end #####################
 
 
# 同步还是异步发送消息，默认“sync”表同步，"async"表异步。异步可以提高发送吞吐量,
# 也意味着消息将会在本地buffer中,并适时批量发送，但是也可能导致丢失未发送过去的消息
producer.type=sync
############## 异步发送 (以下四个异步参数可选) ####################
# 在async模式下,当message被缓存的时间超过此值后,将会批量发送给broker,默认为5000ms
# 此值和batch.num.messages协同工作.
queue.buffering.max.ms = 5000
# 在async模式下,producer端允许buffer的最大消息量
# 无论如何,producer都无法尽快的将消息发送给broker,从而导致消息在producer端大量沉积
# 此时,如果消息的条数达到阀值,将会导致producer端阻塞或者消息被抛弃，默认为10000
queue.buffering.max.messages=20000
# 如果是异步，指定每次批量发送数据量，默认为200
batch.num.messages=500
# 当消息在producer端沉积的条数达到"queue.buffering.max.meesages"后 
# 阻塞一定时间后,队列仍然没有enqueue(producer仍然没有发送出任何消息) 
# 此时producer可以继续阻塞或者将消息抛弃,此timeout值用于控制"阻塞"的时间 
# -1: 无阻塞超时限制,消息不会被抛弃 
# 0:立即清空队列,消息被抛弃 
queue.enqueue.timeout.ms=-1
################ end ###############
 
# 当producer接收到error ACK,或者没有接收到ACK时,允许消息重发的次数 
# 因为broker并没有完整的机制来避免消息重复,所以当网络异常时(比如ACK丢失) 
# 有可能导致broker接收到重复的消息,默认值为3.
message.send.max.retries=3
 
 
# producer刷新topic metada的时间间隔,producer需要知道partition leader的位置,以及当前topic的情况 
# 因此producer需要一个机制来获取最新的metadata,当producer遇到特定错误时,将会立即刷新 
# (比如topic失效,partition丢失,leader失效等),此外也可以通过此参数来配置额外的刷新机制，默认值600000 
topic.metadata.refresh.interval.ms=60000</code></pre>
<div><pre><code class="language-java">import java.util.*;  
   
import kafka.javaapi.producer.Producer;  
import kafka.producer.KeyedMessage;  
import kafka.producer.ProducerConfig;  
   
public class TestProducer {  
    public static void main(String[] args) {  
        long events = Long.parseLong(args[0]);  
        Random rnd = new Random();  
   
        Properties props = new Properties();  
        props.put("metadata.broker.list", "192.168.2.105:9092");  
        props.put("serializer.class", "kafka.serializer.StringEncoder"); //默认字符串编码消息  
        props.put("partitioner.class", "example.producer.SimplePartitioner");  
        props.put("request.required.acks", "1");  
   
        ProducerConfig config = new ProducerConfig(props);  
   
        Producer&lt;String, String&gt; producer = new Producer&lt;String, String&gt;(config);  
   
        for (long nEvents = 0; nEvents &lt; events; nEvents++) {   
               long runtime = new Date().getTime();    
               String ip = “192.168.2.” + rnd.nextInt(255);   
               String msg = runtime + “,www.example.com,” + ip;   
               KeyedMessage&lt;String, String&gt; data = new KeyedMessage&lt;String, String&gt;("page_visits", ip, msg);  
               producer.send(data);  
        }  
        producer.close();  
    }  
}</code></pre></div>
</div>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t2" style="color:rgb(255,153,0)"></a>2.1 指定关键字key，发送消息到指定partitions</h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"></div>
<div class="line number1 index0 alt2" style="font-family:Arial; font-size:14.3999996185303px; line-height:20px; color:rgb(51,51,51); border:0px!important; bottom:auto!important; float:none!important; height:auto!important; left:auto!important; margin:0px!important; outline:0px!important; overflow:visible!important; padding:0px 1em 0px 0px!important; position:static!important; right:auto!important; top:auto!important; vertical-align:baseline!important; width:auto!important; min-height:inherit!important; white-space:nowrap!important">
说明：如果需要实现自定义partitions消息发送，需要实现Partitioner接口</div>
<div class="line number1 index0 alt2" style="font-family:Arial; font-size:14.3999996185303px; line-height:20px; color:rgb(51,51,51); border:0px!important; bottom:auto!important; float:none!important; height:auto!important; left:auto!important; margin:0px!important; outline:0px!important; overflow:visible!important; padding:0px 1em 0px 0px!important; position:static!important; right:auto!important; top:auto!important; vertical-align:baseline!important; width:auto!important; min-height:inherit!important; white-space:nowrap!important">
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; font-size:12px; width:760.737487792969px; overflow:auto; padding-top:1px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/37811291#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/37811291#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/426922" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/426922/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:2658px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">class</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> CustomizePartitioner </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">implements</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Partitioner {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> CustomizePartitioner(VerifiableProperties props) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * 返回分区索引编号</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * @param key sendMessage时，输出的partKey</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * @param numPartitions topic中的分区总数</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * @return</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="annotation" style="margin:0px; padding:0px; border:none; color:rgb(100,100,100); background-color:inherit">@Override</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> partition(Object key, </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> numPartitions) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        System.out.println(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"key:"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + key + </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"  numPartitions:"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + numPartitions);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        String partKey = (String)key;  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (</span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"part2"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.equals(partKey))  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">2</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//        System.out.println("partKey:" + key);</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        ........  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        ........  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">}  </span></li></ol>
</div>
<br>
<h1 style="margin:0px; padding:0px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a>3.consumer程序开发例子</h1>
<h2 style="margin:0px; padding:0px"><a target="_blank" name="t4" style="color:rgb(255,153,0)"></a>3.1 <span style="font-size:14px">consumer参数说明</span></h2>
<div>
<pre style="white-space:pre-wrap; word-wrap:normal; margin-top:15px; overflow:auto; font-family:Consolas,'Liberation Mono',Menlo,Courier,monospace; font-size:13px; border:1px solid rgb(221,221,221); line-height:19px; padding:6px 10px; margin-bottom:0px!important; background-color:rgb(248,248,248)"><code style="font-family:Consolas,'Liberation Mono',Menlo,Courier,monospace; font-size:12px; margin:0px; border:none; padding:0px; word-wrap:normal; display:inline; line-height:inherit; background:transparent"># zookeeper连接服务器地址，此处为线下测试环境配置(kafka消息服务--&gt;kafka broker集群线上部署环境wiki)
# 配置例子："127.0.0.1:3000,127.0.0.1:3001,127.0.0.1:3002"
zookeeper.connect=192.168.2.225:2181,192.168.2.225:2182,192.168.2.225:2183/config/mobile/mq/mafka
# zookeeper的session过期时间，默认5000ms，用于检测消费者是否挂掉，当消费者挂掉，其他消费者要等该指定时间才能检查到并且触发重新负载均衡
zookeeper.session.timeout.ms=5000
zookeeper.connection.timeout.ms=10000
# 指定多久消费者更新offset到zookeeper中。注意offset更新时基于time而不是每次获得的消息。一旦在更新zookeeper发生异常并重启，将可能拿到已拿到过的消息
zookeeper.sync.time.ms=2000
 
#指定消费组
group.id=xxx
# 当consumer消费一定量的消息之后,将会自动向zookeeper提交offset信息 
# 注意offset信息并不是每消费一次消息就向zk提交一次,而是现在本地保存(内存),并定期提交,默认为true
auto.commit.enable=true
# 自动更新时间。默认60 * 1000
auto.commit.interval.ms=1000
 
# 当前consumer的标识,可以设定,也可以有系统生成,主要用来跟踪消息消费情况,便于观察
conusmer.id=xxx 
 
# 消费者客户端编号，用于区分不同客户端，默认客户端程序自动产生
client.id=xxxx
# 最大取多少块缓存到消费者(默认10)
queued.max.message.chunks=50
# 当有新的consumer加入到group时,将会reblance,此后将会有partitions的消费端迁移到新 
# 的consumer上,如果一个consumer获得了某个partition的消费权限,那么它将会向zk注册 
# "Partition Owner registry"节点信息,但是有可能此时旧的consumer尚没有释放此节点, 
# 此值用于控制,注册节点的重试次数. 
rebalance.max.retries=5
# 获取消息的最大尺寸,broker不会像consumer输出大于此值的消息chunk
# 每次feth将得到多条消息,此值为总大小,提升此值,将会消耗更多的consumer端内存
fetch.min.bytes=6553600
# 当消息的尺寸不足时,server阻塞的时间,如果超时,消息将立即发送给consumer
fetch.wait.max.ms=5000
socket.receive.buffer.bytes=655360
 
# 如果zookeeper没有offset值或offset值超出范围。那么就给个初始的offset。有smallest、largest、
# anything可选，分别表示给当前最小的offset、当前最大的offset、抛异常。默认largest
auto.offset.reset=smallest
# 指定序列化处理类(mafka client API调用说明--&gt;3.序列化约定wiki)，默认为kafka.serializer.DefaultDecoder,即byte[]
derializer.class=com.meituan.mafka.client.codec.MafkaMessageDecoder</code></pre>
</div>
<div><br>
</div>
</div>
<h2 style="font-family:Arial; line-height:20px; color:rgb(51,51,51); margin:0px!important; padding:0px 1em 0px 0px!important; border:0px!important; bottom:auto!important; float:none!important; height:auto!important; left:auto!important; outline:0px!important; overflow:visible!important; position:static!important; right:auto!important; top:auto!important; vertical-align:baseline!important; width:auto!important; min-height:inherit!important; white-space:nowrap!important">
<a target="_blank" name="t5" style="color:rgb(255,153,0)"></a>3.2 多线程并行消费topic</h2>
<div class="line number1 index0 alt2" style="font-family:Arial; font-size:14.3999996185303px; line-height:20px; color:rgb(51,51,51); border:0px!important; bottom:auto!important; float:none!important; height:auto!important; left:auto!important; margin:0px!important; outline:0px!important; overflow:visible!important; padding:0px 1em 0px 0px!important; position:static!important; right:auto!important; top:auto!important; vertical-align:baseline!important; width:auto!important; min-height:inherit!important; white-space:nowrap!important">
ConsumerTest类<br>
</div>
<div class="line number1 index0 alt2" style="font-family:Arial; font-size:14.3999996185303px; line-height:20px; color:rgb(51,51,51); border:0px!important; bottom:auto!important; float:none!important; height:auto!important; left:auto!important; margin:0px!important; outline:0px!important; overflow:visible!important; padding:0px 1em 0px 0px!important; position:static!important; right:auto!important; top:auto!important; vertical-align:baseline!important; width:auto!important; min-height:inherit!important; white-space:nowrap!important">
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; font-size:12px; width:760.737487792969px; overflow:auto; padding-top:1px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/37811291#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/37811291#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/426922" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/426922/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:4076px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">import</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> kafka.consumer.ConsumerIterator;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">import</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> kafka.consumer.KafkaStream;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">class</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ConsumerTest </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">implements</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Runnable {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> KafkaStream m_stream;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> m_threadNumber;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ConsumerTest(KafkaStream a_stream, </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> a_threadNumber) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        m_threadNumber = a_threadNumber;  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        m_stream = a_stream;  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> run() {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        ConsumerIterator&lt;<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">byte</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">[], </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">byte</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">[]&gt; it = m_stream.iterator();  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">while</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (it.hasNext())  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            System.out.println(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Thread "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + m_threadNumber + </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">": "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String(it.next().message()));  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        System.out.println(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Shutting down Thread: "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + m_threadNumber);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">}  </span></li></ol>
</div>
ConsumerGroupExample类<br>
</div>
<div class="line number1 index0 alt2" style="font-family:Arial; line-height:20px; border:0px!important; bottom:auto!important; float:none!important; height:auto!important; left:auto!important; margin:0px!important; outline:0px!important; overflow:visible!important; padding:0px 1em 0px 0px!important; position:static!important; right:auto!important; top:auto!important; vertical-align:baseline!important; width:auto!important; min-height:inherit!important; white-space:nowrap!important">
<div class="dp-highlighter bg_java" style="color:rgb(51,51,51); font-size:12px; font-family:Consolas,'Courier New',Courier,mono,serif; width:760.737487792969px; overflow:auto; padding-top:1px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/37811291#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/37811291#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/426922" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/426922/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:4522px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">import</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> kafka.consumer.ConsumerConfig;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">import</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> kafka.consumer.KafkaStream;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">import</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> kafka.javaapi.consumer.ConsumerConnector;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">import</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> java.util.HashMap;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">import</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> java.util.List;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">import</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> java.util.Map;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">import</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> java.util.Properties;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">import</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> java.util.concurrent.ExecutorService;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">import</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> java.util.concurrent.Executors;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">class</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ConsumerGroupExample {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ConsumerConnector consumer;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String topic;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  ExecutorService executor;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ConsumerGroupExample(String a_zookeeper, String a_groupId, String a_topic) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        consumer = kafka.consumer.Consumer.createJavaConsumerConnector(  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                createConsumerConfig(a_zookeeper, a_groupId));  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">this</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.topic = a_topic;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> shutdown() {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (consumer != </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">) consumer.shutdown();  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (executor != </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">) executor.shutdown();  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> run(</span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> a_numThreads) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        Map&lt;String, Integer&gt; topicCountMap = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> HashMap&lt;String, Integer&gt;();  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        topicCountMap.put(topic, <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Integer(a_numThreads));  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        Map&lt;String, List&lt;KafkaStream&lt;<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">byte</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">[], </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">byte</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">[]&gt;&gt;&gt; consumerMap = consumer.createMessageStreams(topicCountMap);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        List&lt;KafkaStream&lt;<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">byte</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">[], </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">byte</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">[]&gt;&gt; streams = consumerMap.get(topic);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 启动所有线程</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        executor = Executors.newFixedThreadPool(a_numThreads);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 开始消费消息</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> threadNumber = </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">for</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (</span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> KafkaStream stream : streams) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            executor.submit(<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ConsumerTest(stream, threadNumber));  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            threadNumber++;  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ConsumerConfig createConsumerConfig(String a_zookeeper, String a_groupId) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        Properties props = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Properties();  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        props.put(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"zookeeper.connect"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"192.168.2.225:2183/config/mobile/mq/mafka"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        props.put(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"group.id"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"push-token"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        props.put(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"zookeeper.session.timeout.ms"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"60000"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        props.put(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"zookeeper.sync.time.ms"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"2000"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        props.put(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"auto.commit.interval.ms"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"1000"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ConsumerConfig(props);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> main(String[] args) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        String zooKeeper = args[<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">];  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        String groupId = args[<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">];  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        String topic = args[<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">2</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">];  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> threads = Integer.parseInt(args[</span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">3</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">]);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        ConsumerGroupExample example = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ConsumerGroupExample(zooKeeper, groupId, topic);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        example.run(threads);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            Thread.sleep(<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">10000</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (InterruptedException ie) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        example.shutdown();  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">}  </span></li></ol>
</div>
<div class="line number1 index0 alt2" style="border:0px!important; bottom:auto!important; float:none!important; height:auto!important; left:auto!important; margin:0px!important; outline:0px!important; overflow:visible!important; padding:0px 1em 0px 0px!important; position:static!important; right:auto!important; top:auto!important; vertical-align:baseline!important; width:auto!important; min-height:inherit!important">
<span style="font-size:18px; color:rgb(51,51,51)"><strong>总结：</strong><br>
</span><span style="color:#ff0000"><span style="font-size:14.3999996185303px"><span style="white-space:pre"></span>kafka消费者api分为high api和low api，目前上述demo是都是使用kafka high api，高级api不用关心维护消费状态信息和负载均衡，系统会根据配置参数，</span><br>
<span style="font-size:14.3999996185303px">定期flush offset到zk上，如果有多个consumer且每个consumer创建了多个线程，高级api会根据zk上注册consumer信息，进行自动负载均衡操作。</span></span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">注意事项：</span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">1.高级api将会内部实现持久化每个分区最后读到的消息的offset，数据保存在zookeeper中的消费组名中(如/consumers/push-token-group/offsets/push-token/2。</span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">其中push-token-group是消费组，push-token是topic，最后一个2表示第3个分区)，每间隔一个(默认1000ms)时间更新一次offset，</span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">那么可能在重启消费者时拿到重复的消息。此外，当分区leader发生变更时也可能拿到重复的消息。因此在关闭消费者时最好等待一定时间（10s）然后再shutdown()</span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">2.消费组名是一个全局的信息，要注意在新的消费者启动之前旧的消费者要关闭。如果新的进程启动并且消费组名相同，kafka会添加这个进程到可用消费线程组中用来消费</span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">topic和触发重新分配负载均衡，那么同一个分区的消息就有可能发送到不同的进程中。</span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">3.如果消费者组中所有consumer的总线程数量大于分区数，一部分线程或某些consumer可能无法读取消息或处于空闲状态。</span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">4.如果分区数多于线程数(如果消费组中运行者多个消费者，则线程数为消费者组内所有消费者线程总和)，一部分线程会读取到多个分区的消息</span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">5.如果一个线程消费多个分区消息，那么接收到的消息是不能保证顺序的。</span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">备注：可用zookeeper web ui工具管理查看zk目录树数据： xxx/consumers/push-token-group/owners/push-token/2其中</span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">push-token-group为消费组，push-token为topic,2为分区3.查看里面的内容如：</span><br>
<span style="color:rgb(51,51,51); font-size:14.3999996185303px">push-token-group-mobile-platform03-1405157976163-7ab14bd1-0表示该分区被该标示的线程所执行。</span></div>
<div class="line number1 index0 alt2" style="border:0px!important; bottom:auto!important; float:none!important; height:auto!important; left:auto!important; margin:0px!important; outline:0px!important; overflow:visible!important; padding:0px 1em 0px 0px!important; position:static!important; right:auto!important; top:auto!important; vertical-align:baseline!important; width:auto!important; min-height:inherit!important">
<span style="color:#333333"><span style="font-size:14px"><br>
</span></span><span style="font-size:14.3999996185303px"><span style="color:rgb(51,51,51); white-space:pre"></span><span style="color:#006600">producer性能优化:异步化，消息批量发送，具体浏览上述参数说明。consumer性能优化:如果是高吞吐量数据，设置每次拿取消息(fetch.min.bytes)大些，</span></span><span style="color:#006600"><br>
<span style="font-size:14.3999996185303px">拿取消息频繁(fetch.wait.max.ms)些(或时间间隔短些)，如果是低延时要求，则设置时间时间间隔小，每次从kafka broker拿取消息尽量小些。</span></span></div>
</div>
<br>
<p><span style="font-size:24px; color:#ff0000"><strong>22） kafka broker内部架构</strong></span></p>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
下面介绍kafka broker的主要子模块，帮助您更好地学习并理解kafka源代码和架构。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
如下介绍几个子模块：</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<ul style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li><span style="font-size:12px">Kafka API layer</span></li><li><span style="font-size:12px">LogManager and Log</span></li><li><span style="font-size:12px">ReplicaManager</span></li><li><span style="font-size:12px">ZookeeperConsumerConnector</span></li><li><span style="font-size:12px">service Schedule</span></li></ul>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-size:12px">如下是系统几个模块如何组成到一起架构图：</span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><img src="https://img-blog.csdn.net/20140803144704215?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</div>
<span style="font-size:24px; color:#ff0000"><strong>23）apache kafka源码分析走读-kafka整体结构分析</strong></span>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">kafka源代码工程目录结构如下图：</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px"><img src="https://img-blog.csdn.net/20140803205201428?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">下面只对core目录结构作说明，其他都是测试类或java客户端代码</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"></span></span></p>
<pre style="white-space:pre-wrap; word-wrap:normal; overflow:auto; font-family:Consolas,'Liberation Mono',Menlo,Courier,monospace; margin-top:15px; border:1px solid rgb(221,221,221); line-height:19px; padding:6px 10px; color:rgb(51,51,51); margin-bottom:0px!important; background-color:rgb(248,248,248)"><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>admin</strong></span>      --管理员模块，操作和管理topic，paritions相关，包含create,delete topic,扩展patitions</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px">
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>Api</strong></span>       --该模块主要负责组装数据，组装2种类型数据， </span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="white-space:pre">		</span>1.读取或解码客户端发送的二进制数据.</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="white-space:pre"></span><span style="white-space:pre">		</span>2.编码log消息数据，组装为需要发送的数据。</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px">
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>client</strong></span><span style="white-space:pre"> </span>  <span style="white-space:pre"></span> --该模块比较简单，就一个类，Producer读取kafka broker元数据信息，</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="white-space:pre">		</span>topic和partitions，以及leader
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px">
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>cluster</strong></span>   --该模块包含几个实体类，Broker,Cluster,Partition,Replica,解释他们之间关系：Cluster由多个broker组成，一个Broker包含多个partition，一个                                 topic的所有</span><span style="font-size:10px">partitions分布在不同broker的中，一个Replica包含多个Partition。</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px">
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>common</strong></span><span style="white-space:pre"> </span>    --通用模块,只包含异常类和错误验证</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px">
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>consumer</strong></span>    --consumer处理模块，负责所有客户端消费者数据和逻辑处理</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px">
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>contoroller</strong></span>  --负责中央控制器选举，partition的leader选举，副本分配，副本重新分配，</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="white-space:pre">		</span>partition和replica扩容。</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px">
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>javaapi</strong></span><span style="white-space:pre"> </span>     --提供java的producer和consumer接口api</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px">
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>log</strong></span>          --kafka文件系统，负责处理和存储所有kafka的topic数据。</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px">
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>message</strong></span>    --封装kafka的ByteBufferMessageSet</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px">
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>metrics</strong></span>    --<span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; line-height:20.7999992370605px">内部状态的监控模块</span>
</span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; line-height:20.7999992370605px"><span style="font-size:10px">
</span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>network</strong></span>           --网络事件处理模块，负责处理和接收客户端连接</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px">
</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>producer</strong></span>          --producer实现模块，包括同步和异步发送消息。</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px">
</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>serializer</strong></span>         --序列化或反序列化当前消息
</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px">
</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>kafka</strong></span>           --kafka门面入口类，副本管理，topic配置管理，leader选举实现(由contoroller模块调用)。</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px">
</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>tools</strong></span>           --一看这就是工具模块，包含内容比较多：</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px"><span style="white-space:pre">			</span>a.导出对应consumer的offset值.</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px"><span style="white-space:pre">			</span>b.导出LogSegments信息，当前<span style="white-space:pre"></span>topic的log写的位置信息.</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px"><span style="white-space:pre">			</span>c.导出zk上所有consumer的offset值.</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px"><span style="white-space:pre">			</span>d.修改注册在zk的consumer的offset值.</span></span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="line-height:20.7999992370605px; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="font-size:10px"><span style="white-space:pre">			</span>f.producer和consumer的使用例子.</span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="line-height:20.7999992370605px; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="font-size:10px">
</span></span></p><p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px"><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif"><span style="line-height:20.7999992370605px"><span style="font-size:10px"><span style="color:rgb(51,51,255)"><strong>utils</strong></span><span style="white-space:pre">		</span>  <span style="white-space:pre"></span>--Json工具类，Zkutils工具类，Utils创建线程工具类，KafkaScheduler公共调度器类，公共日志类等等。</span></span></span></p></pre>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">1.kafka启动类：kafka.scala</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">kafka为kafka broker的main启动类，其主要作用为加载配置，启动report服务(</span><span style="font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; line-height:20.7999992370605px">内部状态的监控</span><span style="font-size:18px">)，注册释放资源的钩子，以及门面入口类。</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
kafka类代码如下：</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<pre><code class="language-java">......
 try {
      val props = Utils.loadProps(args(0))          //加载配置文件
      val serverConfig = new KafkaConfig(props)
      KafkaMetricsReporter.startReporters(serverConfig.props)             //启动report服务(内部状态的监控)
      val kafkaServerStartble = new KafkaServerStartable(serverConfig)    //kafka server核心入口类
      // attach shutdown handler to catch control-c
      Runtime.getRuntime().addShutdownHook(new Thread() {                 //钩子程序，当jvm退出前，销毁所有资源
        override def run() = {
          kafkaServerStartble.shutdown
        }
      })

      kafkaServerStartble.startup
      kafkaServerStartble.awaitShutdown
    }
......</code></pre>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,51,255)">KafkaServerStartble</span><strong>类包装了</strong><span style="color:rgb(51,51,255)">KafkaSever</span><strong>类，其实啥都没有做。只是调用包装类而已</strong><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,51,255)">KafkaSever</span><strong>类是kafka broker运行控制的核心入口类，它是采用门面模式设计的。</strong><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px"><span style="font-weight:bold"><span style="font-size:12px"><img src="https://img-blog.csdn.net/20140803222531978?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</span></span></span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">kafka中KafkaServer类，采用门面模式，是网络处理，io处理等得入口.</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">ReplicaManager  <span style="white-space:pre"> </span>
 副本管理<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">KafkaApis<span style="white-space:pre"> </span>   <span style="white-space:pre"></span>api处理<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">KafkaRequestHandlerPool<span style="white-space:pre"></span>kafka  请求处理池  &lt;-- num.io.threads io线程数量<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">LogManager    </span><span style="color:rgb(51,51,51); font-family:Consolas,'Liberation Mono',Menlo,Courier,monospace; line-height:19px; white-space:pre-wrap; background-color:rgb(248,248,248)"><span style="font-size:12px">kafka文件系统，负责处理和存储所有kafka的topic数据</span></span><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">TopicConfigManager<span style="white-space:pre"> </span>
 topic管理<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">KafkaHealthcheck<span style="white-space:pre"> </span>
 健康检查<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">KafkaController<span style="white-space:pre"> </span>
 kafka集群中央控制器选举，leader选举，副本分配。<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">KafkaScheduler<span style="white-space:pre"> </span>
 负责副本管理和日志管理调度等等<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">ZkClient         负责注册zk相关信息.<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">BrokerTopicStats<span style="white-space:pre"> </span>
 topic信息统计和监控<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">ControllerStats          中央控制器统计和监控<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px"><br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">KafkaServer部分主要代码如下：</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px"></span></p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/37911993#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/37911993#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/441740" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/441740/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:4250px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">......    </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">def startup() {  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    info(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"starting"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    isShuttingDown = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> AtomicBoolean(</span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    shutdownLatch = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> CountDownLatch(</span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/* start scheduler */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    kafkaScheduler.startup()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/* setup zookeeper */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    zkClient = initZk()  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/* start log manager */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    logManager = createLogManager(zkClient)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    logManager.startup()  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    socketServer = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> SocketServer(config.brokerId,  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                                    config.hostName,  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                                    config.port,  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                                    config.numNetworkThreads,  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                                    config.queuedMaxRequests,  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                                    config.socketSendBufferBytes,  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                                    config.socketReceiveBufferBytes,  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                                    config.socketRequestMaxBytes)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    socketServer.startup()  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    replicaManager = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ReplicaManager(config, time, zkClient, kafkaScheduler, logManager, isShuttingDown)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    kafkaController = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> KafkaController(config, zkClient)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/* start processing requests */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    apis = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> KafkaApis(socketServer.requestChannel, replicaManager, zkClient, config.brokerId, config, kafkaController)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    requestHandlerPool = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> KafkaRequestHandlerPool(config.brokerId, socketServer.requestChannel, apis, config.numIoThreads)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">     </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    Mx4jLoader.maybeLoad()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    replicaManager.startup()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    kafkaController.startup()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    topicConfigManager = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> TopicConfigManager(zkClient, logManager)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    topicConfigManager.startup()  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/* tell everyone we are alive */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    kafkaHealthcheck = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> KafkaHealthcheck(config.brokerId, config.advertisedHostName, config.advertisedPort, config.zkSessionTimeoutMs, zkClient)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    kafkaHealthcheck.startup()  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    registerStats()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    startupComplete.set(<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">true</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    info(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"started"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> def initZk(): ZkClient = {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    info(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Connecting to zookeeper on "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + config.zkConnect)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    val zkClient = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ZkClient(config.zkConnect, config.zkSessionTimeoutMs, config.zkConnectionTimeoutMs, ZKStringSerializer)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    ZkUtils.setupCommonPaths(zkClient)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    zkClient  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">   *  Forces some dynamic jmx beans to be registered on server startup.</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">   */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> def registerStats() {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    BrokerTopicStats.getBrokerAllTopicsStats()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    ControllerStats.uncleanLeaderElectionRate  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    ControllerStats.leaderElectionTimer  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">.......  </span></li></ol>
</div>
<p><span style="font-size:24px; color:#ff0000"><strong>24）apache kafka源码分析走读-Producer分析</strong></span></p>
<p></p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px">producer的发送方式剖析</h1>
<p></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
Kafka提供了Producer类作为java producer的api，该类有sync和async两种发送方式。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
sync架构图</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px"><img src="https://img-blog.csdn.net/20140808144251703?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">async架构图</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px"><img src="https://img-blog.csdn.net/20140808144504718?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">调用流程如下：</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px"><img src="https://img-blog.csdn.net/20140808173819422?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px"><br>
</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">代码流程如下：</span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
Producer:当new Producer(new ProducerConfig()),其底层实现，实际会产生两个核心类的实例：Producer、DefaultEventHandler。在创建的同时，会默认new一个ProducerPool，即我们每new一个java的Producer类，就会有创建Producer、EventHandler和ProducerPool，ProducerPool为连接不同kafka broker的池，初始连接个数有broker.list参数决定。<br>
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
调用producer.send方法流程：</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
当应用程序调用producer.send方法时，其内部其实调的是eventhandler.handle(message)方法,eventHandler会首先序列化该消息,<br>
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
eventHandler.serialize(events)--&gt;dispatchSerializedData()--&gt;partitionAndCollate()--&gt;send()--&gt;SyncProducer.send()<br>
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
调用逻辑解释：当客户端应用程序调用producer发送消息messages时(既可以发送单条消息，也可以发送List多条消息)，调用eventhandler.serialize首先序列化所有消息，序列化操作用户可以自定义实现Encoder接口，下一步调用partitionAndCollate根据topics的messages进行分组操作，messages分配给dataPerBroker(多个不同的Broker的Map)，根据不同Broker调用不同的SyncProducer.send批量发送消息数据，SyncProducer包装了nio网络操作信息。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<br>
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
Producer的sync与async发送消息处理，大家看以上架构图一目了然。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<br>
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
partitionAndCollate方法详细作用:获取所有partitions的leader所在leaderBrokerId(就是在该partiionid的leader分布在哪个broker上),</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
创建一个HashMap&lt;int, Map&lt;TopicAndPartition, List&lt;KeyedMessage&lt;K,Message&gt;&gt;&gt;&gt;,把messages按照brokerId分组组装数据，然后为SyncProducer分别发送消息作准备工作。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<br>
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
名称解释：partKey:分区关键字，当客户端应用程序实现Partitioner接口时，传入参数key为分区关键字，根据key和numPartitions，返回分区(partitions)索引。记住partitions分区索引是从0开始的。</p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a>Producer平滑扩容机制</h1>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">如果开发过producer客户端代码，会知道metadata.broker.list参数，它的含义是kafak broker的ip和port列表，producer初始化时，就连接这几个broker，这时大家会有疑问，producer支持kafka cluster新增broker节点？它又没有监听zk broker节点或从zk中获取broker信息，答案是肯定的，producer可以支持平滑扩容broker，他是通过定时与现有的metadata.broker.list通信，获取新增broker信息，然后把新建的SyncProducer放入ProducerPool中。等待后续应用程序调用。</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">DefaultEventHandler类中初始化实例化BrokerPartitionInfo类，然后定期brokerPartitionInfo.updateInfo方法，DefaultEventHandler部分代码如下：<br>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; font-size:12px; width:774.599975585938px; overflow:auto; padding-top:1px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38438123#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38438123#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/445971" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/445971/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:2900px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">def handle(events: Seq[KeyedMessage[K,V]]) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  ......  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">while</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (remainingRetries &gt; </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> &amp;&amp; outstandingProduceRequests.size &gt; </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    topicMetadataToRefresh ++= outstandingProduceRequests.map(_.topic)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (topicMetadataRefreshInterval &gt;= </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> &amp;&amp;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        SystemTime.milliseconds - lastTopicMetadataRefreshTime &gt; topicMetadataRefreshInterval) {  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      Utils.swallowError(brokerPartitionInfo.updateInfo(topicMetadataToRefresh.toSet, correlationId.getAndIncrement))  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      sendPartitionPerTopicCache.clear()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      topicMetadataToRefresh.clear  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      lastTopicMetadataRefreshTime = SystemTime.milliseconds  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    outstandingProduceRequests = dispatchSerializedData(outstandingProduceRequests)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (outstandingProduceRequests.size &gt; </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      info(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Back off for %d ms before retrying send. Remaining retries = %d"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.format(config.retryBackoffMs, remainingRetries-</span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">))  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//休眠时间，多长时间刷新一次</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      Thread.sleep(config.retryBackoffMs)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 生产者定期请求刷新最新topics的broker元数据信息</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      Utils.swallowError(brokerPartitionInfo.updateInfo(outstandingProduceRequests.map(_.topic).toSet, correlationId.getAndIncrement))  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      .....  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">}  </span></li></ol>
</div>
<span style="font-size:18px">BrokerPartitionInfo的updateInfo方法代码如下：</span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-size:18px"></span>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; font-size:12px; width:774.599975585938px; overflow:auto; padding-top:1px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38438123#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38438123#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/445971" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/445971/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:3458px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">def updateInfo(topics: Set[String], correlationId: Int) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  var topicsMetadata: Seq[TopicMetadata] = Nil  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//根据topics列表,meta.broker.list,其他配置参数,correlationId表示请求次数，一个计数器参数而已</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//创建一个topicMetadataRequest，并随机的选取传入的broker信息中任何一个去取metadata，直到取到为止</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  val topicMetadataResponse = ClientUtils.fetchTopicMetadata(topics, brokers, producerConfig, correlationId)  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  topicsMetadata = topicMetadataResponse.topicsMetadata  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// throw partition specific exception</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  topicsMetadata.foreach(tmd =&gt;{  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    trace(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Metadata for topic %s is %s"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.format(tmd.topic, tmd))  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(tmd.errorCode == ErrorMapping.NoError) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      topicPartitionInfo.put(tmd.topic, tmd)  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">else</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      warn(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Error while fetching metadata [%s] for topic [%s]: %s "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.format(tmd, tmd.topic, ErrorMapping.exceptionFor(tmd.errorCode).getClass))  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    tmd.partitionsMetadata.foreach(pmd =&gt;{  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (pmd.errorCode != ErrorMapping.NoError &amp;&amp; pmd.errorCode == ErrorMapping.LeaderNotAvailableCode) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        warn(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Error while fetching metadata %s for topic partition [%s,%d]: [%s]"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.format(pmd, tmd.topic, pmd.partitionId,  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          ErrorMapping.exceptionFor(pmd.errorCode).getClass))  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      } <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// any other error code (e.g. ReplicaNotAvailable) can be ignored since the producer does not need to access the replica and isr metadata</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    })  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  })  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  producerPool.updateProducer(topicsMetadata)  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">}  </span></li></ol>
</div>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<div><span style="font-size:18px">ClientUtils.fetchTopicMetadata方法代码：</span><br>
</div>
<div>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; font-size:12px; width:774.599975585938px; overflow:auto; padding-top:1px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38438123#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38438123#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/445971" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/445971/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:4032px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">def fetchTopicMetadata(topics: Set[String], brokers: Seq[Broker], producerConfig: ProducerConfig, correlationId: Int): TopicMetadataResponse = {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  var fetchMetaDataSucceeded: Boolean = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  var i: Int = <span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  val topicMetadataRequest = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> TopicMetadataRequest(TopicMetadataRequest.CurrentVersion, correlationId, producerConfig.clientId, topics.toSeq)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  var topicMetadataResponse: TopicMetadataResponse = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  var t: Throwable = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  val shuffledBrokers = Random.shuffle(brokers) <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//生成随机数</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">while</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(i &lt; shuffledBrokers.size &amp;&amp; !fetchMetaDataSucceeded) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//对随机选到的broker会创建一个SyncProducer</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    val producer: SyncProducer = ProducerPool.createSyncProducer(producerConfig, shuffledBrokers(i))  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    info(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Fetching metadata from broker %s with correlation id %d for %d topic(s) %s"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.format(shuffledBrokers(i), correlationId, topics.size, topics))  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//发送topicMetadataRequest到该broker去取metadata，获得该topic所对应的所有的broker信息</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      topicMetadataResponse = producer.send(topicMetadataRequest)  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      fetchMetaDataSucceeded = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">true</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      ......  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(!fetchMetaDataSucceeded) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">throw</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> KafkaException(</span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"fetching topic metadata for topics [%s] from broker [%s] failed"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.format(topics, shuffledBrokers), t)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">else</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    debug(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Successfully fetched metadata for %d topic(s) %s"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.format(topics.size, topics))  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> topicMetadataResponse  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">}  </span></li></ol>
</div>
</div>
<span style="font-size:18px">ProducerPool的updateProducer</span><br>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; font-size:12px; width:774.599975585938px; overflow:auto; padding-top:1px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38438123#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38438123#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/445971" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/445971/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:4626px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">def updateProducer(topicMetadata: Seq[TopicMetadata]) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    val newBrokers = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> collection.mutable.HashSet[Broker]  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    topicMetadata.foreach(tmd =&gt; {  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      tmd.partitionsMetadata.foreach(pmd =&gt; {  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(pmd.leader.isDefined)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          newBrokers+=(pmd.leader.get)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      })  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    })  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    lock <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">synchronized</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      newBrokers.foreach(b =&gt; {  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(syncProducers.contains(b.id)){  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          syncProducers(b.id).close()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          syncProducers.put(b.id, ProducerPool.createSyncProducer(config, b))  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">else</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          syncProducers.put(b.id, ProducerPool.createSyncProducer(config, b))  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      })  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  }  </span></li></ol>
</div>
<br>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
当我们启动kafka broker后，并且大量producer和consumer时，经常会报如下异常信息。</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:18px; color:rgb(255,0,0)"><strong>root@lizhitao:/opt/soft$ Closing socket connection to 192.168.11.166</strong></span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong></strong></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="color:rgb(51,51,51)">笔者也是经常很长时间看源码分析，才明白了为什么ProducerConfig配置信息里面并不要求使用者提供完整的kafka集群的broker信息，而是任选一个或几个即可。因为他会通过您选择的broker和topics信息而获取最新的所有的broker信息。</span></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="color:rgb(51,51,51)">值得了解的是用于发送TopicMetadataRequest的SyncProducer虽然是用ProducerPool.createSyncProducer方法建出来的，但用完并不还回ProducerPool，而是直接Close.</span></p>
</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><span style="font-size:24px; color:rgb(255,102,0)"><strong>重难点理解：</strong></span></div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">刷新metadata并不仅在第一次初始化时做。为了能适应kafka broker运行中因为各种原因挂掉、paritition改变等变化，</div>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">eventHandler会定期的再去刷新一次该metadata，刷新的间隔用参数topic.metadata.refresh.interval.ms定义，默认值是10分钟。<br>
这里有三点需要强调：<br>
<ul>
<li>客户端调用send, 才会新建SyncProducer，只有调用send才会去定期刷新metadata</li><li>在每次取metadata时，kafka会新建一个SyncProducer去取metadata，逻辑处理完后再close。</li><li>根据当前SyncProducer(一个Broker的连接)取得的最新的完整的metadata，刷新ProducerPool中到broker的连接.</li><li>每10分钟的刷新会直接重新把到每个broker的socket连接重建，意味着在这之后的第一个请求会有几百毫秒的延迟。如果不想要该延迟，把topic.metadata.refresh.interval.ms值改为-1，这样只有在发送失败时，才会重新刷新。Kafka的集群中如果某个partition所在的broker挂了，可以检查错误后重启重新加入集群，手动做rebalance，producer的连接会再次断掉，直到rebalance完成，那么刷新后取到的连接着中就会有这个新加入的broker。</li></ul>
<div>说明：每个SyncProducer实例化对象会建立一个socket连接</div>
<div><span style="font-size:24px; color:rgb(255,102,0)"><strong>特别注意:</strong></span></div>
在ClientUtils.fetchTopicMetadata调用完成后，回到BrokerPartitionInfo.updateInfo继续执行，在其末尾，pool会根据上面取得的最新的metadata建立所有的SyncProducer，即Socket通道producerPool.updateProducer(topicsMetadata)<br>
在ProducerPool中，SyncProducer的数目是由该topic的partition数目控制的，即每一个SyncProducer对应一个broker，内部封了一个到该broker的socket连接。每次刷新时，会把已存在SyncProducer给close掉，即关闭socket连接，然后新建SyncProducer，即新建socket连接，去覆盖老的。<br>
如果不存在，则直接创建新的。</div>
<br>
<strong><span style="font-size:24px; color:#ff0000">25）apache kafka性能优化架构分析</span></strong>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:24px">Apache kafka性能优化架构分析</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140808151200678?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px; color:rgb(51,102,255)">应用程序优化：数据压缩</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140808151242190?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140808151306479?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140808151409503?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140808151517831?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:18px">consumer offset默认情况下是定时批量更新topics的partitions offset值</span></p>
<br>
<p><span style="font-size:24px; color:#ff0000"><strong>26）apache kafka源码分析走读-server端网络架构分析</strong></span></p>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
笔者今天分析一下kafka网络架构，俗话说人无好的胫骨，就没有好的身体，建筑没有扎实可靠的结构框架，就不会屹立不倒。同样的服务端程序没有好的网络架构，其性能就会受到极大影响，其他方面再怎么优化，也会受限于此，那kafka网络架构是怎样的呢，它不是用的现今流行的netty，mina的高性能网络架构，而是自己基于java nio开发的。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
kafka网络架构图如下：</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<img src="https://img-blog.csdn.net/20140808181112124?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"></p>
<br>
<span style="font-size:24px; color:#ff0000"><strong>27）apache kafka源码分析走读-ZookeeperConsumerConnector分析</strong></span>
<p></p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><span style="font-size:18px">1.ZookeeperConsumer架构</span></h1>
<p></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
ZookeeperConsumer类中consumer运行过程架构图：</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<img src="https://img-blog.csdn.net/20140809174809543?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"></p>
</blockquote>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="white-space:pre"></span>                                                                                                <span style="font-size:18px; color:rgb(255,0,0)">图1</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
过程分析：</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(51,51,51); font-size:13.63636302948px; line-height:20px; white-space:nowrap"><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/37811291#t5" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">ConsumerGroupExample类</a></span><br>
</p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a><span style="font-size:18px; color:rgb(51,102,255)">2.消费者线程(consumer thread),队列，拉取线程(fetch thread)三者之间关系</span></h1>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
每一个topic至少需要创建一个consumer thread，如果有多个partitions，则可以创建多个consumer thread线程，consumer thread&gt;==partitions数量，否则会有consumer thread空闲。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
部分代码示例如下：</p>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
ConsumerConnector consumer</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
consumer = kafka.consumer.Consumer.createJavaConsumerConnector(</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
            createConsumerConfig());</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 Map&lt;String, Integer&gt; topicCountMap = new HashMap&lt;String, Integer&gt;();</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 topicCountMap.put("test-string-topic", new Integer(1));  //value表示consumer thread线程数量</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 Map&lt;String, List&lt;KafkaStream&lt;byte[], byte[]&gt;&gt;&gt; consumerMap = consumer.createMessageStreams(topicCountMap);</p>
</blockquote>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
具体说明一下三者关系：</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
(1).topic的partitions分布规则</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
paritions是安装kafka brokerId有序分配的。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
例如现在有三个node安装了kafka broker服务端程序，brokerId分别设置为1,2,3，现在准备一个topic为test-string-topic，并且分配12个partitons，此时partitions的kafka broker节点分布情况为 ，partitions索引编号为0,3,6,9等4个partitions在brokerId=1上，1,4,7,10在brokerId=2上，2,5,8,11在brokerId=3上。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
创建consumer thread</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
consumer thread数量与BlockingQueue一一对应。<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
a.当consumer thread count=1时</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
此时有一个blockingQueue1，三个fetch thread线程，该topic分布在几个node上就有几个fetch thread，每个fetch thread会于kafka broker建立一个连接。3个fetch thread线程去拉取消息数据，最终放到blockingQueue1中，等待consumer thread来消费。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
消费者线程，缓冲队列，partitions分布列表如下</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<table cellspacing="0" cellpadding="0" style="color:rgb(0,0,0); font-family:Arial; font-size:14.3999996185303px; line-height:26px; border-collapse:collapse">
<tbody>
<tr>
<td valign="top" style="width:100px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px; color:rgb(255,38,0)">consumer</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px; color:rgb(255,38,0)">线程</span></p>
</td>
<td valign="top" style="width:97px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px; color:rgb(255,38,0)">Blocking Queue</span></p>
</td>
<td valign="top" style="width:130px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px; color:rgb(255,38,0)">partitions</span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:100px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">consumer thread1</span></span></p>
</td>
<td valign="top" style="width:97px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">blockingQueue1</span></span></p>
</td>
<td valign="top" style="width:130px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">0,1,2,3,4,5,6,7,8,9,10,11</span></span></p>
</td>
</tr>
</tbody>
</table>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; line-height:26px; font-size:11.8181819915771px">
<span style="font-size:14px">fetch thread与</span><span style="font-size:14px">partitions分布列表如下</span><br>
</p>
<table cellspacing="0" cellpadding="0" style="color:rgb(0,0,0); font-family:Arial; font-size:14.3999996185303px; line-height:26px; border-collapse:collapse">
<tbody>
<tr>
<td valign="top" style="width:94px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px; color:rgb(255,38,0)">fetch</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px; color:rgb(255,38,0)">线程</span></p>
</td>
<td valign="top" style="width:73px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px; color:rgb(255,38,0)">partitions</span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:94px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">fetch thread1</span></span></p>
</td>
<td valign="top" style="width:73px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">0,3,6,9</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:94px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">fetch thread2</span></span></p>
</td>
<td valign="top" style="width:73px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">1,4,7,10</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:94px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">fetch thread3</span></span></p>
</td>
<td valign="top" style="width:73px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">2,5,8,11</span></span></p>
</td>
</tr>
</tbody>
</table>
<br style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
b. 当consumer thread count=2时</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
此时有consumerThread1和consumerThread2分别对应2个队列blockingQueue1，blockingQueue2,这2个消费者线程消费partitions依次为:0,1,2,3,4,5与6,7,8,9,10,11;消费者线程，缓冲队列，partitions分布列表如下</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<table cellspacing="0" cellpadding="0" style="color:rgb(0,0,0); font-family:Arial; font-size:14.3999996185303px; line-height:26px; border-collapse:collapse">
<tbody>
<tr>
<td valign="top" style="width:100px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="color:rgb(255,0,0)"><span style="font-family:Helvetica; letter-spacing:0px">consumer</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">线程</span></span></p>
</td>
<td valign="top" style="width:97px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(255,0,0)">Blocking Queue</span></span></p>
</td>
<td valign="top" style="width:76px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(255,0,0)">partitions</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:100px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">consumer thread1</span></span></p>
</td>
<td valign="top" style="width:97px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">blockingQueue1</span></span></p>
</td>
<td valign="top" style="width:76px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">0,1,2,3,4,5</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:100px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">consumer thread2</span></span></p>
</td>
<td valign="top" style="width:97px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">blockingQueue2</span></span></p>
</td>
<td valign="top" style="width:76px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">6,7,8,9,10,11</span></span></p>
</td>
</tr>
</tbody>
</table>
<br style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
fetch thread与partitions分布列表如下</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<table cellspacing="0" cellpadding="0" style="color:rgb(0,0,0); font-family:Arial; font-size:14.3999996185303px; line-height:26px; border-collapse:collapse">
<tbody>
<tr>
<td valign="top" style="width:94px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="color:rgb(255,0,0)"><span style="font-family:Helvetica; letter-spacing:0px">fetch</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">线程</span></span></p>
</td>
<td valign="top" style="width:73px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(255,0,0)">partitions</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:94px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">fetch thread1</span></span></p>
</td>
<td valign="top" style="width:73px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">0,3,6,9</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:94px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">fetch thread2</span></span></p>
</td>
<td valign="top" style="width:73px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">1,4,7,10</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:94px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">fetch thread3</span></span></p>
</td>
<td valign="top" style="width:73px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">2,5,8,11</span></span></p>
</td>
</tr>
</tbody>
</table>
<br style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
c. 当consumer thread count=4时<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
消费者线程，缓冲队列，partitions分布列表如下<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<table cellspacing="0" cellpadding="0" style="color:rgb(0,0,0); font-family:Arial; font-size:14.3999996185303px; line-height:26px; border-collapse:collapse">
<tbody>
<tr>
<td valign="top" style="width:100px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="color:rgb(255,0,0)"><span style="font-family:Helvetica; letter-spacing:0px">consumer</span><span style="font-family:'Heiti SC Light'; letter-spacing:0px">线程</span></span></p>
</td>
<td valign="top" style="width:97px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(255,0,0)">Blocking Queue</span></span></p>
</td>
<td valign="top" style="width:76px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(255,0,0)">partitions</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:100px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">consumer thread1</span></span></p>
</td>
<td valign="top" style="width:97px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">blockingQueue1</span></span></p>
</td>
<td valign="top" style="width:76px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">0,1,2</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:100px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">consumer thread2</span></span></p>
</td>
<td valign="top" style="width:97px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">blockingQueue2</span></span></p>
</td>
<td valign="top" style="width:76px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">3,4,5</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:100px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">consumer thread3</span></span></p>
</td>
<td valign="top" style="width:97px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">blockingQueue3</span></span></p>
</td>
<td valign="top" style="width:76px; height:13px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">6,7,8</span></span></p>
</td>
</tr>
<tr>
<td valign="top" style="width:100px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">consumer thread4</span></span></p>
</td>
<td valign="top" style="width:97px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">blockingQueue4</span></span></p>
</td>
<td valign="top" style="width:76px; height:14px; border:1px solid rgb(0,0,0); padding:4px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-family:Helvetica; letter-spacing:0px"><span style="color:rgb(51,51,255)">9,10,11</span></span></p>
</td>
</tr>
</tbody>
</table>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
fetch thread与partitions分布列表如下<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
同上<br>
<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
同理当消费线程consumer thread count=n,都是安装上述分布规则来处理的。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<br>
</p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t4" style="color:rgb(255,153,0)"></a><span style="font-size:18px"><span style="color:rgb(51,102,255)">3.consumer消息线程以及队列创建逻辑</span></span></h1>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">运用ZookeeperConsumerConnector类创建多线程并行消费测试类，ConsumerGroupExample类初始化，调用createMessageStreams方法，实际是在consume方法处理的逻辑，创建KafkaStream,以及阻塞队列(LinkedBlockingQueue),KafkaStream与队列个数一一对应，消费者线程数量决定阻塞队列的个数。</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">registerConsumerInZK()方法：设置消费者组，注册消费者信息consumerIdString到zookeeper上。</span><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">consumerIdString产生规则部分代码如下:<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px"></span></p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38458631#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38458631#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/471073" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/471073/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:2892px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">String consumerUuid = </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(config.consumerId!=</span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> &amp;&amp; config.consumerId)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"> consumerUuid = consumerId;  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">else</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {   </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"> String uuid = UUID.randomUUID()  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">   </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  consumerUuid = <span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"%s-%d-%s"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.format(  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    InetAddress.getLocalHost.getHostName, System.currentTimeMillis,  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    uuid.getMostSignificantBits().toHexString.substring(<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">,</span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">8</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">));  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">}      </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">String consumerIdString =  config.groupId + <span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"_"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + consumerUuid;  </span></span></li></ol>
</div>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
kafka zookeeper注册模型结构或存储结构如下：<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/23744675" rel="nofollow" style="color:rgb(255,153,0); text-decoration:none">kafka在zookeeper中存储结构</a>           </p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
说明：目前把kafka中绝大部分存储模型都列表出来了，当前还有少量不常使用的，暂时还没有列举，后续会加上。</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
consumer初始化逻辑处理：</p>
<span style="font-family:Arial; font-size:14px; line-height:26px">1.实例化并注册loadBalancerListener监听，ZKRebalancerListener监听<span style="background-color:rgb(240,240,240)">consumerIdString状态变化</span></span><br style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
 </p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:13.63636302948px">触发consumer reblance条件如下几个：</span><br>
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:13.63636302948px">ZKRebalancerListener：当<span style="font-size:13.63636302948px">/kafka01/consumer</span></span><span style="font-size:13.63636302948px">/[consumer-group]/ids</span><span style="font-size:13.63636302948px">子节点变化时，会触发</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:13.63636302948px">ZKTopicPartitionChangeListener：当该topic的partitions发生变化时，会触发。<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:13.63636302948px">      val topicPath = "/kafka01/brokers/topics" + "/" + "topic-1"<br>
      zkClient.subscribeDataChanges(topicPath, topicPartitionChangeListener)<br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px"><br>
</span></p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
consumer reblance逻辑</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
consumer offset更新机制</p>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-size:12px">reblance计算规则：（有待补充）</span></p>
<br>
<p><span style="font-size:24px; color:#ff0000"><strong>28）kafka的ZkUtils类的java版本部分代码</strong></span></p>
<p></p>
<div class="bar" style="padding-left:45px; font-family:Consolas,'Courier New',Courier,mono,serif; line-height:26px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38518527#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/38518527#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/448747" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/448747/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:451px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); font-family:Consolas,'Courier New',Courier,mono,serif; line-height:26px; margin:0px 0px 1px 45px!important">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit"> * Created with IntelliJ IDEA.</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit"> * User: lizhitao</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit"> * Date: 14-6-6</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit"> * Time: 下午3:01</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit"> * To change this template use File | Settings | File Templates.</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit"> */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">class</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> TestMafkaZkUtils {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Logger logger = Logger.getLogger(TestMafkaZkUtils.</span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">class</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**********   kafka zk root conf   *********/</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String ConsumersPath = </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/consumers"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String BrokerIdsPath = </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/brokers/ids"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String BrokerTopicsPath = </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/brokers/topics"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String TopicConfigPath = </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/config/topics"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String TopicConfigChangesPath = </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/config/changes"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String ControllerPath = </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/controller"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String ControllerEpochPath = </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/controller_epoch"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String ReassignPartitionsPath = </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/admin/reassign_partitions"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String DeleteTopicsPath = </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/admin/delete_topics"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String PreferredReplicaLeaderElectionPath = </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/admin/preferred_replica_election"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String getTopicPath(String topic) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  BrokerTopicsPath + </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + topic;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String getTopicPartitionsPath(String topic) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">   getTopicPath(topic) +  </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/partitions"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String getTopicConfigPath(String topic) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  TopicConfigPath + </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + topic;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String getDeleteTopicPath(String clusterName, String topic ) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">   DeleteTopicsPath + </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + topic;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String getBrokerIdsPath() {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  BrokerIdsPath;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> List&lt;MafkaBroker&gt; getAllBrokersInCluster(ZkClient zkClient, String clusterName) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (!pathExists(zkClient, getBrokerIdsPath())) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">throw</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ZkNoNodeException(getBrokerIdsPath());  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        List&lt;String&gt; brokerIds = getChildrenParentMayNotExist(zkClient, getBrokerIdsPath());  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        Collections.sort(brokerIds);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//                List&lt;String&gt;     MafkaBroker getBrokerInfo(ZkClient zkClient, int brokerId)</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        List&lt;MafkaBroker&gt; retList = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ArrayList&lt;MafkaBroker&gt;();  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">for</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (String brokerIdStr : brokerIds) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            MafkaBroker broker = getBrokerInfo(zkClient, Integer.valueOf(brokerIdStr));  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (broker!=</span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                retList.add(broker);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> retList;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String getMetadataBrokerList(ZkClient zkClient, String clusterName) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        List&lt;MafkaBroker&gt; brokers = TestMafkaZkUtils.getAllBrokersInCluster(zkClient, clusterName);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        StringBuffer sb = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> StringBuffer();  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">for</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (MafkaBroker broker : brokers) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            logger.info(broker);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (sb.length() &gt; </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                sb.append(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">","</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            sb.append(broker.getHost()).append(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">":"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">).append(broker.getPort());  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> sb.toString();  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * get children nodes name</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * @param zkClient zkClient</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * @param path full path</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * @return children nodes name or null while path not exist</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> List&lt;String&gt; getChildrenParentMayNotExist(ZkClient zkClient, String path) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> zkClient.getChildren(path);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (ZkNoNodeException e) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (Exception ex) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            logger.error(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"getChildrenParentMayNotExist invoke fail!"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">,ex);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * This API takes in a broker id, queries zookeeper for the broker metadata and returns the metadata for that broker</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * or throws an exception if the broker dies before the query to zookeeper finishes</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * @param brokerId The broker id</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * @param zkClient The zookeeper client connection</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * @return An optional MafkaBroker object encapsulating the broker metadata</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> MafkaBroker getBrokerInfo(ZkClient zkClient, </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> brokerId) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//        Pair&lt;String, Stat&gt;</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        String brokerInfoStr = readDataMaybeNull(zkClient, getBrokerIdsPath() + <span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"/"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + brokerId).getLeft();  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (StringUtils.isNotEmpty(brokerInfoStr)) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> MafkaBroker.createBroker(brokerId, brokerInfoStr);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">else</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">{  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Pair&lt;String, Stat&gt; readData(ZkClient client, String path) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        Stat stat = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Stat();  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        String dataStr = client.readData(path, stat);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Pair.of(dataStr, stat);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Pair&lt;String, Stat&gt; readDataMaybeNull(ZkClient client, String path) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        Stat stat = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Stat();  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        Pair&lt;String, Stat&gt; dataAndStat = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            dataAndStat = Pair.of((String)client.readData(path, stat), stat);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(ZkNoNodeException nkex) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Pair.of(</span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, stat);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(Exception ex) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            logger.error(ex);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> dataAndStat;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * Update the value of a persistent node with the given path and data.</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * create parrent directory if necessary. Never throw NodeExistException.</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> updateEphemeralPath(ZkClient client, String path, String data) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            client.writeData(path, data);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(ZkNoNodeException zkex) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            createParentPath(client, path);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            client.createEphemeral(path, data);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (Exception ex) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            logger.error(ex);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">boolean</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> deletePath(ZkClient client, String path) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> client.delete(path);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(ZkNoNodeException zkex) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// this can happen during a connection loss event, return normally</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            logger.info(path + <span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">" deleted during connection loss; this is ok"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (Exception ex) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            logger.error(ex);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> deletePathRecursive(ZkClient client, String path) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            client.deleteRecursive(path);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(ZkNoNodeException zkex) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// this can happen during a connection loss event, return normally</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            logger.info(path + <span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">" deleted during connection loss; this is ok"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (Exception ex) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            logger.error(ex);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> maybeDeletePath(String zkUrl, String dir) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            ZkClient zk = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ZkClient(zkUrl, </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">30</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">*</span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1000</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">30</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">*</span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1000</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> MafkaZKStrSerializer());  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            zk.deleteRecursive(dir);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            zk.close();  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(Exception ex) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            logger.error(ex);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     *  make sure a persistent path exists in ZK. Create the path if not exist.</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> makeSurePersistentPathExists(ZkClient client, String path) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (!client.exists(path))  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            client.createPersistent(path, <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">true</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">); </span><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// won't throw NoNodeException or NodeExistsException</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     *  create the parent path</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> createParentPath(ZkClient client, String path) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        String parentDir = path.substring(<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, path.lastIndexOf(</span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">'/'</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">));  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (parentDir.length() != </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            client.createPersistent(parentDir, <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">true</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * Create an ephemeral node with the given path and data. Create parents if necessary.</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> createEphemeralPath(ZkClient client, String path, String data) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            client.createEphemeral(path, data);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(ZkNoNodeException znex) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            createParentPath(client, path);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            client.createEphemeral(path, data);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * Create an ephemeral node with the given path and data.</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * Throw NodeExistException if node already exists.</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> createEphemeralPathExpectConflict(ZkClient client, String path, String data) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            createEphemeralPath(client, path, data);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(ZkNodeExistsException zkex) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// this can happen when there is connection loss; make sure the data is what we intend to write</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            String storedData = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                storedData = readData(client, path).getLeft();  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(ZkNoNodeException znex) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                logger.error(znex);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (storedData == </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> || storedData != data) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                logger.info(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"conflict in "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + path + </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">" data: "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + data + </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">" stored data: "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + storedData);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">throw</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> zkex;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">else</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// otherwise, the creation succeeded, return normally</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                logger.info(path + <span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">" exists with value "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + data + </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">" during connection loss; this is ok"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * Create an persistent node with the given path and data. Create parents if necessary.</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> createPersistentPath(ZkClient client, String path, String data) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            client.createPersistent(path, data);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(ZkNoNodeException znex) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            createParentPath(client, path);  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            client.createPersistent(path, data);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String createSequentialPersistentPath(ZkClient client, String path, String data) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> client.createPersistentSequential(path, data);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> List&lt;String&gt; getAllPartitionsByTopic(ZkClient zkClient, String topic) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> getChildren(zkClient, getTopicPartitionsPath(topic));  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * Check if the given path exists</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">boolean</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> pathExists(ZkClient zkClient, String path) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        logger.info(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"pathExists:"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + path+ </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">" zkClient:"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + zkClient);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> zkClient.exists(path);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">/**</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * 功能介绍：解析partitions列表数据,partitions以字符串方式存储，用逗号分隔。</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * @param zkClient</span> </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     * @return</span> </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">     */</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> String getAllPartitionsSepCommaByTopic(ZkClient zkClient,String topic) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        logger.info(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"getTopicPartitionsPath(clusterName, topic):"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + getTopicPartitionsPath(topic));  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (!pathExists(zkClient, getTopicPartitionsPath(topic))) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">throw</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ZkNoNodeException(getTopicPartitionsPath(topic));  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        List&lt;String&gt; partitions = getChildren(zkClient, getTopicPartitionsPath(topic));  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        Collections.sort(partitions,<span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Comparator&lt;String&gt;() {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="annotation" style="margin:0px; padding:0px; border:none; color:rgb(100,100,100); background-color:inherit">@Override</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> compare(String o1, String o2) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> p1 = ( o1 == </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ) ? </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> : Integer.parseInt(o1);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">final</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> p2 = ( o2 == </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ) ? </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> : Integer.parseInt(o2);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> NumberUtils.compare(p1, p2);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        });  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        StringBuffer parts = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> StringBuffer();  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">for</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ( String partition : partitions ) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (parts.length() &gt; </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                parts.append(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">","</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">);  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            parts.append(partition);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> parts.toString();  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> List&lt;String&gt; getChildren(ZkClient client, String path) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> client.getChildren(path);  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> List&lt;MafkaBroker&gt; getAllBrokersInCluster(ZkClient zkClient) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        List&lt;String&gt; brokerIds = getChildrenParentMayNotExist(zkClient, getBrokerIdsPath());  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        Collections.sort(brokerIds);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//                List&lt;String&gt;     MafkaBroker getBrokerInfo(ZkClient zkClient, int brokerId)</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        List&lt;MafkaBroker&gt; retList = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ArrayList&lt;MafkaBroker&gt;();  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">for</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (String brokerIdStr : brokerIds) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            MafkaBroker broker = getBrokerInfo(zkClient, Integer.valueOf(brokerIdStr));  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (broker!=</span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                retList.add(broker);  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> retList;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">public</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">static</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">void</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> main(String[] args) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        ZkClient zkClient;  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//kafka zk根节点</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        String zkConnect = <span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"192.168.2.225:2181,192.168.2.225:2182,192.168.2.225:2183/config/mobile/mq/mafka01"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> zkSessionTimeoutMs = </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">5000</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">int</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> zkConnectionTimeoutMs = </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">5000</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        zkClient = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ZkClient(zkConnect, zkSessionTimeoutMs, zkConnectionTimeoutMs, </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> MafkaZKStrSerializer());  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//获取所有broker信息</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        System.out.println(getAllBrokersInCluster(zkClient));  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">//获取所有partitions信息</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        System.out.println(getAllPartitionsSepCommaByTopic(zkClient, <span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"cluster-switch-topic"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">));  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">}  </span></li></ol>
<br>
<p></p>
<span style="font-size:24px; color:#ff0000"><strong>29）kafka &amp; mafka client开发与实践</strong></span>
<p><span style="white-space:pre"></span>请<a target="_blank" href="http://download.csdn.net/detail/zhongwen7710/8173117" rel="nofollow">单击这里下载</a>（下载网址：http://download.csdn.net/detail/zhongwen7710/8173117）</p>
<p><span style="font-size:24px; color:#ff0000"><strong>30)   kafka文件系统设计那些事</strong></span></p>
<p></p>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px">1.文件系统说明</h1>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:18px">文件系统一般分为系统和用户2种类型，系统级文件系统:ext3,ext4,dfs,ntfs等等,，笔者并不会向大家介绍那种纷繁复杂的分布式或系统级文件系统，而是从kafka架构高性能角度考虑，深入剖析kafka文件系统存储结构设计。</span></p>
</blockquote>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t3" style="color:rgb(255,153,0)"></a><br>
</h1>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t4" style="color:rgb(255,153,0)"></a>2.kafka文件系统架构</h1>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"><br>
</div>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t5" style="color:rgb(255,153,0)"></a>2.1 文件系统数据流</h2>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
下面用图形表示介绍客户端处理几个过程如下：</p>
</blockquote>
<p></p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<img src="https://img-blog.csdn.net/20141028175828919?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" width="770" height="415" alt="" style="border:none; max-width:100%"><br>
</p>
</blockquote>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
                                                            <span class="s1"><strong> <span style="color:rgb(255,0,0)">图1</span></strong></span></p>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li5">当建立连接请求时，首先客户端向kafka broker发送连接请求，broker中由Acceptor thread线程接收并建立连接后，把client的socket以轮询方式转交给相应的processor thread。</li><li class="li5">当client向broker发送数据请求，由processor thread处理并接收client数据放到request缓冲区中，以待IO thread进行逻辑处理和计算并把返回result放到response缓冲区中.<br>
接着唤醒processor thread，processor thread抱住response队列循环发送所有response数据给client.</li></ul>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t6" style="color:rgb(255,153,0)"></a>2.2 kafka文件系统存储结构</h2>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<img src="https://img-blog.csdn.net/20141028180007340?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" width="670" height="561" alt="" style="border:none; max-width:100%"><br>
</p>
</blockquote>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
                                                                                               <span class="s1"><strong><span style="font-size:18px; color:rgb(255,0,0)">图2</span></strong></span></p>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li5">paritions分布规则，kafka集群由多个kafka broker组成，一个topic的partitions会分布在一个或多个broker上，topic的partitions在kafka集群上分配规则为，安装paritions索引编号依次有序分布在broker上，<br>
当partitions数量 &gt; brokers数量，会依次轮回再次迭代分配。</li><li class="li5">partitions命名规则,paritions名称为:topic-name-index,  index分区索引编号，从0开始依次递增。</li><li class="li5">producer，每个producer可以发送msg到topic任意一个或多个partitons。</li><li class="li6"><span class="s2">consumer，</span>同一个Consumer Group中的Consumers，Kafka将相应Topic中的每个消息只发送给其中一个Consumer.</li></ul>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t7" style="color:rgb(255,153,0)"></a>2.3 kafka的文件系统结构-目录</h2>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
目前假如kafka集群中只有一个broker，数据文件目录为message-folder，例如笔者创建一个topic名称为：report_push,  partitions=4</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
存储路径和目录规则为：</p>
<p class="p7" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
xxx/message-folder</p>
<p class="p7" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
                              |--report_push-0</p>
<p class="p7" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
                              |--report_push-1</p>
<p class="p7" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
                              |--report_push-2</p>
<p class="p7" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
                              |--report_push-3</p>
<p class="p7" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
形象表示图如下：</p>
<p class="p7" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<img src="https://img-blog.csdn.net/20141028180258878?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" width="422" height="334" alt="" style="border:none; max-width:100%"><br>
</p>
</blockquote>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
                                   <span style="white-space:pre"> </span> <span class="s1"><strong><span style="color:rgb(255,0,0)">图3</span></strong></span></p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t8" style="color:rgb(255,153,0)"></a>2.4 kafka的文件系统结构-partiton文件存储方式</h2>
<div style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<blockquote style="margin:0px 0px 0px 40px; border:none; padding:0px"><img src="https://img-blog.csdn.net/20141028180537906?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" width="670" height="287" alt="" style="border:none; max-width:100%"><br>
</blockquote>
</div>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
                                                           <span class="s1"><strong><span style="color:rgb(255,0,0)">图4</span></strong></span></p>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
每个partition（topic-name-index)目录中存储海量msg消息，那它是怎么存储的呢？文件存储结构是怎样？</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
这么多(海量)消息是存储在一个大文件中，类似DB那样存储，还是其他方式存储结构呢？笔者后续会像剥洋葱一样，给大家一层一层依次分解并分析。</p>
</blockquote>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li8">数据库和kafka文件系统比较，相信大家都用过数据库，数据库底层文件系统相当复杂，因为数据库特点，需要按照关键字，id快速查询，修改，删除，日志，回滚等等。<br>
所以数据库文件系统是分页存储的树形结构，需要支持大量随机事物操作。<span class="s3">相比数据库支持查询，事物等等复杂文件，则kafka消息队列类型文件系统简单多了，kafka文件系统存储特点是，</span><br>
<span class="s3">只需要支持producer和consumer顺序生产和消息就够了，消息(msg)生命周期由consumer决定。</span></li><li class="li5">partiton文件存储结构分析，每个partition就像如上图4，一个巨大文件消息数据被平均分配到多个文件大小相等的文件中。即相当于一个大文件被切成很多相等大小的文件段<span class="s4">segment file</span><br>
(消息数量不一定相等)。因为每个topic中消息生命周期由最后一个consumer决定，当某个或些消息被最后一个consumer(consumer group)消息后，就可以删除该消息。显然易见，</li></ul>
<p class="p5" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
          这样做的目的是broker能快速回收磁盘空间，而且小文件也能mmap全部到内存。主要目的就是提高磁盘利用率和消息处理性能。</p>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t9" style="color:rgb(255,153,0)"></a>2.5 kafka的文件系统结构-partiton文件存储segment file组成</h2>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
读者从2.4节了解到kafka文件系统partition存储方式，下面向大家介绍一下partion文件存储中segement file组成结构。一个商业化消息队列的性能好坏，</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
其文件系统存储结构设计是衡量一个消息队列服务程序最关键指标之一，他也是消息队列中最核心且最能体现消息队列技术水平的部分。在本节中我们将走进segment file内部一探究竟。</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
segment file组成：由2大部分组成，分别为segment data file和segment index file，此2个文件一一对应，成对出现.</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
segment index file索引文件组成结构如下：</p>
<p class="p9" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span class="s2"> </span><strong>00000000000000000000.index       文件名称，文件串大小最大支持2^64bit</strong></p>
<table cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td valign="baseline" class="td1">
<p class="p10" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">每次记录相应log文件记录的相对条数和物理偏移位置位置，共8bytes</span></p>
<p class="p10" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span class="s5">4</span><span class="s2"></span><span class="s6"><strong>byte</strong></span><span class="s2"> </span>当前segment file offset - last seg file offset记录条数       offset</span></p>
<p class="p10" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px"><span class="s5">4</span><span class="s2"></span><span class="s6"><strong>byte</strong></span><span class="s2"></span>对应segment file物理偏移地址 position</span></p>
<p class="p10" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:14px">………</span></p>
</td>
</tr>
</tbody>
</table>
</blockquote>
<span style="font-family:Arial; font-size:14px; line-height:26px; color:rgb(255,0,0)">           segment data file索引文件组成结构如下：<br>
</span><span style="font-family:Arial; font-size:14.3999996185303px; line-height:26px"></span>
<p class="p9" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="color:rgb(255,0,0)"><span class="s2">      </span>     00000000000000000000.log<span class="s2">        </span><strong>文件名称，文件串大小最大支持2^64bit，与index对应</strong></span></p>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p9" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong><img src="https://img-blog.csdn.net/20141028180947957?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" width="670" height="392" alt="" style="border:none; max-width:100%"> 
    </strong></p>
</blockquote>
<p class="p9" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<strong><span style="white-space:pre"></span>                     <span style="white-space:pre"></span><span style="font-size:18px; color:rgb(255,0,0)">图5</span>      </strong></p>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p12" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<strong>参数说明：</strong></p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
4 byte CRC32：使用crc32算法计算除CRC32这4byte外的buffer。</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
1 byte “magic"：表示数据文件协议版本号</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
1 byte “attributes"：表示标识独立版本，标识压缩类型，编码类型。</p>
<p class="p5" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 key data：可选，可以存储判断或表示这个消息块的元数据信息。</p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
payload data：消息体，该消息体可能会存储多条消息记录，内部是按照序号有序存储的。</p>
</blockquote>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t10" style="color:rgb(255,153,0)"></a>2.6 kafka文件系统-consumer读取流程</h2>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:12px"><img src="https://img-blog.csdn.net/20141028181045397?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" width="710" height="517" alt="" style="border:none; max-width:100%"> </span></p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="font-size:12px"><span style="color:rgb(255,0,0); font-size:18.1818180084229px"><strong><span style="white-space:pre"></span><span style="white-space:pre"></span>图6</strong></span><br>
</span></p>
</blockquote>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
segment index file：</p>
<p class="p7" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
稀疏索引方式，减少索引文件大小，这样可以直接内存操作，稀疏索引只为数据文件的每个存储块设一个键-指针对,它比稠密索引节省了更多的存储空间，但查找给定值的记录需更多的时间，通过二分查找快速找到segment data file物理位置，如果在index file没有找到data file具体位置，则data file相对位置继续顺序读取查找，直到找到为止。</p>
</blockquote>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t11" style="color:rgb(255,153,0)"></a>2.7 kafka的文件系统结构-总体目录结构</h2>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<img src="https://img-blog.csdn.net/20141028181120855?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"></p>
</blockquote>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p12" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
 </p>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p13" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="white-space:pre"><span style="color:rgb(255,0,0); font-size:18.1818180084229px"><strong>图7</strong></span></span></p>
<p class="p13" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
同一个topic下有不同分区，每个分区下面会划分为多个(段)文件，只有一个当前文件在写，其他文件只读。当写满一个文件（写满的意思是达到设定值）则切换文件，新建一个当前文件用来写，老的当前文件切换为只读。文件的命名以起始偏移量来命名。看一个例子，假设report_push这个topic下的0-0分区可能有以下这些文件：</p>
<p class="p14" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 • 00000000000000000000.index</p>
<p class="p14" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 • 00000000000000000000.log </p>
<p class="p14" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 • 00000000000000368769.index </p>
<p class="p14" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 • 00000000000000368769.log </p>
<p class="p14" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 • 00000000000000737337.index </p>
<p class="p14" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 • 00000000000000737337.log</p>
<p class="p14" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 • 00000000000001105814.index</p>
<p class="p14" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
 • 00000000000001105814.log</p>
<p class="p14" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
    ………………..</p>
<p class="p13" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
其中 00000000000000000000.index表示最开始的文件，起始偏移量为0.第二个文件00000000000000368769.index的消息量起始偏移量为368769.同样，第三个文件00000000000000737337.index的起始偏移量为737337.</p>
<p class="p13" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
以起始偏移量命名并排序这些文件，那么当消费者要拉取某个消息起始偏移量位置的数据变的相当简单，只要根据传上来的offset**二分查找**文件列表，定位到具体文件，</p>
<p class="p13" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
然后将绝对offset减去文件的起始节点转化为相对offset，即可开始传输数据。例如，同样以上面的例子为例，假设消费者想抓取从第368969消息位置开始的数据，则根据368969二分查找，</p>
<p class="p13" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
定位到00000000000000368769.log这个文件（368969在368769和737337之间），根据索引文件二分搜索可以确定读取数据最大大小。</p>
</blockquote>
<h2 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t12" style="color:rgb(255,153,0)"></a>2.8 kafka文件系统–实际效果</h2>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<br>
</p>
<p class="p4" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<img src="https://img-blog.csdn.net/20141028181541189?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGl6aGl0YW8=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border:none; max-width:100%"></p>
</blockquote>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<blockquote style="font-family:Arial; font-size:14.3999996185303px; line-height:26px; margin:0px 0px 0px 40px; border:none; padding:0px">
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
<span style="white-space:pre"></span>  <span style="white-space:pre"></span>                                                  <span style="white-space:pre"><span style="color:rgb(255,0,0); font-size:18.1818180084229px"><strong>图8</strong></span></span>   </p>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px">
基本不会有磁盘读的大量操作，都在内存进行，只有定期磁盘批量写操作。</p>
</blockquote>
<h1 style="margin:0px; padding:0px; font-family:Arial; line-height:26px"><a target="_blank" name="t13" style="color:rgb(255,153,0)"></a>3.总结</h1>
<p class="p2" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span class="s7"> <span style="white-space:pre"></span></span>高效文件系统特点</p>
<ul class="ul1" style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<li class="li5">一个大文件分成多个小文件段。</li><li class="li5">多个小文件段，容易定时清除或删除已经消费完文件，减少磁盘占用。</li><li class="li5">index全部映射到memory直接操作，避免segment file被交换到磁盘增加IO操作次数。</li><li class="li5">根据索引信息，可以确定发送response到consumer的最大大小。</li><li class="li5">索引文件元数据存储用的是相对前一个segment file的offset存储，节省空间大小。</li></ul>
<p><span style="font-size:24px; color:#ff0000"><strong>31）kafka的ZookeeperConsumer实现</strong></span></p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
kafka的ZookeeperConsumer数据获取的步骤如下：</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
入口ZookeeperConsumerConnector def consume[T](topicCountMap: scala.collection.Map[String,Int], decoder: Decoder[T])<br>
: Map[String,List[KafkaStream[T]]] 方法<br>
客户端启动后会在消费者注册目录上添加子节点变化的监听ZKRebalancerListener，ZKRebalancerListener实例会在内部创建一个线程，这个线程定时检查监听的事件有没有执行（消费者发生变化）,如果没有变化则wait1秒钟，当发生了变化就调用 syncedRebalance 方法，去rebalance消费者。</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/502981" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/502981/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:622px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">while</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (!isShuttingDown.get) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            lock.lock()  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (!isWatcherTriggered)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                cond.await(<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1000</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, TimeUnit.MILLISECONDS) </span><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// wake up periodically so that it can check the shutdown flag</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">finally</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              doRebalance = isWatcherTriggered  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              isWatcherTriggered = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              lock.unlock()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (doRebalance)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              syncedRebalance  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">case</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> t =&gt; error(</span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"error during syncedRebalance"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, t)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          }  </span></li></ol>
</div>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
syncedRebalance方法在内部会调用def rebalance(cluster: Cluster): Boolean方法，去执行操作。<br>
这个方法的伪代码如下：</p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/502981" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/502981/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:1040px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">while</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (!isShuttingDown.get) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            lock.lock()  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (!isWatcherTriggered)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                cond.await(<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1000</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, TimeUnit.MILLISECONDS) </span><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// wake up periodically so that it can check the shutdown flag</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">finally</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              doRebalance = isWatcherTriggered  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              isWatcherTriggered = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              lock.unlock()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (doRebalance)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              syncedRebalance  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">catch</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">case</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> t =&gt; error(</span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"error during syncedRebalance"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">, t)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          }  </span></li></ol>
</div>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
syncedRebalance方法在内部会调用def rebalance(cluster: Cluster): Boolean方法，去执行操作。<br>
这个方法的伪代码如下：</p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/502981" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/502981/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:1458px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 关闭所有的数据获取者</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">closeFetchers  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 解除分区的所有者</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">releasePartitionOwnership  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 按规则得到当前消费者拥有的分区信息并保存到topicRegistry中</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">topicRegistry=getCurrentConsumerPartitionInfo  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 修改并重启Fetchers</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">updateFetchers  </span></li></ol>
</div>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
updateFetcher是这样实现的。</p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/502981" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/502981/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:1695px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">private</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> def updateFetcher(cluster: Cluster) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 遍历topicRegistry中保存的当前消费者的分区信息，修改Fetcher的partitions信息 </span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      var allPartitionInfos : List[PartitionTopicInfo] = Nil  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">for</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (partitionInfos &lt;- topicRegistry.values)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">for</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (partition &lt;- partitionInfos.values)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          allPartitionInfos ::= partition  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      info(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Consumer "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + consumerIdString + </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">" selected partitions : "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> +  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        allPartitionInfos.sortWith((s,t) =&gt; s.partition &lt; t.partition).map(_.toString).mkString(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">","</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">))  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      fetcher match {  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">case</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Some(f) =&gt;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 调用fetcher的startConnections方法，初始化Fetcher并启动它</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          f.startConnections(allPartitionInfos, cluster)  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">case</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> None =&gt;  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li></ol>
</div>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
Fetcher在startConnections时，它先把topicInfo按brokerid去分组</p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/502981" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/502981/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:2073px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">for</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(info &lt;- topicInfos) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      m.get(info.brokerId) match {  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">case</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> None =&gt; m.put(info.brokerId, List(info))  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">case</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Some(lst) =&gt; m.put(info.brokerId, info :: lst)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li></ol>
</div>
<span style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">然后检查每组topicInfo对应的broker是否在当前集群中注册了</span>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/502981" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/502981/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:2275px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">val brokers = ids.map { id =&gt;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      cluster.getBroker(id) match {  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">case</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> Some(broker) =&gt; broker  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">case</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> None =&gt; </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">throw</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> IllegalStateException(</span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Broker "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + id + </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">" is unavailable, fetchers could not be started"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li></ol>
</div>
<span style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">最后对每个broker创建一个FetcherRunnable线程，并启动它。这个线程负责从服务器上不断获取数据，把数据插入内部阻塞队列的操作。</span>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
// 对每个分区分别创建FetchRequest</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/502981" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/502981/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:2542px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">val fetches = partitionTopicInfos.map(info =&gt;  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> FetchRequest(info.topic, info.partition.partId, info.getFetchOffset, config.fetchSize))  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 批量执行fetch操作</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        val response = simpleConsumer.multifetch(fetches : _*)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">....  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 遍历返回获取到的数据</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">for</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">((messages, infopti) &lt;- response.zip(partitionTopicInfos)) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">try</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            var done = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">false</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 当zk中存放的offset值不在kafka机器上存在时，比如consumer好久没有启动，相应的offset的数据已经在kafka集群中被过期删除清理掉了</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(messages.getErrorCode == ErrorMapping.OffsetOutOfRangeCode) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              info(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"offset for "</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> + infopti + </span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">" out of range"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// see if we can fix this error</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              val resetOffset = resetConsumerOffsets(infopti.topic, infopti.partition)  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(resetOffset &gt;= </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                infopti.resetFetchOffset(resetOffset)  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                infopti.resetConsumeOffset(resetOffset)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                done = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">true</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 如果成功了，把消息放到队列中，实际上是把当前分区信息、当前获取到的消息、当前获取使用的fetchoffset封装FetchedDataChunk对象，放到分区消息对象的内部队列中（chunkQueue.put(new FetchedDataChunk(messages, this, fetchOffset))）。</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">            <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (!done)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">              read += infopti.enqueue(messages, infopti.getFetchOffset)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          }  </span></li></ol>
</div>
<span style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">客户端用ConsumerIterator不断的从分区信息的内部队列中取数据。ConsumerIterator实现了IteratorTemplate的接口，它的内部保存一个Iterator的属性current，每次调用makeNext时会检查它，如果有则从中取否则从队列中取。</span>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/502981" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/502981/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:3158px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">protected</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> def makeNext(): MessageAndMetadata[T] = {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    var currentDataChunk: FetchedDataChunk = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// if we don't have an iterator, get one，从内部变量中取数据</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    var localCurrent = current.get()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(localCurrent == </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> || !localCurrent.hasNext) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 内部变量中取不到值，检查timeout的值</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (consumerTimeoutMs &lt; </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        currentDataChunk = channel.take <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 是负数(-1)，则表示永不过期，如果接下来无新数据可取，客户端线程会在channel.take阻塞住</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">else</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 设置了过期时间，在没有新数据可用时，pool会在相应的时间返回，返回值为空，则说明没有取到新数据，抛出timeout的异常</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        currentDataChunk = channel.poll(consumerTimeoutMs, TimeUnit.MILLISECONDS)  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (currentDataChunk == </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">null</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">) {  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          <span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// reset state to make the iterator re-iterable</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          resetState()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">throw</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> ConsumerTimeoutException  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// kafka把shutdown的命令也做为一个datachunk放到队列中，用这种方法来保证消息的顺序性</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(currentDataChunk eq ZookeeperConsumerConnector.shutdownCommand) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        debug(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Received the shutdown command"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        channel.offer(currentDataChunk)  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">return</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> allDone  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      } <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">else</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        currentTopicInfo = currentDataChunk.topicInfo  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (currentTopicInfo.getConsumeOffset != currentDataChunk.fetchOffset) {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          error(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"consumed offset: %d doesn't match fetch offset: %d for %s;\n Consumer may lose data"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                        .format(currentTopicInfo.getConsumeOffset, currentDataChunk.fetchOffset, currentTopicInfo))  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">          currentTopicInfo.resetConsumeOffset(currentDataChunk.fetchOffset)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 把取出chunk中的消息转化为iterator</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        localCurrent = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> (enableShallowIterator) currentDataChunk.messages.shallowIterator  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">                       <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">else</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> currentDataChunk.messages.iterator  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 使用这个新的iterator初始化current，下次可直接从current中取数据</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">        current.set(localCurrent)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      }  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    }  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 取出下一条数据，并用下一条数据的offset值设置consumedOffset</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    val item = localCurrent.next()  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    consumedOffset = item.offset  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 解码消息，封装消息和它的topic信息到MessageAndMetadata对象，返回</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> MessageAndMetadata(decoder.toEvent(item.message), currentTopicInfo.topic)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  }  </span></li></ol>
</div>
<span style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">ConsumerIterator的next方法</span>
<p style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
</p>
<div class="dp-highlighter bg_java" style="font-family:Consolas,'Courier New',Courier,mono,serif; width:774.599975585938px; overflow:auto; padding-top:1px; line-height:26px; margin:18px 0px!important; background-color:rgb(231,229,220)">
<div class="bar" style="padding-left:45px">
<div class="tools" style="padding:3px 8px 10px 10px; font-size:9px; line-height:normal; font-family:Verdana,Geneva,Arial,Helvetica,sans-serif; color:silver; border-left-width:3px; border-left-style:solid; border-left-color:rgb(108,226,108); background-color:rgb(248,248,248)">
<strong>[java]</strong> <a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="ViewSource" title="view plain" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">view
 plain</a><a target="_blank" href="http://blog.csdn.net/lizhitao/article/details/40650989#" rel="nofollow" class="CopyToClipboard" title="copy" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; text-indent:-2000px; background-color:inherit">copy</a><a target="_blank" href="https://code.csdn.net/snippets/502981" rel="nofollow" title="在CODE上查看代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border:none; max-width:100%; position:relative; top:1px; left:2px"></a><a target="_blank" href="https://code.csdn.net/snippets/502981/fork" rel="nofollow" title="派生到我的代码片" style="color:rgb(160,160,160); text-decoration:none; border:none; padding:1px; margin:0px 10px 0px 0px; font-size:9px; display:inline-block; width:16px; height:16px; background-color:inherit"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border:none; max-width:100%; position:relative; top:2px; left:2px"></a>
<div style="position:absolute; left:376px; top:4024px; width:18px; height:18px; z-index:99">
</div>
</div>
</div>
<ol start="1" class="dp-j" style="padding:0px; border:none; list-style-position:initial; color:rgb(92,92,92); margin:0px 0px 1px 45px!important; background-color:rgb(255,255,255)">
<li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span style="margin:0px; padding:0px; border:none; background-color:inherit">  override def next(): MessageAndMetadata[T] = {  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    val item = <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">super</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.next()  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">if</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">(consumedOffset &lt; </span><span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">0</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">      <span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">throw</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> </span><span class="keyword" style="margin:0px; padding:0px; border:none; color:rgb(0,102,153); font-weight:bold; background-color:inherit">new</span><span style="margin:0px; padding:0px; border:none; background-color:inherit"> IllegalStateException(</span><span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Offset returned by the message set is invalid %d"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.format(consumedOffset))  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 使用makeNext方法设置的consumedOffset，去修改topicInfo的消费offset</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    currentTopicInfo.resetConsumeOffset(consumedOffset)  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    val topic = currentTopicInfo.topic  </span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    trace(<span class="string" style="margin:0px; padding:0px; border:none; color:blue; background-color:inherit">"Setting %s consumed offset to %d"</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">.format(topic, consumedOffset))  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    ConsumerTopicStat.getConsumerTopicStat(topic).recordMessagesPerTopic(<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    ConsumerTopicStat.getConsumerAllTopicStat().recordMessagesPerTopic(<span class="number" style="margin:0px; padding:0px; border:none; color:rgb(192,0,0); background-color:inherit">1</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">)  </span></span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit"><span class="comment" style="margin:0px; padding:0px; border:none; color:rgb(0,130,0); background-color:inherit">// 返回makeNext得到的item</span><span style="margin:0px; padding:0px; border:none; background-color:inherit">  </span></span></li><li style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important; background-color:rgb(248,248,248)">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">    item  </span></li><li class="alt" style="border-style:none none none solid; border-left-width:3px; border-left-color:rgb(108,226,108); list-style:decimal-leading-zero outside; color:inherit; line-height:18px; margin:0px!important; padding:0px 3px 0px 10px!important">
<span style="margin:0px; padding:0px; border:none; color:black; background-color:inherit">  }  </span></li></ol>
</div>
<span style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">KafkaStream对ConsumerIterator做了进一步的封装，我们调用stream的next方法就可以取到数据了（内部通过调用ConsumerIterator的next方法实现）</span><br style="font-family:Arial; font-size:14.3999996185303px; line-height:26px">
<span style="font-family:Arial; line-height:26px; font-size:18px"><span style="color:rgb(255,0,0)"><strong>注意：</strong></span><br>
ConsumerIterator的实现可能会造成数据的重复发送（这要看生产者如何生产数据），FetchedDataChunk是一个数据集合，它内部会包含很多数据块，一个数据块可能包含多条消息，但同一个数据块中的消息只有一个offset，所以当一个消息块有多条数据，处理完部分数据发生异常时，消费者重新去取数据，就会再次取得这个数据块，然后消费过的数据就会被重新消费。</span>
<p class="p1" style="margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; font-family:Arial; font-size:14.3999996185303px; line-height:26px">
这篇文章转载自田加国：http://www.tianjiaguo.com/system-architecture/kafka/kafka的zookeeperconsumer实现/</p>
<br>
<p>以上文章来自网络整理，可以参看：<span style="color:rgb(51,51,51); font-family:微软雅黑,Verdana,sans-serif,宋体; font-size:12.8000001907349px; line-height:26px">http://blog.csdn.net/lizhitao/article/details/39499283</span></p>
<div style="top:5436px">
<div class="syntaxhighlighter nogutter  java" style="font-family:Arial; font-size:14.3999996185303px; margin:0px; padding:0px; line-height:20px">
</div>
</div>
            </div>
                </div>