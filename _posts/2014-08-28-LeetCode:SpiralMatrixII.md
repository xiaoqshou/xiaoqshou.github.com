---
date: 2014-08-28 11:22:10
layout: post
title: LeetCode:Spiral Matrix II
categories: LeetCode
tags: LeetCode
comments: false
---

Given an integer n, generate a square matrix filled with elements from 1 to n2 in spiral order.

For example,
Given n = 3,
You should return the following matrix:

[

     [ 1, 2, 3 ],

     [ 4, 5, 6 ],

     [ 7, 6, 5 ]

]

***
Java solution one:


		public int[][] generateMatrix(int n) {
			int[][] results = new int[n][n];
			int num = 1;
			int length = n;
			if(length>=2)
			{
				for(int i=0;i<n/2;i++)
				{
					for(int j = 0;j<length-1;j++)
						results[i][j+i]= num++;
					for(int j=0;j<length-1;j++)
						results[j+i][n-1-i]= num++;
					for(int j=0;j<length-1;j++)
						results[n-1-i][n-j-1-i]=num++;
					for(int j=0;j<length-1;j++)
						results[n-j-1-i][i]=num++;
					length=length-2;
				}
			}
			if(length==1)
				results[n/2][n/2]=num;
			return results;
			}

