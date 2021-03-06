---
layout:     post
title:      通过案例对SparkStreaming透彻理解（1）
---
<div id="article_content" class="article_content clearfix csdn-tracking-statistics" data-pid="blog" data-mod="popu_307" data-dsm="post">
								<div class="article-copyright">
					版权声明：本文为博主原创文章，未经博主允许不得转载。					https://blog.csdn.net/erfucun/article/details/52291761				</div>
								            <div id="content_views" class="markdown_views prism-atom-one-dark">
							<!-- flowchart 箭头图标 勿删 -->
							<svg xmlns="http://www.w3.org/2000/svg" style="display: none;"><path stroke-linecap="round" d="M5,0 0,2.5 5,5z" id="raphael-marker-block" style="-webkit-tap-highlight-color: rgba(0, 0, 0, 0);"></path></svg>
							<p>本博文主要包含内容为：</p>

<p>1、spark streaming另类在线实验 <br>
2、瞬间理解spark streaming本质</p>

<p>一，对SparkStreaming的深入理解：</p>

<p>1、 首先为何从Spark Streaming切入Spark定制？Spark的子框架已有若干，为何选择Spark Streaming？</p>

<ul>
<li><p>Spark最开始只有Spark Core，没有目前的这些子框架。这些子框架是构建于Spark Core之上的。没有哪个子框架能摆脱Spark Core。我们通过对一个框架的彻底研究，肯定可以领会Spark力量的源泉，并精通所有问题的解决之道。</p></li>
<li><p>Spark SQL涉及了很多SQL语法细节的解析和优化，当然分析其解析、优化从而集中精力去研究Spark而言是一件重要的事情，但不是最重要的事情，所以Spark SQL不太适合作为具体的子框架值得我们去研究。</p></li>
<li><p>目前Spark R现在不成熟，支撑功能有限。</p></li>
<li><p>图计算，从各版本演进而言Graphx几乎没有改进，这种趋势，Graphx是不是已经发展基本到尽头了；另外图计算而言有很多数学级别的算法，而要把Spark做到极致，数学对我们来说重要，但对于研究而言不是最重要的。</p></li>
<li><p>Mechine Learning在封装了Vector向量、Metrics构建了众多的算法库，从而涉及了太多的数学知识，所有选择ML其实也不是太好的选择。</p></li>
<li><p>最后筛选出SparkStreaming子框架才是最佳的研究切入黄金点。</p></li>
</ul>

<p>2、对SparkStreaming的理解?</p>

<ul>
<li>Spark Streaming是流式计算，当今时代是一个流处理时代，一切数据如果不是流式处理， 或者说和流式处理不相关的话，都是无效的数据。 <br>
-流式处理才是我们对大数据的初步印象，而不是批处理和数据挖掘，当然Spark强悍的地方在于，他的流式处理可以在线的直接使用机器学习、图计算、SparkSQL、Spark R的成果。</li>
<li>整个Spark的程序，基于Spark Streaming的最容易出问题，也是最受关注的地方，也是最需要人才的地方。</li>
<li>Spark Streaming和其他子框架的不同之处，Spark Streaming很像基于Spark Core之上的应用程序。</li>
<li>　正如世界万物发展一样，任何技术都有其关键点或转折点，SparkStreaming相当于独孤九剑，SparkCore 相当于易筋经。SparkStreaming运行在SparkCore上，所以很多性能调优都是建立在SparkCore上的；Spark是大数据的龙脉，SparkStreaming是龙脉的穴位。寻龙点穴，Spark就是龙脉，Spark Streaming就是穴位</li>
</ul>

<p>3、当今现状</p>

<p>2015年是流式处理的一年。大家考虑用Spark，主要也是因为Spark Streaming。这是一个流处理的时代，一切数据如果与流式处理不相关的话，都是无效的数据。Spark之所以强悍的一个重要原因在于，它的流式处理可以在线使用图计算、机器学习或者SparkR的成果，<strong>这得益于Spark一体化、多元化的基础架构设计。也就是在Spark Streaming中可以调用其它子框架，无需任何设置。</strong>这是Spark的无可匹敌之处，也是Spark Streaming必将一统天下的根源。但Spark的应用中，Spark Streaming也是最容易出问题的。</p>

<p>Spark Streaming与其它子框架不同之处在于，它更像是Spark Core之上的一个应用程序。所以如果要做Spark的定制开发，Spark Streaming则提供了最好的参考。你想掌握Spark Streaming，但你不去精通Spark Core的话，那是不可能的。所以我们选择Spark Streaming来提升自己，是找到了关键点。</p>

