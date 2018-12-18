---
title: PAT每日一题|1002 A+B for Polynomials
url: 128.html
id: 128
categories:
  - PAT
date: 2018-09-30 10:12:19
tags:
---

This time, you are supposed to find A+B where A and B are two polynomials.

### Input Specification:

Each input file contains one test case. Each case occupies 2 lines, and each line contains the information of a polynomial:

K N​1​​ a​N​1​​​​ N​2​​ a​N​2​​​​ ... N​K​​ a​N​K​​​​

where K is the number of nonzero terms in the polynomial, N​i​​ and a​N​i​​​​ (i=1,2,⋯,K) are the exponents and coefficients, respectively. It is given that 1≤K≤10，0≤N​K​​<⋯<N​2​​<N​1​​≤1000.

### Output Specification:

For each test case you should output the sum of A and B in one line, with the same format as the input. Notice that there must be NO extra space at the end of each line. Please be accurate to 1 decimal place.

### Sample Input:

    2 1 2.4 0 3.2
    2 2 1.5 1 0.5
    

### Sample Output:

    3 2 1.5 1 2.9 0 3.2
    

#### 正确：

    #include <stdio.h>
    int main() {
    	float coe[1001] = { 0.0 };
    	int a, b, i, m,num=0;
    	float n;
    	scanf("%d", &a);
    	for (i = 0; i < a; i++) {
    		scanf("%d%f", &m,&n);
    		coe[m] = coe[m] + n;
    	}
    	scanf("%d", &b);
    	for (i = 0; i < b; i++) {
    		scanf("%d%f", &m,&n);
    		coe[m] = coe[m] + n;
    	}
    	for (i = 1000; i >= 0; i--) {
    		if (coe[i] != 0.0) {
    			num++;
    		}
    	}
    	printf("%d", num);
    	for (i = 1000; i >= 0; i--) {
    		if (coe[i] != 0.0) {
    			printf(" %d %.1f", i, coe[i]);
    		}
    	}
    }

#### 错误：

    #include <stdio.h>
    int main() {
    	float coe[1001] = { 0.0 };
    	int a, b, i, m,num=0;
    	float n;
    	scanf("%d", &a);
    	for (i = 0; i < a; i++) {
    		scanf("%d%f", &m,&n);
    		if (coe[m] == 0.0) num++;
    		coe[m] = coe[m] + n;
    	}
    	scanf("%d", &b);
    	for (i = 0; i < b; i++) {
    		scanf("%d%f", &m,&n);
    		if (coe[m] == 0.0) num++;
    		coe[m] = coe[m] + n;
    	}
    	printf("%d", num);
    	for (i = 1000; i >= 0; i--) {
    		if (coe[i] != 0.0) {
    			printf(" %d %.1f", i, coe[i]);
    		}
    	}
    }