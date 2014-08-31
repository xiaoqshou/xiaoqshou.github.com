---
author: LiuYang
comments: false
date: 2014-08-24 11:22:10
layout: post
title: LeetCode:PalindromeNumber
categories: LeetCode
tags: LeetCode
---

Determine whether an integer is a palindrome. Do this without extra space.

## step1:

	public boolean isPalindrome(int x) {
		 if(x<0)
			 return false;
		 while((int)(Math.log10(x))>1)
		 {
			 if((int)(x/(Math.pow(10, (int)Math.log10(x))))==x%10)
			 {
				 if((int)(x/(Math.pow(10, ((int)Math.log10(x))-1)))!=0)
				 {
					 x=x%(int)(Math.pow(10,(int)Math.log10(x)));
					 x=x/10;
				 }
				 else if(x/10==0)
				 {
					 x=x%(int)(Math.pow(10,(int)Math.log10(x)));
					 x=x/100;
				 }
			 }
			 else
			 {
				 return false;
			 }
		 }
		 return true;
	}


## step2:

	public boolean isPalindrome(int x) {
		 if(x<0)
			 return false;
		 while((int)Math.log(x)>1)
		 {
			 if(((int)(x/(Math.pow(10, (int)Math.log10(x))))==x%10))
			 {
				 int size = (int)Math.log10(x);
				 int highTen = (int) (((int)(x/Math.pow(10, size)))*Math.pow(10, size));
				 int dis = size-(int)Math.log10(x-highTen);
				 if(x%Math.pow(10, dis)==x%10)
				 {
					 x-=highTen;
		 
					 x/=Math.pow(10,dis);
				 }
				 else
					 return false;
			 }
			 else
				 return false;
		 }
		 return true;
	}

## step3: without extra space

	public boolean isPalindrome(int x) {
		 if(x<0)
			 return false;
		 while(x!=0&&(int)Math.log10(x)>=1)
		 {
			 if(((int)(x/(Math.pow(10, (int)Math.log10(x))))==x%10))
			 {
				 if(x%Math.pow(10, (int)Math.log10(x)-(int)Math.log10(x-(int) (((int)(x/Math.pow(10, (int)Math.log10(x))))*Math.pow(10, (int)Math.log10(x)))))==x%10)
				 {
					 x=(int)(x/Math.pow(10,(int)Math.log10(x)-(int)Math.log10(x-(int) (((int)(x/Math.pow(10, (int)Math.log10(x))))*Math.pow(10, (int)Math.log10(x))))));
					 x-=(int) (((int)(x/Math.pow(10, (int)Math.log10(x))))*Math.pow(10, (int)Math.log10(x)));
				 }
				 else
					 return false;
			 }
			 else
				 return false;
		 }
		 return true;
	 }



