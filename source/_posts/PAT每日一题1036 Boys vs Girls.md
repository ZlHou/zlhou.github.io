---
title: PAT每日一题|1036 Boys vs Girls
url: 157.html
id: 157
categories:
  - PAT
date: 2018-10-10 18:36:20
tags:
---

This time you are asked to tell the difference between the lowest grade of all the male students and the highest grade of all the female students.

### Input Specification:

Each input file contains one test case. Each case contains a positive integer N, followed by N lines of student information. Each line contains a student's `name`, `gender`, `ID` and `grade`, separated by a space, where `name` and `ID` are strings of no more than 10 characters with no space, `gender` is either `F` (female) or `M` (male), and `grade` is an integer between 0 and 100. It is guaranteed that all the grades are distinct.

### Output Specification:

For each test case, output in 3 lines. The first line gives the name and ID of the female student with the highest grade, and the second line gives that of the male student with the lowest grade. The third line gives the difference grade​F​​−grade​M​​. If one such kind of student is missing, output `Absent` in the corresponding line, and output `NA` in the third line instead.

### Sample Input 1:

    3
    Joe M Math990112 89
    Mike M CS991301 100
    Mary F EE990830 95


### Sample Output 1:

    Mary EE990830
    Joe Math990112
    6


### Sample Input 2:

    1
    Jean M AA980920 60


### Sample Output 2:

    Absent
    Jean AA980920
    NA


​    
    #include <stdio.h>
    #include <math.h>
    #include <string.h>
    struct stu
    {
    	char name[100];
    	char gender;
    	char id[100];
    	int grade;
    }stu[10000],f,m;
    
    int main() {
    	int n;
    	int i;
    	int result=0;
    	int lenf, lenm;
    	f.grade = -1;
    	m.grade = 101;
    	scanf("%d", &n);
    	if (n != 0) {
    
    		for (i = 0; i < n; i++) {
    			scanf("%s %c %s %d", &stu[i].name, &stu[i].gender, &stu[i].id, &stu[i].grade);
    			if (stu[i].gender == 'M') {
    
    				if (m.grade > stu[i].grade) {
    					m = stu[i];
    				}
    			}
    			else {
    				if (f.grade < stu[i].grade) {
    					f = stu[i];
    				}
    			}
    		}
    		lenf = strlen(f.id);
    		lenm = strlen(m.id);
    		if (lenf != 0 & lenm != 0) {
    			result = f.grade - m.grade;
    			printf("%s %s\n", f.name, f.id);
    			printf("%s %s\n", m.name, m.id);
    			printf("%d", result);
    		}
    		else if (lenf == 0 & lenm != 0) {
    			printf("Absent\n%s %s\nNA", m.name, m.id);
    		}
    		else if (lenf != 0 & lenm == 0) {
    			printf("%s %s\nAbsent\nNA", f.name, f.id);
    		}
    		
    	}
    	else {
    		printf("Absent\nAbsent\nNA");
    	}
    	
    }