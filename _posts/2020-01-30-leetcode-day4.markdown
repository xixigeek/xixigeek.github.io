---
layout: post
title: LeetCode Day3
date: 2020-01-30 14:07:00 -0500
description: LeetCode 38,53 # Add post description (optional)
tags: [LeetCode, Software] # add tag
---

### LeetCode 38 Count and Say

https://leetcode.com/problems/count-and-say/

Firstly, I have to say the question is hard to understand.We can just use the hashmap to solve it, but I use two index while.
{% highlight java %}
public String countAndSay(int n) {
     String result = "11";
     if (n == 1) {
         return "1";
     } else if (n == 2) {
         return result;
     }
     while (n > 2) {
         n--;
         //转换为char数组处理字符
         char[] array = result.toCharArray();
         result = "";
         int j = 0;
         for (int i = 1; i < array.length; i++) {
             //双指针判断慢指针和快指针元素不同时，计数并”读出来“
             if (array[i] != array[j]) {
                 result += (i - j) + "" + array[i - 1];
                 j = i;
             }
             //对于末尾的元素特特殊处理
             if (i == array.length - 1 && array[i] == array[j]) {
                 result += (i - j + 1) + "" + array[i];
             }
         }
     }
     return result;
}
{% endhighlight  %}

I try another methor by using recursion.
{% highlight java %}
public static String countAndSay(int n) {
    if (n == 1) {
        return "1";
    }
    String newString = countAndSay(n - 1);
    StringBuilder builder = new StringBuilder();
    char pre = newString.charAt(0);
    int count = 0;
    for (int i = 0; i < newString.length(); i++) {
        if (newString.charAt(i) == pre) {
            count++;
        } else {
            builder.append(count).append(pre);
            pre = newString.charAt(i);
            count = 1;
        }

        if (i == newString.length() - 1) {
            builder.append(count).append(pre);
        }
    }
    return builder.toString();
}
{% endhighlight  %}

### LeetCode 53 Maximum Subarray

https://leetcode.com/problems/maximum-subarray/

We hava lots of solutions:
{% highlight java %}
public int maxSubArray(int[] nums) {
    int maxSum = nums[0], currentSum = nums[0];

    for (int i = 1; i < nums.length; i++) {
        currentSum = Math.max(nums[i], currentSum + nums[i]);
        maxSum = Math.max(maxSum, currentSum);
    }
    return maxSum;
}
{% endhighlight  %}

{% highlight java %}
private static int maxSub(int[] origin) {
    int maxSum = origin[0];

    for (int i = 1; i < origin.length; i++) {
        if (origin[i - 1] > 0) {
            origin[i] += origin[i - 1];
        }
        maxSum = Math.max(maxSum, origin[i]);
    }
    return maxSum;
}
{% endhighlight  %}
