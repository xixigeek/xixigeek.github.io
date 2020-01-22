---
layout: post
title: LeetCode Day1
date: 2020-01-17 13:58:35 -0500
description: Now I'm trying to find a job in the USA, although I have already worked for many years my friends suggest to me that I should do some LeetCode.So Let's do it! LeetCode 1,7,13 # Add post description (optional)
tags: [LeetCode, Software] # add tag
---

Now I'm trying to find a job in the USA, although I have already worked for many years my friends suggest to me that I should do some LeetCode.So Let's do it!

### LeetCode 1 Two Sum    

https://leetcode.com/problems/two-sum/

{% highlight java %}
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap();
    for (int i = 0; i < nums.length; i++) {
        if (map.containsKey(target - nums[i])) {
            return new int[]{map.get(target - nums[i]), i};
        } else {
            map.put(nums[i], i);
        }
    }
    throw new IllegalArgumentException("Not match nums");
}
{% endhighlight  %}

Never try this below, you will be an error if your input is "[3,2,4] 6", because 6 = 3 + 3, you should just use one number only once.

{% highlight java %}
//Wrong
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap();
        for (int i = 0; i < nums.length; i++) {
            map.put(nums[i], i);
        }

        for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(target - nums[i])) {
                return new int[]{map.get(target - nums[i]), i};
            }
        }
        return new int[]{};
    }
}
{% endhighlight  %}

### LeetCode 7 Reverse Integer    
https://leetcode.com/problems/reverse-integer/
{% highlight java %}
public int reverse(int x) {
    long result = 0;

    while (x != 0) {
        result = result * 10 + x % 10;
        x /= 10;
    }
    if (result > Integer.MAX_VALUE || result < Integer.MIN_VALUE) {
        return 0;
    } else {
        return (int) (result);
    }
}
{% endhighlight  %}

Another Solution is using the string reverse:
{% highlight java %}
//Version String
 public int reverse(int x) {
        String a = Integer.toString(x);
        int b = 1;

        if (a.charAt(0) == '-') {
            a = a.substring(1);
            b = -1;
        }

        char[] chars = a.toCharArray();
        char[] results = new char[chars.length];

        for (int i = chars.length - 1; i >= 0; i--) {
            results[chars.length - 1 - i] = chars[i];
        }
        long longNum = Long.valueOf(new String(results));
        if (longNum > Integer.MAX_VALUE || longNum < Integer.MIN_VALUE) {
            return 0;
        }
        return (int) (b * longNum);
  }
{% endhighlight  %}

### LeetCode 13 Roman to Integer
https://leetcode.com/problems/roman-to-integer/

The simplest solution is just listing all the roman number in a HashMap.

{% highlight java %}

public int romanToInt(String s) {
       Map<String, Integer> map = new HashMap<>();
       map.put("I", 1);
       map.put("IV", 4);
       map.put("V", 5);
       map.put("IX", 9);
       map.put("X", 10);
       map.put("XL", 40);
       map.put("L", 50);
       map.put("XC", 90);
       map.put("C", 100);
       map.put("CD", 400);
       map.put("D", 500);
       map.put("CM", 900);
       map.put("M", 1000);

       int result = 0;
       for (int i = 0; i < s.length(); i++) {
           if (i + 2 <= s.length() && map.containsKey(s.substring(i, i + 2))) {
               result += map.get(s.substring(i, i + 2));
               i++;
           } else {
               result += map.get(s.substring(i, i + 1));
           }
       }
       return result;
}
   {% endhighlight  %}
