---
title: PAT每日一题|1027 Colors in Mars
url: 141.html
id: 141
categories:
  - PAT
date: 2018-10-02 23:01:30
tags:
---

People in Mars represent the colors in their computers in a similar way as the Earth people. That is, a color is represented by a 6-digit number, where the first 2 digits are for `Red`, the middle 2 digits for `Green`, and the last 2 digits for `Blue`. The only difference is that they use radix 13 (0-9 and A-C) instead of 16. Now given a color in three decimal numbers (each between 0 and 168), you are supposed to output their Mars RGB values.

### Input Specification:

Each input file contains one test case which occupies a line containing the three decimal color values.

### Output Specification:

For each test case you should output the Mars RGB value in the following format: first output `#`, then followed by a 6-digit number where all the English characters must be upper-cased. If a single color is only 1-digit long, you must print a `0` to its left.

### Sample Input:

    15 43 71
    

### Sample Output:

    #123456
    

    #include <stdio.h>
    #include <string.h>
    int main() {
    	int r, g, b;
    	int i;
    	char s1[2] = { '0' }, s2[2] = { '0' }, s3[2] = { '0' };
    	scanf("%d%d%d", &r, &g, &b);
    	i = 0;
    	while (i<=1) {
    		if (r % 13 == 0) s1[i] = '0';
    		else if (r % 13 == 1) s1[i] = '1';
    		else if (r % 13 == 2) s1[i] = '2';
    		else if (r % 13 == 3) s1[i] = '3';
    		else if (r % 13 == 4) s1[i] = '4';
    		else if (r % 13 == 5) s1[i] = '5';
    		else if (r % 13 == 6) s1[i] = '6';
    		else if (r % 13 == 7) s1[i] = '7';
    		else if (r % 13 == 8) s1[i] = '8';
    		else if (r % 13 == 9) s1[i] = '9';
    		else if (r % 13 == 10) s1[i] = 'A';
    		else if (r % 13 == 11) s1[i] = 'B';
    		else if (r % 13 == 12) s1[i] = 'C';
    		i++; r = r / 13;
    	}
    	if (r % 13 == 0) s1[i] = '0';
    	else if (r % 13 == 1) s1[i] = '1';
    	else if (r % 13 == 2) s1[i] = '2';
    	else if (r % 13 == 3) s1[i] = '3';
    	else if (r % 13 == 4) s1[i] = '4';
    	else if (r % 13 == 5) s1[i] = '5';
    	else if (r % 13 == 6) s1[i] = '6';
    	else if (r % 13 == 7) s1[i] = '7';
    	else if (r % 13 == 8) s1[i] = '8';
    	else if (r % 13 == 9) s1[i] = '9';
    	else if (r % 13 == 10) s1[i] = 'A';
    	else if (r % 13 == 11) s1[i] = 'B';
    	else if (r % 13 == 12) s1[i] = 'C';
    
    	i = 0;
    	while (i<=1) {
    		if (g % 13 == 0) s2[i] = '0';
    		else if (g % 13 == 1) s2[i] = '1';
    		else if (g % 13 == 2) s2[i] = '2';
    		else if (g % 13 == 3) s2[i] = '3';
    		else if (g % 13 == 4) s2[i] = '4';
    		else if (g % 13 == 5) s2[i] = '5';
    		else if (g % 13 == 6) s2[i] = '6';
    		else if (g % 13 == 7) s2[i] = '7';
    		else if (g % 13 == 8) s2[i] = '8';
    		else if (g % 13 == 9) s2[i] = '9';
    		else if (g % 13 == 10) s2[i] = 'A';
    		else if (g % 13 == 11) s2[i] = 'B';
    		else if (g % 13 == 12) s2[i] = 'C';
    		i++; g = g / 13;
    	}
    	if (g % 13 == 0) s2[i] = '0';
    	else if (g % 13 == 1) s2[i] = '1';
    	else if (g % 13 == 2) s2[i] = '2';
    	else if (g % 13 == 3) s2[i] = '3';
    	else if (g % 13 == 4) s2[i] = '4';
    	else if (g % 13 == 5) s2[i] = '5';
    	else if (g % 13 == 6) s2[i] = '6';
    	else if (g % 13 == 7) s2[i] = '7';
    	else if (g % 13 == 8) s2[i] = '8';
    	else if (g % 13 == 9) s2[i] = '9';
    	else if (g % 13 == 10) s2[i] = 'A';
    	else if (g % 13 == 11) s2[i] = 'B';
    	else if (g % 13 == 12) s2[i] = 'C';
    
    	i = 0;
    	while (i<=1) {
    		if (b % 13 == 0) s3[i] = '0';
    		else if (b % 13 == 1) s3[i] = '1';
    		else if (b % 13 == 2) s3[i] = '2';
    		else if (b % 13 == 3) s3[i] = '3';
    		else if (b % 13 == 4) s3[i] = '4';
    		else if (b % 13 == 5) s3[i] = '5';
    		else if (b % 13 == 6) s3[i] = '6';
    		else if (b % 13 == 7) s3[i] = '7';
    		else if (b % 13 == 8) s3[i] = '8';
    		else if (b % 13 == 9) s3[i] = '9';
    		else if (b % 13 == 10) s3[i] = 'A';
    		else if (b % 13 == 11) s3[i] = 'B';
    		else if (b % 13 == 12) s3[i] = 'C';
    		i++; b = b / 13;
    	}
    	if (b % 13 == 0) s3[i] = '0';
    	else if (b % 13 == 1) s3[i] = '1';
    	else if (b % 13 == 2) s3[i] = '2';
    	else if (b % 13 == 3) s3[i] = '3';
    	else if (b % 13 == 4) s3[i] = '4';
    	else if (b % 13 == 5) s3[i] = '5';
    	else if (b % 13 == 6) s3[i] = '6';
    	else if (b % 13 == 7) s3[i] = '7';
    	else if (b % 13 == 8) s3[i] = '8';
    	else if (b % 13 == 9) s3[i] = '9';
    	else if (b % 13 == 10) s3[i] = 'A';
    	else if (b % 13 == 11) s3[i] = 'B';
    	else if (b % 13 == 12) s3[i] = 'C';
    	printf("#");
    	for (i = 1; i >= 0; i--) {
    		printf("%c", s1[i]);
    	}
    	for (i =  1; i >= 0; i--) {
    		printf("%c", s2[i]);
    	}
    	for (i =  1; i >= 0; i--) {
    		printf("%c", s3[i]);
    	}
    
    }

#### 注：代码可进行精简