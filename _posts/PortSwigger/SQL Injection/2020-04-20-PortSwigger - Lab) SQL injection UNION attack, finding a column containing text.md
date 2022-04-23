---
layout: post
title: Lab) SQL injection vulnerability in WHERE clause allowing retrieval of hidden data.md
categories: [PortSwigger/SQL Injection]
tags: [SQL Injection]
---

# SQL injection UNION attack, finding a column containing text

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164942711-21f3451f-b3e0-440e-8829-2c5177bbb11b.png"/>

This lab is about finding a column containing text.

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164942825-d07ee776-c883-4dba-9dc7-d2b50a828c6d.png"/>



<img width="70%" src="https://user-images.githubusercontent.com/69608504/164942861-82f23ad1-b5de-4676-93ae-48ccaaa97a8d.png"/>

In this lab, the goal is to make the database retrieve the string '2emsfU'

There is a data type called text in SQL, which is a combination of text and numbers.

In previous post, we learned that in order to make successful UNION attack, the data types of each column must be compatible between the individual queries.

So in this lab, we will learn how to find out the data type of a column.

### First, determine the number of columns in the table.

As learned in the previous post, let's submit the following query:

' ORDER BY 1--
<img width="70%" src="https://user-images.githubusercontent.com/69608504/164943061-94a4d70d-5e70-4993-aa2d-e8ee1716a4bf.png"/>

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164943079-a019a92f-3efe-4c43-ab89-2a7849bd5d35.png"/>

Nothing seems to have changed, so we can assume that the first column is a hidden value.

If we order by 2, 

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164943119-3d0c80ca-6246-412a-9cf6-5968c6429b8f.png"/>

The results are ordered by alphabetical order, so the second column seems to be the product name.

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164943145-6ae75686-21ee-4f15-9687-a632232ed7f2.png"/>

And the third column seems to be the price of the product.

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164943171-2c807302-3a08-4bca-b84f-96497376a637.png"/>

And the fourth column doesn't exist, so we can confirm that there are 3 columns in this table.

Although we know the number of columns existing, we still don't know the type of data for each columns.

This is very important, because this will cause errors in using the UNION attack.

As learned in the previous post, if the data type for each columns aren't compatible, the database will return an error.

Therefore, figuring out the data type for each columns is very important.

But how do we figure it out?

As mentioned above, text is a data type that is a combination of text and numbers, and NULL is used to represent a blank.

Let's try the basic UNION attack, including the NULL:

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164943301-d1b1e05d-3f4f-42f7-9ebc-ce1ab8c85730.png"/>

Nothin's happened. 

But let's see what happens if we change the value. 

Let's try any string. Let's say we want to select a string 'abc'. 

Then we can change the input to:

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164943371-20656f0f-7699-4e97-8ca8-1244935a7d51.png"/>

https://user-images.githubusercontent.com/69608504/164943414-f7016e53-f601-4ce1-a15f-a92f2b00e4c3.png

Error message is returned. 

If we change the query into:

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164943455-543f9343-3426-4b7c-9f87-86d18548e638.png"/>

Something different happened.

There is another row containing the input that we submitted. 

This could be done because the second column consists of text type data.

The UNION attack could be done because the text type was compatible.

Let's try same thing for the third column.

https://user-images.githubusercontent.com/69608504/164943414-f7016e53-f601-4ce1-a15f-a92f2b00e4c3.png

Error message is returned.

In the third column, we checked that there are numbers. In SQL, there are a lot of types for representing a number. 

A number could be translated to text, but the opposite is impossible.

This could be checked in the following example.

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164943652-f1596b19-1533-44b4-b375-360daeb882ea.png"/>

It proves that the value 123 is compatible with text data.

Now, to solve the lab, we need to retrieve the string: '2emsfU'

Let's change the input and submit it.

<img width="70%" src="https://user-images.githubusercontent.com/69608504/164943722-682c2c63-c441-4d67-9687-33b50c2e210f.png"/>

We just solved the lab!

