# Big Data Project - Inverted-Index

What is Inverted Indexing?<br />
We can see it as a data structure that is used by most search engines to quickly find content or web pages which contain specific words or phrases.
Here, a word in a document is indexed, along with a reference to the location of the word in the document.
This is what makes it a faster search as it does not need to scan through each document entirely.

Hadoop Version used: Hadoop-3.2.1
Java Version used: 1.8.0_362

Steps to follow:
1)	Made two sample files in a folder named as input in Downloads:<br />
    sample1.txt<br />
    5722018411	Hello World Bye World
  	
    sample2.txt<br />
    6722018415	Hello Hadoop Goodbye Hadoop

3)	Make an input directory “input”
    command: hdfs dfs -mkdir /input

4)	Put the sample files from Downloads/input to input directory in hadoop
    hdfs dfs –put  /home/keshavgarg/Downloads/input/sample1.txt  /input/
    hdfs dfs –put  /home/keshavgarg/Downloads/input/sample2.txt  /input/

    Come to hadoop-3.2.1 folder using command 'Cd ..'

5)	Then type the command:
    bin/hadoop jar share/hadoop/mapreduce/invertedindex.jar InvertedIndex /input /output

6)	Type hdfs dfs -cat /input/part-r-00000


How to convert java file to jar file:

1)	Add these line to the hadoop-env.sh or set them in terminal
    export PATH=${JAVA_HOME}/bin:${PATH}
    export HADOOP_CLASSPATH=${JAVA_HOME}/lib/tools.jar

2)	 Copy the InvertedIndex.java to Hadoop Distributed root folder

3)	Then run these commands: 
    bin/hadoop com.sun.tools.javac.Main InvertedIndex.java
    jar cf invertedindex.jar InvertedIndex*.class

4)	It will create a jar file along with three class files, copy all of them in
    hadoop-3.2.1/share/hadoop/mapreduce
