---
title: "Dynamic Programming::Change Making Problem"
date: 2018-08-11
tags: [Data Structure & Algorithms, Dynamic Programming, Optimization]
header:
   image: "/images/deepspeech/shenzhen.jpg"
excerpt: "Data Structure & Algorithms, Dynamic Programming, Optimization"
---

[Change Making DP problem](https://en.wikipedia.org/wiki/Change-making_problem) is a related to making changes with the 
coins. This problem can be categorised in  several form of [Dynamic Programming](https://en.wikipedia.org/wiki/Dynamic_programming)
based on the types of coin we can change. The coin system is country specific problem. Most of the countries have a 
coin system as of [1,5,10,25,50], while some of the countries have the coin system of [1,2,5,10,20,50].
To this end, I'll follow the US standard of coin system, and depending on the coin system the implementation vary greatly.
And, US based coin system is easier to solve as compared to other system.  

For more details on on formal definition of change making Problem please
 refer to the wikipedia link on the top. ![change making problem](/images/changemaking/changemaking.png)

And, based on the illustration of the problem statement, I've implemented the knapsack problem in java.
**Before** diving into the implementation, please read the problem definition to solve by yourself.


```
import java.util.ArrayList;
import java.util.Arrays;

public class MinCoinChange {

    public static void main(String[] args) {
        int[] coins = new int[]{1,5,10,25};
        int money = 32;
        ArrayList<Integer> cache = new ArrayList<>();
        System.out.println(change(coins, money, cache));
    }

    private static ArrayList change(int[] coins, int money, ArrayList<Integer> cache) {
        if (money == 0)
            return cache;
        while (money > 0){
            for (int i=coins.length-1; i>=0; i--){
                if (money >= coins[i]){
                    money = money- coins[i];
                    cache.add(coins[i]);
                    return change(coins, money, cache);
                }
            }
        }
        return cache;
    }
}
```

Couldn't share the Github link due to NDA with partners associated with [LeetCode](https://leetcode.com/) 
and [HackerRank](https://www.hackerrank.com/).
