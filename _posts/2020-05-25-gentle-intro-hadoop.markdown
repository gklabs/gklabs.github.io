---
layout: post
title: "A gentle introduction to Hadoop"
date: 2020-05-25 19:00:00
categories: Big Data Hadoop

Introduction
====================

This article aims to simplify and make Hadoop less cooler by understanding the overall purpose and working of a file system. 

Why do we care about Big Data ?
==========================

Consider the following facts:
* Humans generate a lot of data.
* 95% of the new data was generated between 

We can characterize Big data by the following features.
* Volume
* Velocity
* Variety

Data is knowledge and knowledge is wealth. If Machine learning models are a vehicle, then the fuel that drives the vehicle is data. Thus there is a need to build a cheap and efficient file system architecture that can help in fast accessibility and retrieval of data. Hadoop is one such architecture.

Bob and the magic godown: An anology
=================
Consider farmer Abe cultivating rice and has a storage space in his house to store his yield. But the storage space is enough just to store yield of 100 sacks while on a good year he can end up with a yield more than 300 to 500 sacks. He would now have to approach the magic godown whose owner Bob is a friend to store the excess yield. Bob maintains a book with the details of room capacity and a team of elves in charge of each of the rooms in the godown. He offers to store all of Abe's yield. The magic in the godown is that it can create 2 replicas of the stock that is brought to it.

Two months later Abe wants 20 sacks of rice from the godown to make rice noodles and he goes to the godown. Bob knowing that the godown is capable of magic, asks for the recipe for the rice noodles and gives it to the godown elves.The godown elves *apply* the recipe to the sacks of rice placed at different rooms individually and ask the elder elf to combine all of the rice noodles into a single container. The rice noodle is combined and shipped to Abe. 


What is HDFS?
==================



Hadoop File System has 5 components or services under 2 main categories of functions.
* Master Services
	* Name node (Bob)
	* Secondary Name node
	* Job Tracker (elder elf)
* Slave services
	* Data node
	* Task tracker




The Mapreduce algorithm
======================

Map

Reduce

References
============