<p>二：通过案例来深入理解SparkStreaming工作原理</p>

<p>1、研究SparkStreaming时，有困惑你的东西，SparkStreaming数据不断流进来，根据batchInterval时间片不断生成Job，并将Job提交集群处理，如果能清晰的看到数据的流入和数据的处理，你心里会很很踏实。</p>

<p>如何能清晰的看到数据的处理过程呢？只需要一个小技巧：就是把SparkStreaming中的batchInterval放的足够大，例如说从30秒调整为1分钟一次batch，或者5分钟一次batch，你会很清晰的看到整个流程序的运行过程。在这里利用上篇博文的代码</p>



<pre class="prettyprint"><code class=" hljs scala"><span class="hljs-javadoc">/**
* Created by hadoop on 2016/4/18.
* 背景描述 在广告点击计费系统中 我们在线过滤掉 黑名单的点击 进而保护广告商的利益
* 只有效的广告点击计费
* 
*/</span>
<span class="hljs-class"><span class="hljs-keyword">object</span> <span class="hljs-title">OnlineBlackListFilter</span> {</span>  
    <span class="hljs-keyword">def</span> main(args: Array[String]){  
      <span class="hljs-javadoc">/**  
       * 第1步：创建Spark的配置对象SparkConf，设置Spark程序的运行时的配置信息，  
       * 例如说通过setMaster来设置程序要链接的Spark集群的Master的URL，如果设置  
       * 为local，则代表Spark程序在本地运行，特别适合于机器配置条件非常差（例如  
       * 只有1G的内存）的初学者。  
       */</span>  
      <span class="hljs-comment">// 创建SparkConf对象  </span>
      <span class="hljs-keyword">val</span> conf = <span class="hljs-keyword">new</span> SparkConf()  
      <span class="hljs-comment">// 设置应用程序的名称，在程序运行的监控界面可以看到名称  </span>
      conf.setAppName(<span class="hljs-string">"OnlineBlackListFilter"</span>)  
      <span class="hljs-comment">// 此时，程序在Spark集群  </span>
      conf.setMaster(<span class="hljs-string">"spark://Master:7077"</span>)  

      <span class="hljs-keyword">val</span> ssc = <span class="hljs-keyword">new</span> StreamingContext(conf, Seconds(<span class="hljs-number">30</span>))  

      <span class="hljs-javadoc">/**  
       * 黑名单数据准备，实际上黑名单一般都是动态的，例如在Redis或者数据库中，  
       * 黑名单的生成往往有复杂的业务逻辑，具体情况算法不同，  
       * 但是在Spark Streaming进行处理的时候每次都能够访问完整的信息。  
       */</span>  
      <span class="hljs-keyword">val</span> blackList = Array((<span class="hljs-string">"Spy"</span>, <span class="hljs-keyword">true</span>),(<span class="hljs-string">"Cheater"</span>, <span class="hljs-keyword">true</span>))  
      <span class="hljs-keyword">val</span> blackListRDD = ssc.sparkContext.parallelize(blackList, <span class="hljs-number">8</span>)  

      <span class="hljs-keyword">val</span> adsClickStream = ssc.socketTextStream(<span class="hljs-string">"Master"</span>, <span class="hljs-number">9999</span>)  

      <span class="hljs-javadoc">/**  
       * 此处模拟的广告点击的每条数据的格式为：time、name  
       * 此处map操作的结果是name、（time，name）的格式  
       */</span>  
      <span class="hljs-keyword">val</span> adsClickStreamFormatted = adsClickStream.map { ads =&gt; (ads.split(<span class="hljs-string">" "</span>)(<span class="hljs-number">1</span>), ads) }  
      adsClickStreamFormatted.transform(userClickRDD =&gt; {  
        <span class="hljs-comment">// 通过leftOuterJoin操作既保留了左侧用户广告点击内容的RDD的所有内容，  </span>
        <span class="hljs-comment">// 又获得了相应点击内容是否在黑名单中  </span>
        <span class="hljs-keyword">val</span> joinedBlackListRDD = userClickRDD.leftOuterJoin(blackListRDD)  

        <span class="hljs-javadoc">/**  
         * 进行filter过滤的时候，其输入元素是一个Tuple：（name,((time,name), boolean)）  
         * 其中第一个元素是黑名单的名称，第二元素的第二个元素是进行leftOuterJoin的时候是否存在的值。  
         * 如果存在的话，表面当前广告点击是黑名单，需要过滤掉，否则的话是有效点击内容；  
         */</span>  
        <span class="hljs-keyword">val</span> validClicked = joinedBlackListRDD.filter(joinedItem =&gt; {  
          <span class="hljs-keyword">if</span>(joinedItem._2._2.getOrElse(<span class="hljs-keyword">false</span>))  
          {  
            <span class="hljs-keyword">false</span>  
          } <span class="hljs-keyword">else</span> {  
            <span class="hljs-keyword">true</span>  
          }  

        })  

        validClicked.map(validClick =&gt; {validClick._2._1})  
      }).print  

      <span class="hljs-javadoc">/**  
       * 计算后的有效数据一般都会写入Kafka中，下游的计费系统会从kafka中pull到有效数据进行计费  
       */</span>  
      ssc.start()  
      ssc.awaitTermination()
    }  
} </code></pre>

