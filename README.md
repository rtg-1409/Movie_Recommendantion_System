## Movie-Recommendation-System

A movie recommender based on user's watching history implemented in Java, Hadoop with collaborative filtering algorithms.

## Environment

First, this project used docker to construct hadoop cluster. Make sure you have installed docker. Then execute following lines in terminal(Mac and Linux):

```
$ sudo docker pull joway/hadoop-cluster # download mirror from dockerhub to construct hadoop cluster.

$ git clone https://github.com/joway/hadoop-cluster-docker

$ sudo docker network create --driver=bridge hadoop # Construct bridge for hadoop namenode and datanode.

$ cd hadoop-cluster-docker
```
Then start docker container and run hadoop:

```
$ sudo ./start-container.sh

$ ./start-hadoop.sh
```


## Usage
Enter src directory and compile java files. Generate output to corresponding directory:

```
$ cd src/main/java/

$ hadoop com.sun.tools.javac.Main *.java

$ jar cf recommender.jar *.class

$ hadoop jar recommender.jar Driver /input /dataDividedByUser /coOccurrenceMatrix /Normalize /Multiplication /Sum

$ hdfs dfs -cat /Sum/*

```

1.`</input>`: original dataset

2.`</dataDividedByUser>`:  output directory for DividerByUser job

3.`</coOccurrenceMatrix>`:  output directory for coOccurrenceMatrixBuilder job

4.`</Normalize>`:  output directory for Normalize job

5.`</Multiplication>`:  output directory for Multiplication job

6.`</Sum>`:  output directory for Sum job

## Source of data

Netflix Prize: https://www.netflixprize.com/

