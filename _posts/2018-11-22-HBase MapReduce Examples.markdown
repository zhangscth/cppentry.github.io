---
layout:     post
title:      HBase MapReduce Examples
---
<div id="article_content" class="article_content clearfix csdn-tracking-statistics" data-pid="blog" data-mod="popu_307" data-dsm="post">
								            <link rel="stylesheet" href="https://csdnimg.cn/release/phoenix/template/css/ck_htmledit_views-f76675cdea.css">
						<div class="htmledit_views" id="content_views">
                
<div class="titlepage" style="font-family:Simsun;font-size:14px;line-height:19px;">
<div>
<div>
<h2 class="title" style="color:rgb(153,0,0);line-height:1.3;clear:both;">
7.2. HBase MapReduce Examples</h2>
</div>
</div>
</div>
<div class="section" title="7.2.1. HBase MapReduce Read Example" style="font-family:Simsun;font-size:14px;line-height:19px;">
<div class="titlepage">
<div>
<div>
<h3 class="title" style="color:rgb(153,0,0);line-height:1.3;">
<a name="mapreduce.example.read"></a>7.2.1. HBase MapReduce Read Example</h3>
</div>
</div>
</div>
<p>The following is an example of using HBase as a MapReduce source in read-only manner. Specifically, there is a Mapper instance but no Reducer, and nothing is being emitted from the Mapper. There job would be defined as follows...</p>
<pre class="programlisting" style="line-height:1;background-color:rgb(238,238,238);border:1px solid rgb(204,204,204);">Configuration config = HBaseConfiguration.create();
Job job = new Job(config, "ExampleRead");
job.setJarByClass(MyReadJob.class);     // class that contains mapper

Scan scan = new Scan();
scan.setCaching(500);        // 1 is the default in Scan, which will be bad for MapReduce jobs
scan.setCacheBlocks(false);  // don't set to true for MR jobs
// set other scan attrs
...

TableMapReduceUtil.initTableMapperJob(
  tableName,        // input HBase table name
  scan,             // Scan instance to control CF and attribute selection
  MyMapper.class,   // mapper
  null,             // mapper output key
  null,             // mapper output value
  job);
job.setOutputFormatClass(NullOutputFormat.class);   // because we aren't emitting anything from mapper

boolean b = job.waitForCompletion(true);
if (!b) {
  throw new IOException("error with job!");
}
  </pre>
<p>...and the mapper instance would extend <a class="link" href="http://hbase.apache.org/apidocs/org/apache/hadoop/hbase/mapreduce/TableMapper.html" rel="nofollow">TableMapper</a>...</p>
<pre class="programlisting" style="line-height:1;background-color:rgb(238,238,238);border:1px solid rgb(204,204,204);">public static class MyMapper extends TableMapper&lt;Text, Text&gt; {

  public void map(ImmutableBytesWritable row, Result value, Context context) throws InterruptedException, IOException {
    // process data for the row from the Result instance.
   }
}
    </pre>
<p></p>
</div>
<div class="section" title="7.2.2. HBase MapReduce Read/Write Example" style="font-family:Simsun;font-size:14px;line-height:19px;">
<div class="titlepage">
<div>
<div>
<h3 class="title" style="color:rgb(153,0,0);line-height:1.3;">
<a name="mapreduce.example.readwrite"></a>7.2.2. HBase MapReduce Read/Write Example</h3>
</div>
</div>
</div>
<p>The following is an example of using HBase both as a source and as a sink with MapReduce. This example will simply copy data from one table to another.</p>
<pre class="programlisting" style="line-height:1;background-color:rgb(238,238,238);border:1px solid rgb(204,204,204);">Configuration config = HBaseConfiguration.create();
Job job = new Job(config,"ExampleReadWrite");
job.setJarByClass(MyReadWriteJob.class);    // class that contains mapper

Scan scan = new Scan();
scan.setCaching(500);        // 1 is the default in Scan, which will be bad for MapReduce jobs
scan.setCacheBlocks(false);  // don't set to true for MR jobs
// set other scan attrs

