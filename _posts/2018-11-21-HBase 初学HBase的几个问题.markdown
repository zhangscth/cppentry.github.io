---
layout:     post
title:      HBase 初学HBase的几个问题
---
<div id="article_content" class="article_content clearfix csdn-tracking-statistics" data-pid="blog" data-mod="popu_307" data-dsm="post">
								            <div id="content_views" class="markdown_views prism-atom-one-dark">
							<!-- flowchart 箭头图标 勿删 -->
							<svg xmlns="http://www.w3.org/2000/svg" style="display: none;"><path stroke-linecap="round" d="M5,0 0,2.5 5,5z" id="raphael-marker-block" style="-webkit-tap-highlight-color: rgba(0, 0, 0, 0);"></path></svg>
							<p></p><div class="toc"><div class="toc">
<ul>
<li><ul>
<li><a href="#1-%E4%BB%80%E4%B9%88%E6%98%AFhbase" rel="nofollow" target="_blank">什么是HBase</a></li>
<li><a href="#2%E4%BD%95%E6%97%B6%E7%94%A8hbase" rel="nofollow" target="_blank">何时用HBase</a></li>
<li><a href="#%E5%92%8Chivepig%E7%9A%84%E5%8C%BA%E5%88%AB" rel="nofollow" target="_blank">和HivePig的区别</a></li>
<li><a href="#hbase%E7%9A%84%E7%BB%93%E6%9E%84" rel="nofollow" target="_blank">HBase的结构</a><ul>
<li><a href="#1%E8%A1%A8%E8%A1%8C%E5%88%97%E5%92%8C%E5%8D%95%E5%85%83%E6%A0%BC" rel="nofollow" target="_blank">1表行列和单元格</a></li>
<li><a href="#2%E8%87%AA%E5%8A%A8%E5%88%86%E5%8C%BA" rel="nofollow" target="_blank">2自动分区</a></li>
<li><a href="#3hbase%E5%AD%98%E5%82%A8%E6%A0%BC%E5%BC%8F" rel="nofollow" target="_blank">3HBase存储格式</a></li>
<li><a href="#4-wal%E9%A2%84%E5%86%99%E5%BC%8F%E6%97%A5%E5%BF%97" rel="nofollow" target="_blank"> WAL预写式日志</a></li>
<li><a href="#5hbase%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%84" rel="nofollow" target="_blank">5HBase系统架构</a></li>
</ul>
</li>
<li><a href="#%E4%B8%BA%E4%BD%95hbase%E9%80%9F%E5%BA%A6%E5%BE%88%E5%BF%AB" rel="nofollow" target="_blank">为何HBase速度很快</a></li>
<li><a href="#hbase%E5%B8%B8%E7%94%A8%E6%93%8D%E4%BD%9C" rel="nofollow" target="_blank">HBase常用操作</a></li>
</ul>
</li>
</ul>
</div>
</div>


<h2 id="1-什么是hbase">1. 什么是HBase?</h2>

<p>HBase，是Hadoop Database，是一个高可靠性、高性能、面向列、可伸缩的分布式存储系统。使用HBase技术可以在廉价的PC服务器上搭建起大规模结构化的存储集群。它底层的文件系统使用HDFS，使用Zookeeper来管理集群的HMaster和各Region server之间的通信，监控各Region server的状态，存储各Region的入口地址等。</p>



<h2 id="2何时用hbase">2.何时用HBase?</h2>

<p>首先想想传统的关系型数据库都有哪些特点，大概的特点有：</p>

<ol>
<li>支持事务，ACID（原子性、一致性、隔离性和持久性）特性；</li>
<li>行式存储；</li>
<li>SQL语句使用起来比较方便；</li>
<li>支持索引、视图等；</li>
</ol>

<p>接下来我们考虑一个场景：我们想要构建一个社交网站，我们可能会选择易于操作的LAMP（Linux、Apache、Mysql、PHP）模型来快速的搭建一个原型。随着用户数的不断增加，每天有越来越多的人开始访问，这时候，共享的数据库服务器压力会越来越大，可以选择增加应用服务器，但因为这些应用服务器共享中央数据库，所以，随着数据库的CPU和I/O负载升高，这种方案势必不可长久。</p>

<p>这时候，我们可能会增加从服务器，以便并行读取，将读写分离。这样做是因为考虑到用户访问产生的读次数比写入次数更多，但是如果用户数目增加很快，产生的内容越来越多，导致读写数目相差没那么大，这种方案也就不能长久。</p>

<p>接下来的常见做法就是增加缓存，比如使用Memcached。这样，读操作存入到内存中的数据库系统中，但又没办法保证数据一致性，因为用户更新数据到数据库，而数据库不会主动更新缓存中的数据，而且，这种方案只能解决读请求的压力，对于写请求，还是没有解决。所以需要更多的服务器，更快的磁盘，会导致硬件成本快速升高。</p>

