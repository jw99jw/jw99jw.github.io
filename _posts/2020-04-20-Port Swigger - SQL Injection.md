---
layout: post
title: 
categories: [SQL Injection]
tags: [SQL Injection]
---

# SQL Injection - What is it?

Nearly every applications rely on database to process all the data. And those databases contain credentials - such as user accounts and even administrator accounts. 

So, in order to keep those data in shape, databases use SQL, which stands for Structured Query Language. SQL lets you access and manipulate databases. 

It can let you do: 

  -execute queries against a database
  
  -retrieve data from a database
  
  -insert records in a database
  
  -update records in a database
  
  -delete records from a database
  
  -create new databases
  
  -create new tables in a database
  
  -create stored procedures in a database
  
  -create views in a database
  
  -set permissions on tables, procedures, and views

Since SQL is a simple programming language and very powerful at the same time, attackers are able to inject arbitrary code and exploit your databases. 

SQL injection is one of the most common web hacking techniques. 

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164270793-d14b11ff-ed84-4879-8c3f-30dc9d09335d.jpg"/>

SQL injection is the placement of malicious code in SQL statements, through web page input.

# Type of SQL Injection
<img width="70%" src="https://user-images.githubusercontent.com/69608504/164273118-2a67b87a-0528-4860-9315-56ea75600222.jpg"/>

## 1. In-Band(Classic)
The attacker uses the same communication channel to both launch the attack and gather the result of the attack. The retrieved data is presented directly inthe application web page.
This method is easier to exploit than other categories of SQL injection.

### Error-Based SQL Injection
In-band SQL injection technique that forces the database to generate an error, giving the attacker information upon which to refine their injection.

### Union Based SQL Injection
In-band SQL injection technique that leverages the UNION SQL operator to combine the results of two queries into a single result set.

## 2. Inferential(Blind)
There are no actual transfer of data via the web application. But it is just as dangerous as in-band SQL injection. The attacker is able to reconstruct the information by sending particular requests and observing the resulting behavior of the database server.
Since there are no visible signs of attack, it takes longer to exploit than in-band SQL injection.

### Boolean Based SQL Injection
This technique uses Boolean conditions to return a different result dependingon whether the query returns a TRUE or FALSE result.

### Time Based SQL Injection
this relies on the database pausing for a specified amount of time, then returns the results, indicating a successful SQL query execution.

## 3. Out-of-Band (OAST) SQL injection
This exploits vulnerability that consists of triggering an out-of-band network connection to a system that you control. 
This technique is used when all the other tecnhiques don't work. And this technique is not very common, wince it relies on certain features being enabled in the database for it to actually make the network connection.
You could use a variety of protocols for this technique, but the most commonly used ones are DNS and HTTP. 

## 2. 