<p>2、 把程序的Batch Interval设置成300秒: <br>
<img src="https://img-blog.csdn.net/20160823145423955" alt="这里写图片描述" title=""></p>

<p>3、  重新生成一下jar包 。</p>

<p>4、启动Hadoop的HDFS、  启动Spark集群，启动spark的History Server，并且通过web界面是否启动成功，打开数据发送的端口 ： nc -lk 9999</p>

<p>5、利用脚本， 用spark-submit运行前面生成的jar包 。</p>

<p>6、  在数据发送端口输入若干数据，形式比如： <br>
333333 Hadoop <br>
222222 spark <br>
111111 hadoop <br>
555555 Kafka <br>
6666666 Demo <br>
999999 SparkSQL</p>

<p>7、出现如下结果说明运行成功： <br>
<img src="https://img-blog.csdn.net/20160823151552547" alt="这里写图片描述" title=""></p>

<p>8、打开浏览器，看History Server里面的最新的日志信息，看我们目前运行的应用程序中有些什么Job：</p>

<p><img src="https://img-blog.csdn.net/20160823153534416" alt="这里写图片描述" title=""></p>

<p>总共竟然有5个Job。这完全不是我们此前做Spark SQL之类的应用程序时看到的样子。</p>

<p>我们接下来看一看这些Job的内容，主要揭示一些现象，不会做完全深入的剖析，只是为了先让大家进行一些思考。</p>

<ul>
<li>Job 0：此Job不体现我们的业务逻辑代码。这个Job是出于对后面计算的负载均衡的考虑。</li>
</ul>

<p><img src="https://img-blog.csdn.net/20160823154132519" alt="这里写图片描述" title=""></p>

<p>发现此Stage在所有Executor上都存在。　</p>

<ul>
<li>Job 1：运行时间比较长，耗时5.2分钟。 <br>
点击Stage 2的链接，进去看看Aggregated Metrics By Executor部分：</li>
</ul>

<p><img src="https://img-blog.csdn.net/20160823154054190" alt="这里写图片描述" title=""></p>

<p><img src="https://img-blog.csdn.net/20160823154211404" alt="这里写图片描述" title=""> <br>
　 <br>
　可以知道，Stage 2只在Worker1上的一个Executor执行，而且执行了5.2分钟。 <br>
    是否会觉得奇怪：从业务处理的角度看，我们发送的那么一点数据，没有必要去启动一个运行5.2分钟的任务吧。那这个任务是做什么呢？ <br>
    从DAG Visualization部分，就知道此Job实际就是启动了一个接收数据的Receiver：</p>

<p>**原来Receiver是通过一个Job来启动的。那肯定有一个Action来触发它。 <br>
只有一个Worker运行此Job。是用于接收数据。**</p>

<p>　　　Locality Level是PROCESS_LOCAL，原来是内存节点。所以，默认情况下，只要数据不是特别大，数据接收不会使用磁盘，而是直接使用内存中的数据。 <br>
      看来，Spark Streaming应用程序启动后，自己会启动一些Job。默认启动了一个Job来接收数据，为后续处理做准备。</p>

<p>　　　<strong>重要启示：一个Spark应用程序中可以启动很多Job，而这些不同的Job之间可以相互配合。这一认识为我们写复杂Spark程序奠定了良好的基础。</strong></p>

<ul>
<li>Job 2：看Details可以发现有我们程序的主要业务逻辑，体现在Stag 3、Stag4、Stag 5中。</li>
</ul>

<p><img src="https://img-blog.csdn.net/20160823154426405" alt="这里写图片描述" title=""></p>

<p><img src="https://img-blog.csdn.net/20160823154451554" alt="这里写图片描述" title=""></p>

<p>我们看Stag3、Stage4的详情，可以知道这2个Stage都是用2个Executor执行的。所有数据处理是在2台机器上进行的。</p>