<p>而且，随着用户的增多，网站功能势必增加，业务功能都会使用sql语句进行查询，而表数据过多会导致join操作变慢，所以会不得不采用一些逆范式的方式来设计数据库，这样导致无法使用存储过程。而且，数据过大时，索引的效果也没那么强了。因为索引也会变得很大。</p>

<p>这时候应该怎么办？有些人采用了数据库分区的方式，将数据拆分。但是大规模的拆分将导致大量复制操作，带来大量的I/O损耗。所以这种方式也不一定好。</p>

<p>03年，谷歌发表了一片论文叫做《The Google File System》，这个文件系统简称GFS，该文件系统中的数据在节点中冗余存储，即使一台服务器发生故障，也不会影响数据可用性。但是，GFS只适合存储少量非常大的文件，不适合存储数量众多的小文件，因为文件的元信息存储在主节点的内存中，文件越多，主节点压力越大。经过Google的深入研究，在06年，发表了另外一篇重量级论文《BigTable：A Distributed Storage System for Structed Data》。HBase就是BigTable的开源实现，当然，也建立在HDFS（GFS的开源实现）和Hadoop（MapReduce的开源实现）、Zookeeper（Chubby的开源实现）的基础上。</p>

<p>何时用HBase呢？在下面几种情况下，可以考虑使用HBase替代关系数据库：</p>

<ol>
<li>系统需要适应不同种类的数据格式和数据源，不能预先严格定义模式，需要处理大规模数据；</li>
<li>不强调数据之间的关系，所要存储的数据是半结构化或非结构化的；</li>
<li>数据非常稀疏；</li>
<li>想要更好的进行扩展；</li>
</ol>

<p>比如谷歌就将BigTable用来存储网页的索引数据，索引数据就很好的满足了上面的几点要求。</p>



<h2 id="和hivepig的区别">和Hive,Pig的区别？</h2>

<ol>
<li>HBase是低延迟、非结构化和面向编程的，而Hive是高延迟、结构化和面向分析的；</li>
<li>Hive本身不存储和计算数据，它完全依赖与HDFS和MapReduce，Hive中的表是逻辑表；</li>
<li>HBase通过组织起节点内所有机器的内存，提供一个超大的内存Hash表，它需要在磁盘和内存组织自己的数据结构，HBase中的表是物理表；</li>
<li>如果是全表扫描，就用Hive+Hadoop，如果是索引访问，就用HBase+Hadoop。</li>
<li>Hive主要用于静态的结构以及需要经常分析的工作；</li>
<li>Pig相比Hive相对轻量，它主要的优势是相对比于直接使用Hadoop Java APIs可大幅消减代码量；</li>
<li>Hive和Pig都可以与HBase组合使用，Hive和Pig还为HBase提供了高层语言支持，使得在HBase上进行数据统计处理变得非常简单。</li>
</ol>



<h2 id="hbase的结构">HBase的结构?</h2>

<h3 id="1表行列和单元格">1）表、行、列和单元格</h3>

<p>先做一个简单的总结：最基本的单位是列（column），一列或者多列组成一行（row），并且由唯一的行键（row key）来确定存储。一个表中有很多行，每一列可能有多个版本，在每一个单元格（Cell）中存储了不同的值。</p>

<p>HBase的行与行之间是有序的，按照row key的字典序进行排序，行键是唯一的，在一个表里只出现一次，否则就是在更新同一行，行键可以是任意的字节数组。一行由若干列组成，其中的某些列又可以构成一个列族（column family），一个列族的所有列存储在同一个底层的存储文件里，这个文件称之为HFile。</p>

<p>列族需要在创建表的时候就定义好，数量也不宜过多。列族名必须由可打印字符组成，创建表的时候不需要定义好列。对列的引用格式通常为family：qualifier，qualifier也可以是任意的字节数组。同一个列族里qualifier的名称应该唯一，否则就是在更新同一列，列的数量没有限制，可以有数百万个。列值也没有类型和长度限定。HBase会对row key的长度做检查，默认应该小于65536。</p>

<p>一个可视化的HBase表如下：</p>

<p><img src="https://img-blog.csdn.net/20140731121001213" alt="这里写图片描述" title=""></p>

<p>Timestamp代表时间戳，默认由系统指定，用户也可以显示设置。使用不同的时间戳来区分不同的版本。一个单元格的不同版本的值按照时间戳降序排列在一起，在读取的时候优先取最新的值。用户可以指定每个值能保存的最大版本数，HBase-0.96版本默认的最大版本数为1。</p>

