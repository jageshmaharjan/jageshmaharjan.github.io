---
title: "Dynamic Programming::Rod Cutting Problem"
date: 2018-08-19
tags: [Data Structure & Algorithms, Dynamic Programming, Optimization]
header:
   image: "/images/deepspeech/deepspeech.jpg"
excerpt: "Data Structure & Algorithms, Dynamic Programming, Optimization"
---

[Rod Cutting problem](http://users.csc.calpoly.edu/~dekhtyar/349-Spring2010/lectures/lec09.349.pdf) is one of the most 
popular problem in [Dynamic Programming](https://en.wikipedia.org/wiki/Dynamic_programming). 

The problem statement is illustrated in the link above and explanation is well described in [![YouTube Video](/images/rodcutting/RodCutting.png)](https://www.youtube.com/watch?v=ElFrskby_7M&t)

And, based on the illustration of the problem statement, I implemented on the rod-cutting problem in java.
**Before** diving into the implementation, please watch the video and try to solve by yourself.


```
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

public class RodCuttingProblem {

    public static void main(String[] args) {
        int[][] lengthPriceOfRod = new int[][]{
                {1,2,3,4,5,6,7,8},{1,5,8,9,10,17,17,20}};

        int n = 8;
        int[] cache = maxProfit(lengthPriceOfRod, n, new int[lengthPriceOfRod.length]);
        System.out.println(Arrays.toString(cache));
        Arrays.sort(cache);
        System.out.println(cache[cache.length-1]);
    }

    private static int[] maxProfit(int[][] lengthPriceOfRod, int n, int[] memo) {
        int[] cache = new int[lengthPriceOfRod[0].length];
        cache[0] = lengthPriceOfRod[1][0];
        for (int i=1; i<cache.length; i++){
            cache[i] = getMax(cache, lengthPriceOfRod, i);
        }
        return cache;
    }

    private static int getMax(int[] cache, int[][] lengthPriceOfRod, int i) {
        int max = lengthPriceOfRod[1][i];
        for (int j=0; j<i; j++){
            int val = lengthPriceOfRod[1][j] + cache[i-j-1];
            max = val > max ? val : max;
        }
        return max;
    }
}
```

Couldn't share the Github link due to NDA with partners associated with [LeetCode](https://leetcode.com/) 
and [HackerRank](https://www.hackerrank.com/).