TableMapReduceUtil.initTableMapperJob(
	sourceTable,      // input table
	scan,	          // Scan instance to control CF and attribute selection
	MyMapper.class,   // mapper class
	null,	          // mapper output key
	null,	          // mapper output value
	job);
TableMapReduceUtil.initTableReducerJob(
	targetTable,      // output table
	null,             // reducer class
	job);
job.setNumReduceTasks(0);

boolean b = job.waitForCompletion(true);
if (!b) {
    throw new IOException("error with job!");
}
    </pre>
<p>An explanation is required of what <code class="classname">TableMapReduceUtil</code> is doing, especially with the reducer. <a class="link" href="http://hbase.apache.org/apidocs/org/apache/hadoop/hbase/mapreduce/TableOutputFormat.html" rel="nofollow">TableOutputFormat</a> is
 being used as the outputFormat class, and several parameters are being set on the config (e.g., TableOutputFormat.OUTPUT_TABLE), as well as setting the reducer output key to <code class="classname">ImmutableBytesWritable</code> and reducer value to <code class="classname">Writable</code>.
 These could be set by the programmer on the job and conf, but<code class="classname">TableMapReduceUtil</code> tries to make things easier.</p>
<p>The following is the example mapper, which will create a <code class="classname">Put</code> and matching the input <code class="classname">Result</code> and emit it. Note: this is what the CopyTable utility does.</p>
<p></p>
<pre class="programlisting" style="line-height:1;background-color:rgb(238,238,238);border:1px solid rgb(204,204,204);">public static class MyMapper extends TableMapper&lt;ImmutableBytesWritable, Put&gt;  {

	public void map(ImmutableBytesWritable row, Result value, Context context) throws IOException, InterruptedException {
		// this example is just copying the data from the source table...
   		context.write(row, resultToPut(row,value));
   	}

  	private static Put resultToPut(ImmutableBytesWritable key, Result result) throws IOException {
  		Put put = new Put(key.get());
 		for (KeyValue kv : result.raw()) {
			put.add(kv);
		}
		return put;
   	}
}
    </pre>
<p></p>
<p>There isn't actually a reducer step, so <code class="classname">TableOutputFormat</code> takes care of sending the <code class="classname">Put</code> to the target table.</p>
<p></p>
<p>This is just an example, developers could choose not to use <code class="classname">TableOutputFormat</code> and connect to the target table themselves.</p>
<p></p>
</div>
<div class="section" title="7.2.3. HBase MapReduce Read/Write Example With Multi-Table Output" style="font-family:Simsun;font-size:14px;line-height:19px;">
<div class="titlepage">
<div>
<div>
<h3 class="title" style="color:rgb(153,0,0);line-height:1.3;">
<a name="mapreduce.example.readwrite.multi"></a>7.2.3. HBase MapReduce Read/Write Example With Multi-Table Output</h3>
</div>
</div>
</div>
<p>TODO: example for <code class="classname">MultiTableOutputFormat</code>.</p>
</div>
<div class="section" title="7.2.4. HBase MapReduce Summary to HBase Example" style="font-family:Simsun;font-size:14px;line-height:19px;">
<div class="titlepage">
<div>
<div>
<h3 class="title" style="color:rgb(153,0,0);line-height:1.3;">
<a name="mapreduce.example.summary"></a>7.2.4. HBase MapReduce Summary to HBase Example</h3>
</div>
</div>
</div>
<p>The following example uses HBase as a MapReduce source and sink with a summarization step. This example will count the number of distinct instances of a value in a table and write those summarized counts in another table.</p>
<pre class="programlisting" style="line-height:1;background-color:rgb(238,238,238);border:1px solid rgb(204,204,204);">Configuration config = HBaseConfiguration.create();
Job job = new Job(config,"ExampleSummary");
job.setJarByClass(MySummaryJob.class);     // class that contains mapper and reducer

Scan scan = new Scan();
scan.setCaching(500);        // 1 is the default in Scan, which will be bad for MapReduce jobs
scan.setCacheBlocks(false);  // don't set to true for MR jobs
// set other scan attrs

