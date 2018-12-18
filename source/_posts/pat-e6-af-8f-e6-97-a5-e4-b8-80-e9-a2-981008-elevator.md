---
title: PAT每日一题|1008 Elevator
url: 135.html
id: 135
categories:
  - PAT
date: 2018-10-02 09:59:23
tags:
---

The highest building in our city has only one elevator. A request list is made up with N positive numbers. The numbers denote at which floors the elevator will stop, in specified order. It costs 6 seconds to move the elevator up one floor, and 4 seconds to move down one floor. The elevator will stay for 5 seconds at each stop.

For a given request list, you are to compute the total time spent to fulfill the requests on the list. The elevator is on the 0th floor at the beginning and does not have to return to the ground floor when the requests are fulfilled.

### Input Specification:

Each input file contains one test case. Each case contains a positive integer N, followed by N positive numbers. All the numbers in the input are less than 100.

### Output Specification:

For each test case, print the total time on a single line.

### Sample Input:

    3 2 3 1
    

### Sample Output:

    41
    

    #include <stdio.h>
    int main() {
    	int n,time=0;
    	int i,now=0;
    	int floor[100];
    	scanf("%d", &n);
    	for (i = 0; i < n; i++) {
    		scanf("%d", &floor[i]);
    	}
    	time = time + n * 5;
    	for (i = 0; i < n; i++) {
    		if (floor[i] - now > 0) {
    			time = time + (floor[i] - now) * 6;
    		}
    		else if (floor[i] - now < 0) {
    			time = time + (now - floor[i]) * 4;
    		}
    		now = floor[i];
    	}
    	printf("%d", time);
    }