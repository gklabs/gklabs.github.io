---
layout: post
title: "A gentle introduction to Hadoop"
date: 2020-05-25 19:00:00
categories: Big Data Hadoop
---
status: in progress


Introduction
====================

This article aims to simplify and make Hadoop less cooler by understanding the overall purpose and working of a file system. 

Why do we care about Big Data ?
==========================

Consider the following facts:
* Humans and human created systems generate a lot of data.
* 95% of the new data was generated between 2010- 2016


![Information growth](/assets/Hilbert_InfoGrowth.png){:class="img-responsive"}


As data storage technology improved, so did the we start to store all kinds of data- logs, text, video, audio, images.

To summarise, we characterize Big data by the following features.
* Volume- The quantity of the generated data.
* Velocity- The speed at which data is generated and processed to meet the demands.
* Variety- The type and nature of data

We also talk about _veracity_ indicating the quality of the data captured.

Data is knowledge and knowledge is wealth. If Machine learning models are a vehicle, then the fuel that drives the vehicle is data. Thus there is a need to build a cheap and efficient file system architecture that can help in fast accessibility and retrieval of data. Hadoop is one such architecture.

Bob and the magic godown: An anology for Hadoop
=================
Consider farmer Abe cultivating rice and has a storage space in his house to store his yield. But the storage space is enough just to store yield of 100 sacks while on a good year he can end up with a yield more than 300 to 500 sacks. He would now have to approach the magic godown whose owner Bob is a friend to store the excess yield. Bob maintains a book with the details of room capacity and a team of elves in charge of each of the rooms in the godown. He offers to store all of Abe's yield. The magic in the godown is that it can create 2 replicas of the stock that is brought to it. This is because Bob knows that his team of elves can sometimes be inefficient and therefore makes multiple copies of the stock.

Two months later Abe wants 20 sacks of rice from the godown to make rice noodles and he goes to the godown. Bob knowing that the godown is capable of magic, *asks* for the recipe for the rice noodles and gives it to the godown elves. The godown elves *apply* the recipe to the sacks of rice placed at different rooms individually and ask the elder elf to combine all of the rice noodles into a single container. The rice noodle is combined and shipped to Abe. 


What is HDFS?
==================

HDFS or Hadoop File System lets you store large amounts of data (read petabytes, zetabytes) on a scaleable and cost-efficient collection of nodes (cluster of consumer computers AKA commodity hardware). Hadoop is designed to prevent data loss while also being efficient at providing fast access to data. 

Hadoop also follows the write-once-read-many model, which simply means that data once stored is not altered but only read many times for performing tasks or executing various commands. Commands that are to be executed on the data are handled using the MapReduce processing model.

Hadoop File System has 5 components or services under 2 main categories of functions.
* Master Services
	* Name node (Bob): Manages the data block management.
	* Secondary Name node: Works concurrently with Name node.
	* Job Tracker (Elder Elf): 

* Slave services
	* Data node: Commodity hardware nodes which provide storage. Data nodes send _heartbeat_ to Name node indicating their functioning status. The interval for these heartbeats vary but is usually in the range of 3 seconds.
	* Task tracker

## Process overview
Based on the analogy, lets go through the sequence of steps of storing and retrieving data from the Hadoop File System.

1. For instance consider a file that includes phone numbers of everyone in the world entered alphabetically; The numbers of alphabet 'A' are stored on server 1 and 'B' on server 2 etc.

1. To ensure availability when any of the nodes fail, HDFS makes 2 replicas of the data and now has to find space in its storage capacity to store the data. (Known as _Redundancy_ or _fault tolerance_)

1. The cluster contains two different types hardware systems- first, the commodity hardware (usually referred to as SATA) and a second, more advanced, reliable and optimized storage hardware(usually SAS disks). The HDFS runs as a layer on top of the commodity hardware to manage incoming data. [This article](https://hadoopoopadoop.com/2015/09/22/hadoop-hardware/) explains the differences in the hardware well.

1. HDFS uses the advanced hardware to store 'metadata' or data about data on the location description of the incoming data. For instance, the incoming 100 TB of the data could be distributed among 5 machines and this information about the distribution would be stored in the advanced hardware.

1. The cluster stores data in _blocks_. Blocks are the smallest unit of data in HDFS. Each block have a size of 64 MB. HDFS tries to place each block (of the given data) on separate nodes(data nodes). The file creation process uses a _staging mechanism_ where the data to be written to HDFS is temporarily stored locally until enough data accumulates for a block. Once that accumulation is complete the Name node _commits_ the data to be written to disk.


![HDFS heartbeat process. Image from IBM's developer blog](/assets/heartbeat.jpg){:class="img-responsive"}



The Mapreduce algorithm
======================

In 2004, Google came up with the MapReduce algorithm to effectively process queries on large data repositories
* Map:

* Reduce:

References
============
* https://en.wikipedia.org/wiki/MapReduce
* https://www.ibm.com/developerworks/library/wa-introhdfs/index.html
* Big Table paper http://static.googleusercontent.com/media/research.google.com/en//archive/bigtable-osdi06.pdf
* MapReduce paper http://static.googleusercontent.com/media/research.google.com/en//archive/mapreduce-osdi04.pdf