<p>HBase的存取模式如下（表，行键，列族，列，时间戳）-&gt; 值。即一个表中的某一行键的某一列族的某一列的某一个版本的值唯一。</p>

<p>行数据的存取操作是原子的，可以读取任意数目的列。目前还不支持跨行事务和跨表事务。</p>

<p>同一列族下的数据压缩在一起，访问控制磁盘和内存都在列族层面进行。</p>



<h3 id="2自动分区">2）自动分区</h3>

<p>HBase中扩展和负载均衡的基本单元称作region，region本质上是以行键排序的连续存储空间。如果region过大，系统就会把它们动态拆分，相反的，就把多个region合并，以减少存储文件数量。</p>

<p>一个表最开始只有一个region，用户开始向表中插入数据时，系统会检查region大小，确保不会超过配置的最大值，如果超过，会从region中行键的中间值一分为二，将该region分为大小大致相等的两个region。</p>

<p>注意，每个region只能由一个region server加载，每一台region服务器可以同时加载多个region。下图展示了一个表，该表实际上是由很多region server加载的region集合组成的逻辑视图。</p>

<p><img src="https://img-blog.csdn.net/20140731140254121" alt="这里写图片描述" title=""></p>

<h3 id="3hbase存储格式">3）HBase存储格式</h3>

<p>HFile：HBase中KeyValue数据的存储格式。HFile是Hadoop的二进制格式文件。</p>

<p>HLog：HBase中WAL（Write-Ahead-Log，预写式日志）文件的存储格式，物理上是Hadoop的Sequence File。</p>

<p>HFile的格式如下图：</p>

<p><img src="https://img-blog.csdn.net/20140731145136723" alt="这里写图片描述" title=""></p>

<p>HFile文件的长度可变，唯一固定的是File Info和Trailer。Trailer存储指向其他块的指针，它在持久化数据到文件结束时写入的，写入后，该文件就会变成不可变的数据存储文件。数据块（data blocks）中存储key-values，可以看做是一个MapFile。当block关闭操作时，第一个key会被写入index中，index文件在hfile关闭操作时写入。 </p>

<p>KeyValue的具体格式如下图：</p>

<p><img src="https://img-blog.csdn.net/20140731145347373" alt="这里写图片描述" title=""></p>

<p>上图中，keytype有四种类型，分别是Put、Delete、 DeleteColumn和DeleteFamily。RowLength为2个字节，Row长度不固定，ColumnFamilyLength为2个字节，ColumnFamily长度不固定，ColumnQualifier长度不固定，TimeStamp为4个字节，KeyType为1个字节。之所以不记录ColumnQualifier的长度是因为可以通过其他字段计算得到。 </p>



<h3 id="4-wal预写式日志">4 ) WAL（预写式日志）</h3>

<p>region server会将数据保存到内存，直到积攒到足够多的数据再将其刷写到磁盘，这样可避免很多小文件。但此时如果发生断电或其他故障，存储在内存中的数据没来得及保存到磁盘，就会出现数据丢失情况。WAL能解决这个问题。每次更新（编辑）都会写入日志，只有日志写入成功后才会告知客户端写入成功，然后服务器按需批量处理内存中的数据。</p>

<p>如果服务器崩溃，region server会回访日志，使得服务器恢复到服务器崩溃前的状态。下图显示了写入过程：</p>

<p><img src="https://img-blog.csdn.net/20140731150335089" alt="这里写图片描述" title=""></p>

<ul>
<li>所有的修改都会先保存到WAL，然后再传给MemStore。整个过程是这样的：</li>
<li>客户端启动一个操作来修改数据，比如Put。每次修改都封装到一个KeyValue对象实例中，通过RPC调用发送出去。这些调用会发送给含有匹配region的Region Server；</li>
<li>KeyValue实例到达后，它们会被分配到管理对应行HRegion实例，数据被写入WAL，然后被放入实际拥有记录的MemStore中；</li>
<li>当MemStore达到一定大小或经历一个特定时间，数据会异步的连续的写入到文件系统中（HFile）。</li>
<li>如果写入过程出现问题，WAL能保证数据不丢失，因为WAL日志HLog存储在HDFS上。其他region server可以读取日志文件并回放修改，恢复数据。</li>
</ul>



<h3 id="5hbase系统架构">5）HBase系统架构</h3>

<p>HBase架构包括HBase Client、Zookeeper、HMaster、HRegionServer、HStore存储几个部分。下面一一叙述。一个大体的架构图如下：</p>

<p><img src="https://img-blog.csdn.net/20140731151718015" alt="这里写图片描述" title=""></p>

<p><strong>a）HBase Client</strong></p>

<p>HBase Client使用HBase的RPC机制与HMaster和HRegionServer进行通信。对于管理类操作（如建表，删表等），Client和HMaster进行RPC；对于数据读写类操作，Client和HRegionServer进行RPC。</p>

