---
layout:     post
title:      Hadoop之HDFS核心知识点
---
<div id="article_content" class="article_content clearfix csdn-tracking-statistics" data-pid="blog" data-mod="popu_307" data-dsm="post">
								            <div id="content_views" class="markdown_views prism-atom-one-dark">
							<!-- flowchart 箭头图标 勿删 -->
							<svg xmlns="http://www.w3.org/2000/svg" style="display: none;"><path stroke-linecap="round" d="M5,0 0,2.5 5,5z" id="raphael-marker-block" style="-webkit-tap-highlight-color: rgba(0, 0, 0, 0);"></path></svg>
							<div id="topics">
    <div class="post">
        <h1 class="postTitle" id="初步掌握hdfs的架构及原理">
            <a id="cb_post_title_url" class="postTitle2" href="https://www.cnblogs.com/codeOfLife/p/5375120.html" rel="nofollow">初步掌握HDFS的架构及原理</a>

        </h1>
        <div class="clear"></div>
        <div class="postBody">
            <div id="cnblogs_post_body" class="blogpost-body">
            <p><span>原文链接：https://www.cnblogs.com/codeOfLife/p/5375120.html</span></p>
            <p><span>目录 </span></p>
<ul>
<li>
<div><a href="#HDFS%E6%98%AF%E5%81%9A%E4%BB%80%E4%B9%88%E7%9A%84" rel="nofollow">HDFS 是做什么的</a></div>
</li>
<li>
<div><a href="#HDFS%E4%BB%8E%E4%BD%95%E8%80%8C%E6%9D%A5" rel="nofollow">HDFS 从何而来</a></div>
</li>
<li>
<div><a href="#%E4%B8%BA%E4%BB%80%E4%B9%88%E9%80%89%E6%8B%A9HDFS%E5%AD%98%E5%82%A8%E6%95%B0%E6%8D%AE" rel="nofollow">为什么选择 HDFS 存储数据</a></div>
</li>
<li>
<div><a href="#HDFS%E5%A6%82%E4%BD%95%E5%AD%98%E5%82%A8%E6%95%B0%E6%8D%AE" rel="nofollow">HDFS 如何存储数据</a></div>
</li>
<li>
<div><a href="#HDFS%E5%A6%82%E4%BD%95%E8%AF%BB%E5%8F%96%E6%96%87%E4%BB%B6" rel="nofollow">HDFS 如何读取文件</a></div>
</li>
<li>
<div><a href="#HDFS%E5%A6%82%E4%BD%95%E5%86%99%E5%85%A5%E6%96%87%E4%BB%B6" rel="nofollow">HDFS 如何写入文件</a></div>
</li>
<li>
<div><a href="#HDFS%E5%89%AF%E6%9C%AC%E5%AD%98%E6%94%BE%E7%AD%96%E7%95%A5" rel="nofollow">HDFS 副本存放策略</a></div>
</li>
<li>
<div><a href="#hadoop2x%E6%96%B0%E7%89%B9%E6%80%A7" rel="nofollow">Hadoop2.x新特性</a></div>
</li>
</ul>
<p><span>1、<a></a>HDFS 是做什么的 </span></p>
<p><span>　　</span><span>HDFS（Hadoop Distributed File System）是Hadoop项目的核心子项目，是分布式计算中数据存储管理的基础，是基于流数据模式访问和处理超大文件的需求而开发的，可以运行于廉价的商用服务器上。它所具有的高容错、高可靠性、高可扩展性、高获得性、高吞吐率等特征为海量数据提供了不怕故障的存储，为超大数据集（Large Data Set）的应用处理带来了很多便利</span>。</p>
<p><span>2、<a></a>HDFS 从何而来 </span></p>
<p>　　HDFS 源于 Google 在2003年10月份发表的GFS（Google File System） 论文。 它其实就是 GFS 的一个克隆版本</p>
<p><span>3、<a></a>为什么选择 HDFS 存储数据 </span></p>
<p><span>　  </span><span>之所以选择 HDFS 存储数据，因为 HDFS 具有以下优点： </span></p>
<p>　　1、<span>高容错性 </span></p>
<ul>
<li>
<div>数据自动保存多个副本。它通过增加副本的形式，提高容错性。</div>
</li>
<li>
<div>某一个副本丢失以后，它可以自动恢复，这是由 HDFS 内部机制实现的，我们不必关心。</div>
</li>
</ul>
<p><span> 　　2、适合批处理 </span></p>
<ul>
<li>
<div>它是通过移动计算而不是移动数据。</div>
</li>
<li>
<div>它会把数据位置暴露给计算框架。</div>
</li>
</ul>
<p><span>　　3、适合大数据处理 </span></p>
<ul>
<li>
<div>处理数据达到 GB、TB、甚至PB级别的数据。</div>
</li>
<li>
<div>能够处理百万规模以上的文件数量，数量相当之大。</div>
</li>
<li>
<div>能够处理10K节点的规模。</div>
</li>
</ul>
<p><span>　　4、流式文件访问 </span></p>
<ul>
<li>
<div>一次写入，多次读取。文件一旦写入不能修改，只能追加。</div>
</li>
<li>
<div>它能保证数据的一致性。</div>
</li>
</ul>
<p><span> 　　5、可构建在廉价机器上 </span></p>
<ul>
<li>
<div>它通过多副本机制，提高可靠性。</div>
</li>
<li>
<div>它提供了容错和恢复机制。比如某一个副本丢失，可以通过其它副本来恢复。</div>
</li>
</ul>
<p><span> 　　当然 HDFS 也有它的劣势，并不适合所有的场合： </span></p>
<p><span> 　　1、低延时数据访问 </span></p>
<ul>
<li>
<div>比如毫秒级的来存储数据，这是不行的，它做不到。</div>
</li>
<li>
<div>它适合高吞吐率的场景，就是在某一时间内写入大量的数据。但是它在低延时的情况下是不行的，比如毫秒级以内读取数据，这样它是很难做到的。</div>
</li>
</ul>
<p><span> 　　2、小文件存储 </span></p>
<ul>
<li>
<div>存储大量小文件(这里的小文件是指小于HDFS系统的Block大小的文件（默认64M）)的话，它会占用 NameNode大量的内存来存储文件、目录和块信息。这样是不可取的，因为NameNode的内存总是有限的。</div>
</li>
<li>
<div>小文件存储的寻道时间会超过读取时间，它违反了HDFS的设计目标。</div>
</li>
</ul>
<p><span>　　3、并发写入、文件随机修改 </span></p>
<ul>
<li>
<div>一个文件只能有一个写，不允许多个线程同时写。</div>
</li>
<li>
<div>仅支持数据 append（追加），不支持文件的随机修改。</div>
</li>
</ul>
<p><span>4、<a></a>HDFS 如何存储数据</span></p>
<p><span>　　<img src="https://images2015.cnblogs.com/blog/615800/201604/615800-20160410194709656-653161719.jpg" alt=""></span></p>
<p>　　　　　　　　　　　　　　　　　　HDFS的架构图</p>
<p>　　HDFS 采用Master/Slave的架构来存储数据，这种架构主要由四个部分组成，分别为HDFS Client、NameNode、DataNode和Secondary NameNode。下面我们分别介绍这四个组成部分   </p>
<p>　　1、Client：就是客户端。</p>
<ul>
<li>文件切分。文件上传 HDFS 的时候，Client 将文件切分成 一个一个的Block，然后进行存储。</li>
<li>与 NameNode 交互，获取文件的位置信息。</li>
<li>与 DataNode 交互，读取或者写入数据。</li>
<li>Client 提供一些命令来管理 HDFS，比如启动或者关闭HDFS。</li>
<li>Client 可以通过一些命令来访问 HDFS。</li>
</ul>
<p>　　2、NameNode：就是 master，它是一个主管、管理者。</p>
<ul>
<li>管理 HDFS 的名称空间</li>
<li>管理数据块（Block）映射信息</li>
<li>配置副本策略</li>
<li>处理客户端读写请求。</li>
</ul>
<p>　　3、DataNode：就是Slave。NameNode 下达命令，DataNode 执行实际的操作。</p>
<ul>
<li>存储实际的数据块。</li>
<li>执行数据块的读/写操作。</li>
</ul>
<p>　　4、Secondary NameNode：并非 NameNode 的热备。当NameNode 挂掉的时候，它并不能马上替换 NameNode 并提供服务。</p>
<ul>
<li>辅助 NameNode，分担其工作量。</li>
<li>定期合并 fsimage和fsedits，并推送给NameNode。</li>
<li>在紧急情况下，可辅助恢复 NameNode。</li>
</ul>
<p><span>5、<a></a>HDFS 如何读取文件 </span></p>
<p><img src="https://images2015.cnblogs.com/blog/615800/201604/615800-20160410194710625-1654660549.png" alt=""></p>
<p>HDFS的文件读取原理，主要包括以下几个步骤：</p>
<ul>
<li>首先调用FileSystem对象的open方法，其实获取的是一个DistributedFileSystem的实例。</li>
<li>DistributedFileSystem通过RPC(远程过程调用)获得文件的第一批block的locations，同一block按照重复数会返回多个locations，这些locations按照hadoop拓扑结构排序，距离客户端近的排在前面。</li>
<li>前两步会返回一个FSDataInputStream对象，该对象会被封装成 DFSInputStream对象，DFSInputStream可以方便的管理datanode和namenode数据流。客户端调用read方法，DFSInputStream就会找出离客户端最近的datanode并连接datanode。</li>
<li>数据从datanode源源不断的流向客户端。</li>
<li>如果第一个block块的数据读完了，就会关闭指向第一个block块的datanode连接，接着读取下一个block块。这些操作对客户端来说是透明的，从客户端的角度来看只是读一个持续不断的流。</li>
<li>如果第一批block都读完了，DFSInputStream就会去namenode拿下一批blocks的location，然后继续读，如果所有的block块都读完，这时就会关闭掉所有的流。</li>
</ul>
<p><span>6、<a></a>HDFS 如何写入文件 </span></p>
<p><img src="https://images2015.cnblogs.com/blog/615800/201604/615800-20160410194711468-990406077.png" alt=""></p>
<p><span>HDFS的文件写入原理，主要包括以下几个步骤：</span></p>
<ul>
<li><span>客户端通过调用 DistributedFileSystem 的create方法，创建一个新的文件。 </span></li>
<li><span>DistributedFileSystem 通过 RPC（远程过程调用）调用 NameNode，去创建一个没有blocks关联的新文件。创建前，NameNode 会做各种校验，比如文件是否存在，客户端有无权限去创建等。如果校验通过，NameNode 就会记录下新文件，否则就会抛出IO异常。 </span></li>
<li><span>前两步结束后会返回 FSDataOutputStream 的对象，和读文件的时候相似，FSDataOutputStream 被封装成 DFSOutputStream，DFSOutputStream 可以协调 NameNode和 DataNode。客户端开始写数据到DFSOutputStream,DFSOutputStream会把数据切成一个个小packet，然后排成队列 data queue。 </span></li>
<li><span>DataStreamer 会去处理接受 data queue，它先问询 NameNode 这个新的 block 最适合存储的在哪几个DataNode里，比如重复数是3，那么就找到3个最适合的 DataNode，把它们排成一个 pipeline。DataStreamer 把 packet 按队列输出到管道的第一个 DataNode 中，第一个 DataNode又把 packet 输出到第二个 DataNode 中，以此类推。 </span></li>
<li><span>DFSOutputStream 还有一个队列叫 ack queue，也是由 packet 组成，等待DataNode的收到响应，当pipeline中的所有DataNode都表示已经收到的时候，这时akc queue才会把对应的packet包移除掉。 </span></li>
<li><span>客户端完成写数据后，调用close方法关闭写入流。 </span></li>
<li><span>DataStreamer 把剩余的包都刷到 pipeline 里，然后等待 ack 信息，收到最后一个 ack 后，通知 DataNode 把文件标示为已完成。</span></li>
</ul>
<p><span>7、<a></a>HDFS 副本存放策略 </span></p>
<p>namenode如何选择在哪个datanode 存储副本（replication）？这里需要对可靠性、写入带宽和读取带宽进行权衡。Hadoop对datanode存储副本有自己的副本策略，在其发展过程中一共有两个版本的副本策略，分别如下所示</p>
<p><img src="https://images2015.cnblogs.com/blog/615800/201604/615800-20160410194712359-1360960663.jpg" alt=""></p>
<p><span>8、<a></a>hadoop2.x新特性 </span></p>
<ul>
<li><span>引入了NameNode Federation，解决了横向内存扩展 </span></li>
<li><span>引入了Namenode HA，解决了namenode单点故障</span></li>
<li>引入了YARN，负责资源管理和调度</li>
<li>
<div>增加了ResourceManager HA解决了ResourceManager单点故障</div>
</li>
</ul>
<p>　　1、NameNode Federation</p>
<p>    架构如下图</p>
<p>    <img src="https://images2015.cnblogs.com/blog/615800/201604/615800-20160410194713140-1298753008.png" alt=""></p>
<ul>
<li>存在多个NameNode，每个NameNode分管一部分目录</li>
<li>NameNode共用DataNode</li>
</ul>
<p>　　这样做的好处就是当NN内存受限时，能扩展内存，解决内存扩展问题，而且每个NN独立工作相互不受影响，比如其中一个NN挂掉啦，它不会影响其他NN提供服务，但我们需要注意的是，虽然有多个NN，分管不同的目录，但是对于特定的NN，依然存在单点故障，因为没有它没有热备，解决单点故障使用NameNode HA</p>
<p>　　2、NameNode HA</p>
<p>　　　　解决方案：</p>
<ul>
<li>基于NFS共享存储解决方案</li>
<li>基于Qurom Journal Manager(QJM)解决方案</li>
</ul>
<p>　　　　1、基于NFS方案</p>
<p>　　　　　　Active NN与Standby NN通过NFS实现共享数据，但如果Active NN与NFS之间或Standby NN与NFS之间，其中一处有网络故障的话，那就会造成数据同步问题</p>
<p>　　　　2、基于QJM方案</p>
<p>     　　架构如下图</p>
<p>     　　<img src="https://images2015.cnblogs.com/blog/615800/201604/615800-20160410194713922-1728782871.png" alt=""></p>
<p>    　　Active NN、Standby NN有主备之分，NN Active是主的，NN Standby备用的</p>
<p>    　　集群启动之后，一个namenode是active状态，来处理client与datanode之间的请求，并把相应的日志文件写到本地中或JN中；</p>
<p>    　　Active NN与Standby NN之间是通过一组JN共享数据（JN一般为奇数个，ZK一般也为奇数个），Active NN会把日志文件、镜像文件写到JN中去，只要JN中有一半写成功，那就表明Active NN向JN中写成功啦，Standby NN就开始从JN中读取数据，来实现与Active NN数据同步，这种方式支持容错，因为Standby NN在启动的时候，会加载镜像文件（fsimage）并周期性的从JN中获取日志文件来保持与Active NN同步</p>
<p>    　　为了实现Standby NN在Active NN挂掉之后，能迅速的再提供服务，需要DN不仅需要向Active NN汇报，同时还要向Standby NN汇报，这样就使得Standby NN能保存数据块在DN上的位置信息，因为在NameNode在启动过程中最费时工作，就是处理所有DN上的数据块的信息</p>
<p>    　　为了实现Active NN高热备，增加了FailoverController和ZK，FailoverController通过Heartbeat的方式与ZK通信，通过ZK来选举，一旦Active NN挂掉，就选取另一个FailoverController作为active状态，然后FailoverController通过rpc，让standby NN转变为Active NN</p>
<p>    　　FailoverController一方面监控NN的状态信息，一方面还向ZK定时发送心跳，使自己被选举。当自己被选为主（Active）的时候，就会通过rpc使相应NN转变Active状态</p>
<p><span>　　　　3、结合HDFS2的新特性，在实际生成环境中部署图 </span></p>
<p>　　<img src="https://images2015.cnblogs.com/blog/615800/201604/615800-20160410194714672-152842366.png" alt=""></p>
<p><span>　　　　这里有12个DN,有4个NN，NN-1与NN-2是主备关系，它们管理/share目录；NN-3与NN-4是主备关系，它们管理/user目录</span></p>
<p> </p>
<div id="ljc">
<div>
<p> 如果，您认为阅读这篇博客让您有些收获，不妨点击一下右下角的【<strong class="nb">推荐</strong>】。<br>
  如果，您希望更容易地发现我的新博客，不妨点击一下左下角的【<strong class="nb">关注我</strong>】。<br>
  如果，您对我的博客所讲述的内容有兴趣，请继续关注我的后续博客，我是【<a href="http://www.cnblogs.com/codeOfLife/" rel="nofollow" target="_blank"><strong class="nb">刘超★ljc</strong></a>】。</p>
