---
title: PAT每日一题|1031 Hello World for U
url: 139.html
id: 139
categories:
  - PAT
date: 2018-10-02 20:41:27
tags:
---

Given any string of N (≥5) characters, you are asked to form the characters into the shape of `U`. For example, `helloworld` can be printed as:

    h  d
    e  l
    l  r
    lowo
    

That is, the characters must be printed in the original order, starting top-down from the left vertical line with n​1​​ characters, then left to right along the bottom line with n​2​​ characters, and finally bottom-up along the vertical line with n​3​​ characters. And more, we would like `U` to be as squared as possible -- that is, it must be satisfied that n​1​​=n​3​​=max { k | k≤n​2​​ for all 3≤n​2​​≤N } with n​1​​+n​2​​+n​3​​−2=N.

### Input Specification:

Each input file contains one test case. Each case contains one string with no less than 5 and no more than 80 characters in a line. The string contains no white space.

### Output Specification:

For each test case, print the input string in the shape of U as specified in the description.

### Sample Input:

    helloworld!
    

### Sample Output:

    h   !
    e   d
    l   l
    lowor
    

    #include <stdio.h>
    #include <string.h>
    int main() {
    	char s[100];
    	int len, i, a,b;
    	int n1, n2, n3;
    	scanf("%s", s);
    	len = strlen(s);
    	if ((len + 2) % 3 == 0) {
    		n1 = n2 = n3 = (len + 2) / 3;
    	}
    	else if (len % 3 == 0) {
    		n1 = n3 = len / 3;
    		n2 = n1 + 2;
    	}
    	else {
    		n1 = n3 = (len + 1) / 3;
    		n2 = n1 + 1;
    	}
    	
    	for (i = 0; i < n1; i++) {
    		printf("%c",s[i]);
    		a = b = 0;
    		if (i != n1-1) {
    			while (a <n2-2) {
    				printf(" ");
    				a++;
    			}
    		}
    		else {
    			while (b <n2-2) {
    				printf("%c", s[i + b + 1]);
    				b++;
    			}
    		}
    		printf("%c\n", s[len - 1 - i]);
    
    	}
    	
    }