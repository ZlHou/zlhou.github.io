---
title: PAT每日一题|1001 A+B Format
url: 121.html
id: 121
categories:
  - PAT
date: 2018-09-29 09:41:46
tags:
---

Calculate a+b and output the sum in standard format -- that is, the digits must be separated into groups of three by commas (unless there are less than four digits).

### Input Specification:

Each input file contains one test case. Each case contains a pair of integers a and b where −10​6​​≤a,b≤10​6​​. The numbers are separated by a space.

### Output Specification:

For each test case, you should output the sum of a and b in one line. The sum must be written in the standard format.

### Sample Input:

    -1000000 9
    

### Sample Output:

    -999,991
    

    #include <stdio.h>
    #include <math.h>
    #include <stdlib.h>
    int sum(int a, int b) {
    	return a + b;
    }
    
    int main() {
    	int a=0, b=0, s;
    	int i = 1000, j = 0;
    	int result[9] = { 0 };
    	scanf("%d%d", &a, &b);
    	s = sum(a, b);
    	while (s / i != 0) {
    		result[j] = s % i;
    		s=s/1000;
    		j++;
    	}
    	result[j] = s % i;
    	for (i = j ; i >= 0; i--) {
    		if (i != j) {
    			result[i] = abs(result[i]);
    
    			if (result[i] == 0) {
    				printf("000");
    			}
    			else if (result[i] > 0 && result[i] < 10) {
    				printf("00%d", result[i]);
    			}
    			else if (result[i] >= 10 && result[i] < 100) {
    				printf("0%d", result[i]);
    			}
    			else {
    				printf("%d", result[i]);
    			}
    		}
    		else printf("%d", result[i]);
    		if (i != 0) {
    			printf(",");
    		}
    	}
    }