<p><img src="https://img-blog.csdn.net/20160823154510390" alt="这里写图片描述" title=""></p>

<p>Stag 5只在Worker1上。这是因为这个Stage有Shuffle操作。</p>

<p><img src="https://img-blog.csdn.net/20160823154607374" alt="这里写图片描述" title=""></p>

<ul>
<li>Job3：有Stage 6、Stage 7、Stage 8。其中Stage 6、Stage 7被跳过。</li>
</ul>

<p><img src="https://img-blog.csdn.net/20160823154648213" alt="这里写图片描述" title=""></p>

<p>看看Stage 8的Aggregated Metrics by Executor部分。可以看到，数据处理是在2台机器上进行的：</p>

<p><img src="https://img-blog.csdn.net/20160823154712594" alt="这里写图片描述" title=""></p>

<ul>
<li>Job4：也体现了我们应用程序中的业务逻辑 。有Stage 9、Stage 10、Stage 11。其中Stage 9、Stage 10被跳过。</li>
</ul>

<p><img src="https://img-blog.csdn.net/20160823154732261" alt="这里写图片描述" title=""></p>

<p>看看Stage 11的详情。可以看到，数据处理是在2台机器上进行的</p>

<p><img src="https://img-blog.csdn.net/20160823154756313" alt="这里写图片描述" title=""></p>

<p>综合以上的现象可以知道，Spark Streaming的一个应用中，运行了这么多Job，远不是我们从网络博客或者书籍上看的那么简单。</p>

<p>　我们有必要通过这些现象，反过来回溯去寻根问源。不过这次暂不做深入分析。</p>

<p>我们的神奇之旅才刚刚开始。</p>

<p>三、SparkStreaming本质的深入理解</p>

<p><img src="https://img-blog.csdn.net/20160823155121423" alt="这里写图片描述" title=""> <br>
- Spark Streaming接收Kafka、Flume、HDFS和Kinesis等各种来源的实时输入数据，进行处理后，处理结果保存在HDFS、Databases等各种地方。 <br>
<img src="https://img-blog.csdn.net/20160823155134470" alt="这里写图片描述" title=""> <br>
- Spark Streaming接收这些实时输入数据流，会将它们按批次划分，然后交给Spark引擎处理，生成按照批次划分的结果流。 <br>
<img src="https://img-blog.csdn.net/20160823155144970" alt="这里写图片描述" title=""> <br>
- Spark Streaming提供了表示连续数据流的、高度抽象的被称为离散流的DStream。DStream本质上表示RDD的序列。任何对DStream的操作都会转变为对底层RDD的操作。 <br>
<img src="https://img-blog.csdn.net/20160823155153299" alt="这里写图片描述" title=""> <br>
- Spark Streaming使用数据源产生的数据流创建DStream，也可以在已有的DStream上使用一些操作来创建新的DStream。</p>

<p>　　在我们前面的实验中，每300秒会产生一批数据，基于这批数据会生成RDD，进而触发Job，执行处理。</p>

<p>　　DStream是一个没有边界的集合，没有大小的限制。</p>

<p>　　DStream代表了时空的概念。随着时间的推移，里面不断产生RDD。</p>

<p>　　锁定到时间段后，就是空间的操作。也就是对本时间段的对应批次的数据的处理。</p>

<p>　　下面用实例来讲解数据处理过程。</p>

<p>　　数据处理会有若干个对DStream的操作，这些操作之间的依赖关系，构成了DStreamGraph。如以下图例所示：　　　 <br>
<img src="https://img-blog.csdn.net/20160823155742134" alt="这里写图片描述" title=""></p>

<p>　　上图中每个foreach都会触发一个作业，就会顺着依赖从后往前回溯，形成DAG，如下图所示： <br>
　　<img src="https://img-blog.csdn.net/20160823155802285" alt="这里写图片描述" title=""> <br>
空间维度确定之后，随着时间不断推进，会不断实例化RDD Graph，然后触发Job去执行处理。</p>

<p>四、接下来我们要做的就是重新阅读官网的SparkStreaming</p>

<p>博文内容源自DT大数据梦工厂Spark课程总结的笔记。相关课程内容视频可以参考：  <br>
百度网盘链接：<a href="http://pan.baidu.com/s/1slvODe1" rel="nofollow">http://pan.baidu.com/s/1slvODe1</a>（如果链接失效或需要后续的更多资源，请联系QQ460507491或者微信号：DT1219477246 获取上述资料）。</p>            </div>
						<link href="https://csdnimg.cn/release/phoenix/mdeditor/markdown_views-9e5741c4b9.css" rel="stylesheet">
                </div>