TableMapReduceUtil.initTableMapperJob(
	sourceTable,        // input table
	scan,               // Scan instance to control CF and attribute selection
	MyMapper.class,     // mapper class
	Text.class,         // mapper output key
	IntWritable.class,  // mapper output value
	job);
TableMapReduceUtil.initTableReducerJob(
	targetTable,        // output table
	MyTableReducer.class,    // reducer class
	job);
job.setNumReduceTasks(1);   // at least one, adjust as required

boolean b = job.waitForCompletion(true);
if (!b) {
	throw new IOException("error with job!");
}
    </pre>
<p>In this example mapper a column with a String-value is chosen as the value to summarize upon. This value is used as the key to emit from the mapper, and an <code class="classname">IntWritable</code> represents an instance counter.</p>
<pre class="programlisting" style="line-height:1;background-color:rgb(238,238,238);border:1px solid rgb(204,204,204);">public static class MyMapper extends TableMapper&lt;Text, IntWritable&gt;  {
	public static final byte[] CF = "cf".getBytes();
	public static final byte[] ATTR1 = "attr1".getBytes();

	private final IntWritable ONE = new IntWritable(1);
   	private Text text = new Text();

   	public void map(ImmutableBytesWritable row, Result value, Context context) throws IOException, InterruptedException {
        	String val = new String(value.getValue(CF, ATTR1));
          	text.set(val);     // we can only emit Writables...

        	context.write(text, ONE);
   	}
}
    </pre>
<p>In the reducer, the "ones" are counted (just like any other MR example that does this), and then emits a <code class="classname">Put</code>.</p>
<pre class="programlisting" style="line-height:1;background-color:rgb(238,238,238);border:1px solid rgb(204,204,204);">public static class MyTableReducer extends TableReducer&lt;Text, IntWritable, ImmutableBytesWritable&gt;  {
	public static final byte[] CF = "cf".getBytes();
	public static final byte[] COUNT = "count".getBytes();

 	public void reduce(Text key, Iterable&lt;IntWritable&gt; values, Context context) throws IOException, InterruptedException {
    		int i = 0;
    		for (IntWritable val : values) {
    			i += val.get();
    		}
    		Put put = new Put(Bytes.toBytes(key.toString()));
    		put.add(CF, COUNT, Bytes.toBytes(i));

    		context.write(null, put);
   	}
}
    </pre>
<p></p>
</div>
<div class="section" title="7.2.5. HBase MapReduce Summary to File Example" style="font-family:Simsun;font-size:14px;line-height:19px;">
<div class="titlepage">
<div>
<div>
<h3 class="title" style="color:rgb(153,0,0);line-height:1.3;">
<a name="mapreduce.example.summary.file"></a>7.2.5. HBase MapReduce Summary to File Example</h3>
</div>
</div>
</div>
<p>This very similar to the summary example above, with exception that this is using HBase as a MapReduce source but HDFS as the sink. The differences are in the job setup and in the reducer. The mapper remains the same.</p>
<pre class="programlisting" style="line-height:1;background-color:rgb(238,238,238);border:1px solid rgb(204,204,204);">Configuration config = HBaseConfiguration.create();
Job job = new Job(config,"ExampleSummaryToFile");
job.setJarByClass(MySummaryFileJob.class);     // class that contains mapper and reducer

Scan scan = new Scan();
scan.setCaching(500);        // 1 is the default in Scan, which will be bad for MapReduce jobs
scan.setCacheBlocks(false);  // don't set to true for MR jobs
// set other scan attrs

TableMapReduceUtil.initTableMapperJob(
	sourceTable,        // input table
	scan,               // Scan instance to control CF and attribute selection
	MyMapper.class,     // mapper class
	Text.class,         // mapper output key
	IntWritable.class,  // mapper output value
	job);