<p>本文版权归作者和博客园共有，欢迎转载，但未经作者同意必须保留此段声明，且在文章页面明显位置给出原文连接，否则保留追究法律责任的权利。</p>




</div>

<p></p></div></div><div id="MySignature"></div>

<div class="clear"></div>
<div id="blog_post_info_block">
<div id="BlogPostCategory">分类: <a href="https://www.cnblogs.com/codeOfLife/category/811619.html" rel="nofollow" target="_blank">hadoop</a></div>
<div id="EntryTag">标签: <a href="https://www.cnblogs.com/codeOfLife/tag/HDFS/" rel="nofollow">HDFS</a>, <a href="https://www.cnblogs.com/codeOfLife/tag/HDFS%E6%9E%B6%E6%9E%84/" rel="nofollow">HDFS架构</a>, <a href="https://www.cnblogs.com/codeOfLife/tag/HDFS%E5%8E%9F%E7%90%86/" rel="nofollow">HDFS原理</a></div>
<div id="blog_post_info"><div id="green_channel">

</div>

<div id="author_profile">
    <div id="author_profile_info" class="author_profile_info">
       </div>
    </div>


</div>

<div class="clear"></div>

        </div>

    </div>  
</div></div>            </div>
						<link href="https://csdnimg.cn/release/phoenix/mdeditor/markdown_views-9e5741c4b9.css" rel="stylesheet">
                </div>