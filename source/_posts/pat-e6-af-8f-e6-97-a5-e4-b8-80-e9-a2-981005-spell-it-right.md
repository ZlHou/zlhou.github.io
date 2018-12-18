---
title: PAT每日一题|1005 Spell It Right
url: 132.html
id: 132
categories:
  - PAT
date: 2018-10-02 09:19:38
tags:
---

Given a non-negative integer N, your task is to compute the sum of all the digits of N, and output every digit of the sum in English.

### Input Specification:

Each input file contains one test case. Each case occupies one line which contains an N (≤10​100​​).

### Output Specification:

For each test case, output in one line the digits of the sum in English words. There must be one space between two consecutive words, but no extra space at the end of a line.

### Sample Input:

    12345
    

### Sample Output:

    one five
    

    #include <stdio.h>
    #include <string.h>
    int main() {
    	int n, i = 0;
    	int j, sum = 0;
    	char d[110];
    	char d1[10][10]={"zero","one","two","three","four","five","six","seven","eight","nine"};
    	int result[100];
    	scanf("%s", d);
    	n = strlen(d);
    	for (i = 0; i < n; i++) {
    		sum = d[i] - '0'+sum;
    	}
    	j = 0;
    		if(sum==0){
    	  printf("zero");
    	  
    	}else{
    	while (sum != 0) {
    		result[j] = sum % 10;
    		sum = sum / 10;
    		j++;
    	}
    
    	for (i = j - 1; i >= 0; i--) {
    		printf("%s",d1[result[i]]);
    		if (i != 0) {
    			printf(" ");
    		}
    	}
    }
    }

注意：考虑输入仅为0的情况