job.setReducerClass(MyReducer.class);    // reducer class
job.setNumReduceTasks(1);    // at least one, adjust as required
FileOutputFormat.setOutputPath(job, new Path("/tmp/mr/mySummaryFile"));  // adjust directories as required

boolean b = job.waitForCompletion(true);
if (!b) {
	throw new IOException("error with job!");
}
    </pre>
As stated above, the previous Mapper can run unchanged with this example. As for the Reducer, it is a "generic" Reducer instead of extending TableMapper and emitting Puts.
<pre class="programlisting" style="line-height:1;background-color:rgb(238,238,238);border:1px solid rgb(204,204,204);"> public static class MyReducer extends Reducer&lt;Text, IntWritable, Text, IntWritable&gt;  {

	public void reduce(Text key, Iterable&lt;IntWritable&gt; values, Context context) throws IOException, InterruptedException {
		int i = 0;
		for (IntWritable val : values) {
			i += val.get();
		}
		context.write(key, new IntWritable(i));
	}
}
    </pre>
</div>
<div class="section" title="7.2.6. HBase MapReduce Summary to HBase Without Reducer" style="font-family:Simsun;font-size:14px;line-height:19px;">
<div class="titlepage">
<div>
<div>
<h3 class="title" style="color:rgb(153,0,0);line-height:1.3;">
<a name="mapreduce.example.summary.noreducer"></a>7.2.6. HBase MapReduce Summary to HBase Without Reducer</h3>
</div>
</div>
</div>
<p>It is also possible to perform summaries without a reducer - if you use HBase as the reducer.</p>
<p>An HBase target table would need to exist for the job summary. The HTable method <code class="code">incrementColumnValue</code> would be used to atomically increment values. From a performance perspective, it might make sense to keep a Map of values with
 their values to be incremeneted for each map-task, and make one update per key at during the <code class="code">cleanup</code> method of the mapper. However, your milage may vary depending on the number of rows to be processed and unique keys.</p>
<p>In the end, the summary results are in HBase.</p>
</div>
<div class="section" title="7.2.7. HBase MapReduce Summary to RDBMS" style="font-family:Simsun;font-size:14px;line-height:19px;">
<div class="titlepage">
<div>
<div>
<h3 class="title" style="color:rgb(153,0,0);line-height:1.3;">
<a name="mapreduce.example.summary.rdbms"></a>7.2.7. HBase MapReduce Summary to RDBMS</h3>
</div>
</div>
</div>
<p>Sometimes it is more appropriate to generate summaries to an RDBMS. For these cases, it is possible to generate summaries directly to an RDBMS via a custom reducer. The <code class="code">setup</code> method can connect to an RDBMS (the connection information
 can be passed via custom parameters in the context) and the cleanup method can close the connection.</p>
<p>It is critical to understand that number of reducers for the job affects the summarization implementation, and you'll have to design this into your reducer. Specifically, whether it is designed to run as a singleton (one reducer) or multiple reducers. Neither
 is right or wrong, it depends on your use-case. Recognize that the more reducers that are assigned to the job, the more simultaneous connections to the RDBMS will be created - this will scale, but only to a point.</p>
<pre class="programlisting" style="line-height:1;background-color:rgb(238,238,238);border:1px solid rgb(204,204,204);"> public static class MyRdbmsReducer extends Reducer&lt;Text, IntWritable, Text, IntWritable&gt;  {

	private Connection c = null;

	public void setup(Context context) {
  		// create DB connection...
  	}

	public void reduce(Text key, Iterable&lt;IntWritable&gt; values, Context context) throws IOException, InterruptedException {
		// do summarization
		// in this example the keys are Text, but this is just an example
	}

	public void cleanup(Context context) {
  		// close db connection
  	}

}
    </pre>
<p>In the end, the summary results are written to your RDBMS table/s.</p>
<p><br></p>
<p><br></p>
<p><a href="http://hbase.apache.org/book/mapreduce.example.html#mapreduce.example.readwrite" rel="nofollow">http://hbase.apache.org/book/mapreduce.example.html#mapreduce.example.readwrite</a><br></p>
</div>
            </div>
                </div>