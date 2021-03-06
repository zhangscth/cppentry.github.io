---
layout:     post
title:      hadoop  hdfs dfs 命令讲解
---
<div id="article_content" class="article_content clearfix csdn-tracking-statistics" data-pid="blog" data-mod="popu_307" data-dsm="post">
								            <link rel="stylesheet" href="https://csdnimg.cn/release/phoenix/template/css/ck_htmledit_views-f76675cdea.css">
						<div class="htmledit_views" id="content_views">
                
<h1><span style="color:#ff0000;">hdfs dfs命令</span></h1>
<h2><span style="color:#ff0000;">appendToFile</span></h2>
<p>Usage: hdfs dfs -appendToFile &lt;localsrc&gt; ... &lt;dst&gt;</p>
<p>追加一个或者多个文件到hdfs<span style="font-family:'宋体';">制定文件中</span>.也可以从命令行读取输入.</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -appendToFile localfile /user/hadoop/hadoopfile</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -appendToFile localfile1 localfile2 /user/hadoop/hadoopfile</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -appendToFile localfile hdfs://nn.example.com/hadoop/hadoopfile</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -appendToFile - hdfs://nn.example.com/hadoop/hadoopfile</span><span style="color:rgb(51,51,51);"> Reads the input from stdin.</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and 1 on error.</p>
<h2><span style="color:#ff0000;">cat</span></h2>
<p>Usage: hdfs dfs -cat URI [URI ...]</p>
<p>查看内容.</p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -cat hdfs://nn1.example.com/file1 hdfs://nn2.example.com/file2</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -cat file:///file3 /user/hadoop/file4</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">Chgrp【change group】</span></h2>
<p>Usage: hdfs dfs -chgrp [-R] GROUP URI [URI ...]</p>
<p>修改所属组.</p>
<p>Options</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -R option will make the change recursively through the directory structure.</span></p>
<h2><span style="color:#ff0000;">chmod</span></h2>
<p>Usage: hdfs dfs -chmod [-R] &lt;MODE[,MODE]... | OCTALMODE&gt; URI [URI ...]</p>
<p>修改权限.</p>
<p>Options</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -R option will make the change recursively through the directory structure.</span></p>
<h2><span style="color:#ff0000;">chown</span></h2>
<p>Usage: hdfs dfs -chown [-R] [OWNER][:[GROUP]] URI [URI ]</p>
<p>修改所有者.</p>
<p>Options</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -R option will make the change recursively through the directory structure.</span></p>
<h2><span style="color:#ff0000;">copyFromLocal</span></h2>
<p>Usage: hdfs dfs -copyFromLocal &lt;localsrc&gt; URI</p>
<p>Similar to put command, except that the source is restricted to a local file reference.</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -f option will overwrite the destination if it already exists.</span></p>
<h2><span style="color:#ff0000;">copyToLocal</span></h2>
<p>Usage: hdfs dfs -copyToLocal [-ignorecrc] [-crc] URI &lt;localdst&gt;</p>
<p>Similar to get command, except that the destination is restricted to a local file reference.</p>
<h2><span style="color:#ff0000;">count</span></h2>
<p>Usage: hdfs dfs -count [-q] [-h] &lt;paths&gt;</p>
<p>列出文件夹数量、文件数量、内容大小. The output columns with -count are: DIR_COUNT, FILE_COUNT, CONTENT_SIZE FILE_NAME</p>
<p>The output columns with -count -q are: QUOTA, REMAINING_QUATA, SPACE_QUOTA, REMAINING_SPACE_QUOTA, DIR_COUNT, FILE_COUNT, CONTENT_SIZE, FILE_NAME</p>
<p>The -h option shows sizes in human readable format.</p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -count hdfs://nn1.example.com/file1 hdfs://nn2.example.com/file2</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -count -q hdfs://nn1.example.com/file1</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -count -q -h hdfs://nn1.example.com/file1</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">cp</span></h2>
<p>Usage: hdfs dfs -cp [-f] [-p | -p[topax]] URI [URI ...] &lt;dest&gt;</p>
<p>复制文件(夹)<span style="font-family:'宋体';">，可以覆盖，可以保留原有权限信息</span></p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -f option will overwrite the destination if it already exists.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -p option will preserve file attributes [topx] (timestamps, ownership, permission, ACL, XAttr). If -p is specified with no </span><span style="color:rgb(51,51,51);">arg</span><span style="color:rgb(51,51,51);">, then preserves timestamps, ownership, permission. If -pa is specified, then preserves permission also because ACL is a super-set of permission. Determination of whether raw namespace extended attributes are preserved is independent of the -p flag.</span></p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -cp /user/hadoop/file1 /user/hadoop/file2</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -cp /user/hadoop/file1 /user/hadoop/file2 /user/hadoop/dir</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">du</span></h2>
<p>Usage: hdfs dfs -du [-s] [-h] URI [URI ...]</p>
<p>显示文件(<span style="font-family:'宋体';">夹</span><span style="font-family:Verdana;">)</span><span style="font-family:'宋体';">大小</span>.</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -s option will result in an aggregate summary of file lengths being displayed, rather than the individual files.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -h option will format file sizes in a "human-readable" fashion (e.g 64.0m instead of 67108864)</span></p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -du /user/hadoop/dir1 /user/hadoop/file1 hdfs://nn.example.com/user/hadoop/dir1</span></p>
<p>Exit Code: Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">dus</span></h2>
<p>Usage: hdfs dfs -dus &lt;args&gt;</p>
<p>Displays a summary of file lengths.</p>
<p>Note: This command is deprecated. Instead use hdfs dfs -du -s.</p>
<h2><span style="color:#ff0000;">expunge</span></h2>
<p>Usage: hdfs dfs -expunge</p>
<p>清空回收站.</p>
<h2><span style="color:#ff0000;">get</span></h2>
<p>Usage: hdfs dfs -get [-ignorecrc] [-crc] &lt;src&gt; &lt;localdst&gt;</p>
<p>Copy files to the local file system. Files that fail the CRC check may be copied with the -ignorecrc option. Files and CRCs may be copied using the -crc option.</p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -get /user/hadoop/file localfile</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -get hdfs://nn.example.com/user/hadoop/file localfile</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">getfacl</span></h2>
<p>Usage: hdfs dfs -getfacl [-R] &lt;path&gt;</p>
<p>显示权限信息.</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-R: List the ACLs of all files and directories recursively.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">path</span><span style="color:rgb(51,51,51);">: File or directory to list.</span></p>
<p>Examples:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -getfacl /file</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -getfacl -R /dir</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and non-zero on error.</p>
<h2><span style="color:#ff0000;">getfattr</span></h2>
<p>Usage: hdfs dfs -getfattr [-R] -n name | -d [-e en] &lt;path&gt;</p>
<p>Displays the extended attribute names and values (if any) for a file or directory.</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-R: Recursively list the attributes for all files and directories.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-n name: Dump the named extended attribute value.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-d: Dump all extended attribute values associated with pathname.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-e </span><span style="color:rgb(51,51,51);">encoding</span><span style="color:rgb(51,51,51);">: Encode values after retrieving them. Valid encodings are "text", "hex", and "base64". Values encoded as text strings are enclosed in double quotes ("), and values encoded as hexadecimal and base64 are prefixed with 0x and 0s, respectively.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">path</span><span style="color:rgb(51,51,51);">: The file or directory.</span></p>
<p>Examples:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -getfattr -d /file</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -getfattr -R -n user.myAttr /dir</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and non-zero on error.</p>
<h2><span style="color:#ff0000;">getmerge</span></h2>
<p>Usage: hdfs dfs -getmerge &lt;src&gt; &lt;localdst&gt; [addnl]</p>
<p>合并.</p>
<h2><span style="color:#ff0000;">ls</span></h2>
<p>Usage: hdfs dfs -ls [-R] &lt;args&gt;</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -R option will return stat recursively through the directory structure.</span></p>
<p>For a file returns stat on the file with the following format:</p>
<p>permissions number_of_replicas userid groupid filesize modification_date modification_time filename</p>
<p>For a directory it returns list of its direct children as in Unix. A directory is listed as:</p>
<p>permissions userid groupid modification_date modification_time dirname</p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -ls /user/hadoop/file1</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">lsr</span></h2>
<p>Usage: hdfs dfs -lsr &lt;args&gt;</p>
<p>Recursive version of ls.</p>
<p>Note: This command is deprecated. Instead use hdfs dfs -ls -R</p>
<h2><span style="color:#ff0000;">mkdir</span></h2>
<p>Usage: hdfs dfs -mkdir [-p] &lt;paths&gt;</p>
<p>Takes path uri's as argument and creates directories.</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -p option behavior is much like Unix mkdir -p, creating parent directories along the path.</span></p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -mkdir /user/hadoop/dir1 /user/hadoop/dir2</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -mkdir hdfs://nn1.example.com/user/hadoop/dir hdfs://nn2.example.com/user/hadoop/dir</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">moveFromLocal</span></h2>
<p>Usage: hdfs dfs -moveFromLocal &lt;localsrc&gt; &lt;dst&gt;</p>
<p>Similar to put command, except that the source localsrc is deleted after it's copied.</p>
<h2><span style="color:#ff0000;">moveToLocal</span></h2>
<p>Usage: hdfs dfs -moveToLocal [-crc] &lt;src&gt; &lt;dst&gt;</p>
<p>Displays a "Not implemented yet" message.</p>
<h2><span style="color:#ff0000;">mv</span></h2>
<p>Usage: hdfs dfs -mv URI [URI ...] &lt;dest&gt;</p>
<p>Moves files from source to destination. This command allows multiple sources as well in which case the destination needs to be a directory. Moving files across file systems is not permitted.</p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -mv /user/hadoop/file1 /user/hadoop/file2</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -mv hdfs://nn.example.com/file1 hdfs://nn.example.com/file2 hdfs://nn.example.com/file3 hdfs://nn.example.com/dir1</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">put</span></h2>
<p>Usage: hdfs dfs -put &lt;localsrc&gt; ... &lt;dst&gt;</p>
<p>Copy single src, or multiple srcs from local file system to the destination file system. Also reads input from stdin and writes to destination file system.</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -put localfile /user/hadoop/hadoopfile</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -put localfile1 localfile2 /user/hadoop/hadoopdir</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -put localfile hdfs://nn.example.com/hadoop/hadoopfile</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -put - hdfs://nn.example.com/hadoop/hadoopfile</span><span style="color:rgb(51,51,51);"> Reads the input from stdin.</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">rm</span></h2>
<p>Usage: hdfs dfs -rm [-f] [-r|-R] [-skipTrash] URI [URI ...]</p>
<p>Delete files specified as args.</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -f option will not display a diagnostic message or modify the exit status to reflect an error if the file does not exist.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -R option deletes the directory and any content under it recursively.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -r option is equivalent to -R.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -skipTrash option will bypass trash, if enabled, and delete the specified file(s) immediately. This can be useful when it is necessary to delete files from an over-quota directory.</span></p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -rm hdfs://nn.example.com/file /user/hadoop/emptydir</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">rmr</span></h2>
<p>Usage: hdfs dfs -rmr [-skipTrash] URI [URI ...]</p>
<p>Recursive version of delete.</p>
<p>Note: This command is deprecated. Instead use hdfs dfs -rm -r</p>
<h2><span style="color:#ff0000;">setfacl</span></h2>
<p>Usage: hdfs dfs -setfacl [-R] [-b|-k -m|-x &lt;acl_spec&gt; &lt;path&gt;]|[--set &lt;acl_spec&gt; &lt;path&gt;]</p>
<p>Sets Access Control Lists (ACLs) of files and directories.</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-b: Remove all but the base ACL entries. The entries for user, group and others are retained for compatibility with permission bits.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-k: Remove the default ACL.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-R: Apply operations to all files and directories recursively.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-m: Modify ACL. New entries are added to the ACL, and existing entries are retained.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-x: Remove specified ACL entries. Other ACL entries are retained.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">--set: Fully replace the ACL, discarding all existing entries. The </span><span style="color:rgb(51,51,51);">acl_spec</span><span style="color:rgb(51,51,51);"> must include entries for user, group, and others for compatibility with permission bits.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">acl_spec</span><span style="color:rgb(51,51,51);">: Comma separated list of ACL entries.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">path</span><span style="color:rgb(51,51,51);">: File or directory to modify.</span></p>
<p>Examples:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -setfacl -m user:hadoop:rw- /file</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -setfacl -x user:hadoop /file</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -setfacl -b /file</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -setfacl -k /dir</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -setfacl --set user::rw-,user:hadoop:rw-,group::r--,other::r-- /file</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -setfacl -R -m user:hadoop:r-x /dir</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -setfacl -m default:user:hadoop:r-x /dir</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and non-zero on error.</p>
<h2><span style="color:#ff0000;">setfattr</span></h2>
<p>Usage: hdfs dfs -setfattr -n name [-v value] | -x name &lt;path&gt;</p>
<p>Sets an extended attribute name and value for a file or directory.</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-b: Remove all but the base ACL entries. The entries for user, group and others are retained for compatibility with permission bits.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-n name: The extended attribute name.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-v value: The extended attribute value. There are three different encoding methods for the value. If the argument is enclosed in double quotes, then the value is the string inside the quotes. If the argument is prefixed with 0x or 0X, then it is taken as a hexadecimal number. If the argument begins with 0s or 0S, then it is taken as a base64 encoding.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">-x name: Remove the extended attribute.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">path</span><span style="color:rgb(51,51,51);">: The file or directory.</span></p>
<p>Examples:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -setfattr -n user.myAttr -v myValue /file</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -setfattr -n user.noValue /file</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -setfattr -x user.myAttr /file</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and non-zero on error.</p>
<h2><span style="color:#ff0000;">setrep</span></h2>
<p>Usage: hdfs dfs -setrep [-R] [-w] &lt;numReplicas&gt; &lt;path&gt;</p>
<p>Changes the replication factor of a file. If path is a directory then the command recursively changes the replication factor of all files under the directory tree rooted at path.</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -w flag requests that the command wait for the replication to complete. This can potentially take a very long time.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -R flag is accepted for backwards compatibility. It has no effect.</span></p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -setrep -w 3 /user/hadoop/dir1</span></p>
<p>Exit Code:</p>
<p>Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">stat</span></h2>
<p>Usage: hdfs dfs -stat URI [URI ...]</p>
<p>Returns the stat information on the path.</p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -stat path</span></p>
<p>Exit Code: Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">tail</span></h2>
<p>Usage: hdfs dfs -tail [-f] URI</p>
<p>Displays last kilobyte of the file to stdout.</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -f option will output appended data as the file grows, as in Unix.</span></p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -tail pathname</span></p>
<p>Exit Code: Returns 0 on success and -1 on error.</p>
<h2><span style="color:#ff0000;">test</span></h2>
<p>Usage: hdfs dfs -test -[ezd] URI</p>
<p>Options:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -e option will check to see if the file exists, returning 0 if true.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -z option will check to see if the file is zero length, returning 0 if true.</span></p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">The -d option will check to see if the path is directory, returning 0 if true.</span></p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -test -e filename</span></p>
<h2><span style="color:#ff0000;">text</span></h2>
<p>Usage: hdfs dfs -text &lt;src&gt;</p>
<p>Takes a source file and outputs the file in text format. The allowed formats are zip and TextRecordInputStream.</p>
<h2><span style="color:#ff0000;">touchz</span></h2>
<p>Usage: hdfs dfs -touchz URI [URI ...]</p>
<p>Create a file of zero length.</p>
<p>Example:</p>
<p><span style="color:rgb(51,51,51);">· </span><span style="color:rgb(51,51,51);">hdfs dfs -touchz pathname</span></p>
<p>Exit Code: Returns 0 on success and -1 on error.</p>
<h2> </h2>
            </div>
                </div>