<p><strong>b）Zookeeper</strong></p>

<p>一个分布式的，开放源码的分布式应用程序协调服务，分布式应用程序可以基于它实现同步服务，配置维护和命名服务等。它是Chubby的开源实现。  <br>
Zookeeper Quorum中除了存储了-ROOT-表的地址和Master的地址，RegionServer也会把自己注册到Zookeeper中，使Master可以随时感知到各个RegionServer的健康状态。 </p>

<p><strong>c）HMaster</strong></p>

<ul>
<li>管理用户对Table的增、删、改、查操作；</li>
<li>管理HRegionServer的负载均衡，调整Region分布；</li>
<li>在Region Split后，负责新Region的分配；</li>
<li>在HRegionServer停机后，负责失效HRegionServer上的Regions迁移。</li>
</ul>

<p><strong>d）HRegionServer</strong></p>

<ul>
<li>主要负责响应用户I/O请求，向HDFS文件系统中读写数据，是HBase中最核心的模块；</li>
<li>当用户更新数据的时候会被分配到对应的HRegion服务器上提交修改，这些修改显示被写到MemStore写缓存和服务器的Hlog文件里面。在操作写入Hlog之后，commit()调用才会将其返回给客户端；</li>
<li>在读取数据的时候，HRegion服务器会先访问BlockCache读缓存，如果缓存里没有改数据，才会回到Hstores磁盘上面寻找，每一个列族都会有一个HStore集合，每一个HStore集合包含很多HstoreFile文件。</li>
</ul>

<p><strong>e）特殊的表</strong></p>

<p>-ROOT- 表和.META.表是两个比较特殊的表。.META.记录了用户表的Region信息，.META.可以有多个regoin。-ROOT-记录了.META.表的Region信息，-ROOT-只有一个region，Zookeeper中记录了-ROOT-表的location。具体如下： </p>

<p><img src="https://img-blog.csdn.net/20140731155028632" alt="这里写图片描述" title=""></p>



<h2 id="为何hbase速度很快">为何HBase速度很快？</h2>

<p>HBase能提供实时计算服务主要原因是由其架构和底层的数据结构决定的，即由LSM-Tree(Log-Structured Merge-Tree) + HTable(region分区) + Cache决定——客户端可以直接定位到要查数据所在的HRegion server服务器，然后直接在服务器的一个region上查找要匹配的数据，并且这些数据部分是经过cache缓存的。</p>

<p>前面说过HBase会将数据保存到内存中，在内存中的数据是有序的，如果内存空间满了，会刷写到HFile中，而在HFile中保存的内容也是有序的。当数据写入HFile后，内存中的数据会被丢弃。</p>

<p>HFile文件为磁盘顺序读取做了优化，按页存储。下图展示了在内存中多个块存储并归并到磁盘的过程，合并写入会产生新的结果块，最终多个块被合并为更大块。</p>

<p><img src="https://img-blog.csdn.net/20140731162806018" alt="这里写图片描述" title=""></p>

<p>多次刷写后会产生很多小文件，后台线程会合并小文件组成大文件，这样磁盘查找会限制在少数几个数据存储文件中。HBase的写入速度快是因为它其实并不是真的立即写入文件中，而是先写入内存，随后异步刷入HFile。所以在客户端看来，写入速度很快。另外，写入时候将随机写入转换成顺序写，数据写入速度也很稳定。</p>

<p>而读取速度快是因为它使用了LSM树型结构，而不是B或B+树。磁盘的顺序读取速度很快，但是相比而言，寻找磁道的速度就要慢很多。HBase的存储结构导致它需要磁盘寻道时间在可预测范围内，并且读取与所要查询的rowkey连续的任意数量的记录都不会引发额外的寻道开销。比如有5个存储文件，那么最多需要5次磁盘寻道就可以。而关系型数据库，即使有索引，也无法确定磁盘寻道次数。而且，HBase读取首先会在缓存（BlockCache）中查找，它采用了LRU（最近最少使用算法），如果缓存中没找到，会从内存中的MemStore中查找，只有这两个地方都找不到时，才会加载HFile中的内容，而上文也提到了读取HFile速度也会很快，因为节省了寻道开销。</p>



<h2 id="hbase常用操作">HBase常用操作：</h2>

<ul>
<li>List；</li>
<li>Create；</li>
<li>Put；</li>
<li>Scan；</li>
<li>Get；</li>
<li>Delete；</li>
<li>Disable；</li>
<li>Drop；</li>
</ul>            </div>
						<link href="https://csdnimg.cn/release/phoenix/mdeditor/markdown_views-9e5741c4b9.css" rel="stylesheet">
                </div>