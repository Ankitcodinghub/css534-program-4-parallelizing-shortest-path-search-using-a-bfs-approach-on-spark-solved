# css534-program-4-parallelizing-shortest-path-search-using-a-bfs-approach-on-spark-solved
**TO GET THIS SOLUTION VISIT:** [CSS534 Program 4: Parallelizing Shortest-Path Search, using a BFS approach on Spark Solved](https://www.ankitcodinghub.com/product/css534-program-4-parallelizing-shortest-path-search-using-a-bfs-approach-on-spark-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;100791&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;5&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (5 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CSS534  Program 4: Parallelizing Shortest-Path Search, using a BFS approach on Spark Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (5 votes)    </div>
    </div>
<h1>1. Purpose</h1>
This programming assignment gets you assimilated to Spark data transformations and actions by parallelizing BFS (breadth-first search)-based shortest-path search.

&nbsp;

<h1>2. Spark Installation and Lab 4A/B</h1>
You need to install Spark independently in your cssmpi Linux account. Follow spark2.3.1_installtion.docx. You can find spark-2.3.1-bin-hadoop2.7.tgz under the /home/NETID/css534/ directory. Please copy it to your account rather than download the file from http://spark.apache.org/.

&nbsp;

<ul>
<li><strong>Lab 4A: </strong>play with pySpark a little, as referring to DataParallel1.ppt’s page 6. Thereafter, write MyClass.java as referring to DataParallel1.ppt’s page 10, compile it, and run it on a single node.</li>
<li><strong>Lab 4B: </strong>set up a Spark standalone cluster in your account, as referring to spark=2.3.1_instllation.docx.</li>
</ul>
Thereafter, copy /home/NETID/css534/programming/Spark/JavaWordCountFlatMp.java to your account, and replace&nbsp; <strong>lines.flatMap( s -&gt; Arrays.asList( s.split( </strong><strong>” “</strong><strong> ) ).iterator() ); </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong>with

<strong>lines.flatMap( new FlatMapFunction&lt;String, String&gt;() { … }); </strong>&nbsp;Then, compile and run it on both a single machine and over parallel machines.

<strong>&nbsp;</strong>

<h1>3. BFS-based Shortest-Path Search and Graph Definition</h1>
Although Dijkstra’s shortest-path search is well known, due to tis dynamic programming aspect, it is quite difficult to parallelize. As discussed in MapReduce, breadth-first search over a given network is easy to parallelize. We will use the same approach but introduce a little more complication to it by giving each graph edge a different weight. For this purpose, we need to define in an input file not only vertex-tovertex edge connectivity but also its weight. The input file format we would like to use is:

&nbsp;

vertexId1=neighbor1,linkWeight1;nieghbor2,linkWeight2;neighbor3,linkWeight3;… vertexId2=…

&nbsp;

For instance, the following 5-vertex graph can be represented in an input file below:

<strong>&nbsp;</strong>

0=3,4;1,3

1=0,3;2,4

2=1,4;3,2;4,1

3=0,4;2,2

4=2,1

For your convenience, you can use GraphGen.class to generate a random network. Copy GraphGen.class and Map.class into your account and type:

<strong>java GraphGen #vertices filename </strong>

Where #vertices is the number of vertices of a graph you want to create and filename is the name of a file that includes all the connectivity and weight information. For example, if you want to create a graph of 3000 vertices and save its information into graph.txt, type:

<strong>java GraphGen 3000 graph.txt </strong>

&nbsp;

<h1>4.Algorithm</h1>
<strong>The main( String[] args ) function</strong> receives three arguments: (1) an input file name, (2) source vertex Id, and (3) destination vertex Id. Thereafter read the input file and start a timer for performance measurement.

&nbsp;

<strong>&nbsp;&nbsp;&nbsp; </strong><strong>// start Sparks and read a given input file&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong>

<strong>&nbsp;&nbsp;&nbsp; </strong><strong>String</strong> <strong>inputFile</strong><strong> = args[0]; </strong>

<h2>&nbsp;&nbsp;&nbsp; SparkConf conf = new SparkConf( ).setAppName( “BFS-based Shortest Path Search” );</h2>
<strong>&nbsp;&nbsp;&nbsp; </strong><strong>JavaSparkContext</strong> <strong>jsc</strong><strong> = </strong><strong>new</strong> <strong>JavaSparkContext</strong><strong>( conf ); </strong>

<strong>&nbsp;&nbsp;&nbsp; JavaRDD&lt;String&gt; lines = jsc.textFile( inputFile ); </strong>

<strong>&nbsp;</strong>

<strong>&nbsp;&nbsp;&nbsp; </strong><strong>// now start a timer&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>&nbsp;&nbsp;&nbsp;&nbsp;</strong><strong>long</strong> <strong>startTime</strong><strong> = System.currentTimeMillis(); </strong>

&nbsp;

After reading a graph definition into the <strong>lines</strong> RDD, create <strong>JavaPairRDD&lt;String, Data&gt; network</strong> by calling a transformation, <strong>lines.mapToPair( line -&gt; { … } );</strong> where <strong>String</strong> is each vertex Id such as “0”, “1”, “2”, … and <strong>Data</strong> is a Data instance that includes the corresponding vertex’s attributes as defined below:

&nbsp;

<strong>import</strong> <strong>java</strong><strong>.</strong><strong>io</strong><strong>.</strong><strong>Serializable</strong><strong>; </strong><strong>import</strong> <strong>java</strong><strong>.</strong><strong>util</strong><strong>.</strong><strong>ArrayList</strong><strong>; </strong><strong>import</strong> <strong>java</strong><strong>.</strong><strong>util</strong><strong>.</strong><strong>List</strong><strong>; </strong><strong>import</strong> <strong>scala</strong><strong>.</strong><strong>Tuple2</strong><strong>; </strong>

<strong>/**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong>

<strong>&nbsp;* Vertex Attributes&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong>

<h2>&nbsp;*/</h2>
<strong>public</strong> <strong>class</strong> <strong>Data</strong> <strong>implements</strong> <strong>Serializable</strong><strong> { </strong>

<strong>&nbsp;&nbsp;&nbsp; List&lt;Tuple2&lt;String,Integer&gt;&gt; neighbors; </strong><strong>// &lt;neighbor0, weight0&gt;, …&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>&nbsp;&nbsp;&nbsp;&nbsp;</strong><strong>String</strong> <strong>status</strong><strong>;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>// “INACTIVE” or “ACTIVE”&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong>

<strong>&nbsp;&nbsp;&nbsp; </strong><strong>Integer</strong> <strong>distance</strong><strong>;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>// the distance so far from source to this vertex&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;</strong>

<strong>&nbsp;&nbsp;&nbsp; </strong><strong>Integer</strong> <strong>prev</strong><strong>;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>// the distance calculated in the previous iteration&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong>

<strong>&nbsp;</strong>

<strong>&nbsp;&nbsp;&nbsp; </strong><strong>public</strong><strong> Data(){ </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; neighbors = </strong><strong>new</strong> <strong>ArrayList</strong><strong>&lt;&gt;();&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; status = </strong><strong>“INACTIVE”</strong><strong>;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; distance = 0; </strong>

<strong>&nbsp;&nbsp;&nbsp; }&nbsp; </strong>

<strong>&nbsp;&nbsp;&nbsp; </strong><strong>public</strong><strong> Data( List&lt;Tuple2&lt;String,Integer&gt;&gt; neighbors,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>Integer</strong> <strong>dist</strong><strong>, </strong><strong>Integer</strong> <strong>prev</strong><strong>, </strong><strong>String</strong> <strong>status</strong><strong> ){&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>if</strong><strong> ( neighbors != null ) { </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>this</strong><strong>.neighbors = </strong><strong>new</strong> <strong>ArrayList</strong><strong>&lt;&gt;( neighbors ); </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; } </strong><strong>else</strong><strong> { </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>this</strong><strong>.neighbors = </strong><strong>new</strong> <strong>ArrayList</strong><strong>&lt;&gt;( ); </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; } </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>this</strong><strong>.distance = dist;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>this</strong><strong>.prev = prev;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>this</strong><strong>.status = status; </strong>

<strong>&nbsp;&nbsp;&nbsp; } }</strong>

Note that, when you instantiate each vertex with a Data instance, you have to make sure that the source vertex’s <strong>Data.status</strong> must be <strong>“ACTIVE”</strong>, while all the other vertices’ status should be “<strong>INACTIVE</strong>”. This way your program can execute at least the very first iteration of the following <strong>while</strong> loop:

&nbsp;

<strong>&nbsp; </strong><strong>while </strong><strong>(</strong><strong>t here are any “ACTIVE” vertices</strong><strong> ) { </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>JavaPairRDD&lt;String, Data&gt; propagatedNetwork = network.flatMapToPair( vertex-&gt; { </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>// If a vertex is “ACTIVE”, create Tuple2( neighbor, new Data( … ) ) for&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // each neighbor where Data should include a new distance to this neighbor. </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // Add each Tuple2 to a list. Don’t forget this vertex itself back to the&nbsp; </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // list. Return all the list items. </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; } ); </strong>

<strong>&nbsp;</strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>network = propagatedNetwork.reduceByKey( ( k1, k2 ) -&gt;{ </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>// For each key, (i.e., each vertex), find the shortest distance and&nbsp; </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // update this vertex’ Data attribute. </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; } ); </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>network = network.mapValues( value -&gt; { </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>// If a vertex’ new distance is shorter than prev, activate this vertex&nbsp;&nbsp; </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // status and replace prev with the new distance. </strong>

<strong>&nbsp;&nbsp;&nbsp;&nbsp; </strong><strong>} ); </strong>

<strong>&nbsp; </strong><strong>} </strong>

&nbsp;

The above <strong>while</strong> loop includes three RDD Transformations: (1) flatMapToPair to create a network that received all distance propagations from the current vertices to their neighbors, (2) reduceByKey to reduce all redundant, identical keys, (i.e., vertices) to a single vertex, and (3) mapValues to activate only vertices whose distance got shorter than prev.

&nbsp;

After completing this <strong>while</strong> loop, stop the timer to measure the time elapsed for the program execution. Don’t forget to retrieve the destination vertex’ distance. That is the shortest path to find.

<strong>&nbsp;</strong>

<ol start="5">
<li><strong> Coding, Compilation, Input Set-up, and Execution </strong>(1)Coding: save your Java source as ShortestPath.java.</li>
</ol>
&nbsp;

(2)Compilation: you may use Maven or directly compile as:

<strong>javac -cp jars/spark-core_2.11-2.3.1.jar:jars/spark-sql_2.11-</strong>

<strong>2.3.1.jar:jars/scala-library-2.11.8.jar:google-collections-1.0.jar:. </strong>

<strong>ShortestPath.java </strong>

<strong>&nbsp; </strong>

<strong>jar -cvf ShortestPath.jar ShortestPath.class Data.class</strong>

&nbsp;

<ul>
<li>Execution:</li>
</ul>
<strong>java GraphGen 3000 graph.txt </strong>

<strong>&nbsp;</strong>

<strong>Spark-submit –class ShortestPath –master spark://cssmpi1h:58000 –executormemory 1G –total-executor-cores 1 ShortestPath.jar graph.txt 0 2999</strong>

&nbsp;

<ul>
<li>Output:</li>
</ul>
Sample outputs are:

<strong>Spark-submit –class ShortestPath –master spark://cssmpi1h:58000 –executormemory 1G –total-executor-cores 1 ShortestPath.jar graph.txt 0 1500 </strong>

<strong>&nbsp;</strong>

<strong>from 0 to 1500 takes distance = 41 </strong>

<strong>&nbsp;</strong>

<strong>Spark-submit –class ShortestPath –master spark://cssmpi1h:58000 –executormemory 1G –total-executor-cores 1 ShortestPath.jar graph.txt 0 2999 </strong>

<strong>&nbsp;</strong>

<strong>from 0 to 2999 takes distance = 32 </strong>

<strong>&nbsp;</strong>

Note that the executor memory of 1G is enough for a network of 3000 vertices. But if you want to test your program with a larger network, you might want to increase the size.

<strong>&nbsp;</strong>

<h1>6. Statement of Work</h1>
Step 1: Code your ShortestPath.java. You may use: GraphGen.java, Map.java, and Data.java. For your initial implementation, follow the algorithm shown above and go to Step 2. If your time allows, you may improve the execution performance of your program by modifying the above code framework or even using a different approach you would like to try.

&nbsp;

Step 2:&nbsp; Compare the performance of the following 12 different executions of your ShortestPath program, using a graph of 3000 vertices. The source and destination vertices should be 0 and 1500 respectively.

<strong>Spark-submit –class ShortestPath –master spark://cssmpi1h:58000 –executormemory 1G –total-executor-cores 1 ShortestPath.jar graph.txt 0 1500 </strong>

&nbsp;

If you want, you may use sp_compile.sh and sp_run.sh scripts, both found in:&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; /home/NETID/css534/programming/Spark.

&nbsp;

The following table shows the performance of the professor’s key answer execution. The best performance improvement by parallel execution is <strong>1.758 times</strong> faster with 3 computing nodes, using 3 cores in total than a sequential execution.

<table width="496">
<tbody>
<tr>
<td width="100"># computing nodes</td>
<td width="96">Ave # cores per node</td>
<td width="102">Total # cores</td>
<td width="90">Elapsed time (sec)</td>
<td width="108">Performance improvement</td>
</tr>
<tr>
<td width="100">1</td>
<td width="96">1</td>
<td width="102">1</td>
<td width="90">371.800</td>
<td width="108">1.000</td>
</tr>
<tr>
<td width="100">1</td>
<td width="96">2</td>
<td width="102">2</td>
<td width="90">268.511</td>
<td width="108">1.385</td>
</tr>
<tr>
<td width="100">1</td>
<td width="96">3</td>
<td width="102">3</td>
<td width="90">265.601</td>
<td width="108">1.400</td>
</tr>
<tr>
<td width="100">1</td>
<td width="96">4</td>
<td width="102">4</td>
<td width="90">263.382</td>
<td width="108">1.385</td>
</tr>
<tr>
<td width="100">2</td>
<td width="96">1</td>
<td width="102">2</td>
<td width="90">211.483</td>
<td width="108">1.758</td>
</tr>
<tr>
<td width="100">2</td>
<td width="96">2</td>
<td width="102">4</td>
<td width="90">212.458</td>
<td width="108">1.750</td>
</tr>
<tr>
<td width="100">2</td>
<td width="96">3</td>
<td width="102">6</td>
<td width="90">220.626</td>
<td width="108">1.685</td>
</tr>
<tr>
<td width="100">2</td>
<td width="96">4</td>
<td width="102">8</td>
<td width="90">220.794</td>
<td width="108">1.684</td>
</tr>
<tr>
<td width="100"><strong>3 </strong></td>
<td width="96"><strong>1 </strong></td>
<td width="102"><strong>3 </strong></td>
<td width="90"><strong>211.473 </strong></td>
<td width="108"><strong>1.758 </strong></td>
</tr>
<tr>
<td width="100">3</td>
<td width="96">2</td>
<td width="102">6</td>
<td width="90">220.496</td>
<td width="108">1.686</td>
</tr>
<tr>
<td width="100">3</td>
<td width="96">3</td>
<td width="102">9</td>
<td width="90">237.306</td>
<td width="108">1.567</td>
</tr>
<tr>
<td width="100">3</td>
<td width="96">4</td>
<td width="102">12</td>
<td width="90">226.306</td>
<td width="108">1.643</td>
</tr>
<tr>
<td width="100">4</td>
<td width="96">1</td>
<td width="102">4</td>
<td width="90">213.598</td>
<td width="108">1.741</td>
</tr>
<tr>
<td width="100">4</td>
<td width="96">2</td>
<td width="102">8</td>
<td width="90">224.098</td>
<td width="108">1.659</td>
</tr>
<tr>
<td width="100">4</td>
<td width="96">3</td>
<td width="102">12</td>
<td width="90">226.633</td>
<td width="108">1.641</td>
</tr>
<tr>
<td width="100">4</td>
<td width="96">4</td>
<td width="102">16</td>
<td width="90">229.745</td>
<td width="108">1.618</td>
</tr>
<tr>
<td width="100">5</td>
<td width="96">1</td>
<td width="102">5</td>
<td width="90">223.575</td>
<td width="108">1.663</td>
</tr>
<tr>
<td width="100">5</td>
<td width="96">2</td>
<td width="102">10</td>
<td width="90">223.103</td>
<td width="108">1.666</td>
</tr>
<tr>
<td width="100">5</td>
<td width="96">3</td>
<td width="102">15</td>
<td width="90">217.056</td>
<td width="108">1.713</td>
</tr>
<tr>
<td width="100">5</td>
<td width="96">4</td>
<td width="102">20</td>
<td width="90">220.251</td>
<td width="108">1.688</td>
</tr>
</tbody>
</table>
&nbsp;

Step 3: Discuss about the following items in your report:

<ul>
<li>Mandatory discussion on pros and cons of the original algorithm/code framework shown in this homework specification.
<ol>
<li>Discussion from the programmability viewpoint.</li>
<li>Discussion from the viewpoint of execution performance.</li>
</ol>
</li>
<li>Optional discussion on pros and cons of your improved algorithm if you implemented any.
<ol>
<li>Discussion from the programmability viewpoint.</li>
<li>Discussion from the viewpoint of execution performance.</li>
</ol>
</li>
</ul>
&nbsp;

<h1>7. What to Turn in</h1>
This programming assignment is due at the beginning of class on the due date. Please turn in the following materials in a hard copy. No email submission is accepted.

<table width="696">
<tbody>
<tr>
<td width="622"><strong>Criteria </strong></td>
<td width="75"><strong>Grade </strong></td>
</tr>
<tr>
<td width="622"><strong>Documentation </strong>of your BFS-based shortest-path search program in <u>just <strong>one page</strong> <strong>please</strong>.</u></td>
<td width="75">20pts</td>
</tr>
<tr>
<td width="622"><strong>Source code</strong> that adheres good modularization, coding style, and an appropriate amount of commends.

•&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 25pts: well-organized and correct code receives

•&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 23pts: messy yet working code or code with minor errors receives

•&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 20pts: code with major bugs or incomplete code receives
</td>
<td width="75">25pts</td>
</tr>
<tr>
<td width="622"><strong>Execution output</strong> that verifies the correctness of your implementation and demonstrates any improvement of your program’s execution performance.

•&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 25pts: Correct execution and better performance than your professor’s program execution (1.75). It should be at least 5% better in terms of performance improvement, (i.e., 1.83 or better).

•&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 23pts: Correct execution and the same performance as your professor’s program execution (between -5% and +5%, i.e., between 1.66 and 1.83).

•&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 20pts: Correct execution but the slower performance than your professor’s program execution, (i.e., -5% or slower = 1.66 or worse).

•&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 15pts: Wrong or incomplete work.
</td>
<td width="75">25pts</td>
</tr>
<tr>
<td width="622"><strong>Discussions </strong>about <u>in one page</u>.

•&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Pros and cons of program 4’s original algorithm o Programmability (10pts) o Execution performance (10pts)

•&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Optional: pros and cons of your improved algorithm if you implemented any. o Programmability (extra 2pts) o Execution performance (extra 2pts)
</td>
<td width="75">20pts</td>
</tr>
<tr>
<td width="622"><strong>Lab Session 4A</strong> Please turn in your lab 4A and 4B together with date of program 4. Your source code and execution outputs are required.

•&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 4A submitted (5pts)

•&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 4B submitted (5pts)
</td>
<td width="75">10pts</td>
</tr>
<tr>
<td width="622"><strong>Total </strong>

Note that program 4 takes 15% of your final grade.
</td>
<td width="75">100pts</td>
</tr>
</tbody>
</table>
&nbsp;
