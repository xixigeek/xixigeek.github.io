---
layout: post
title: LeetCode Day2
date: 2020-01-20 13:58:35 -0500
description: LeetCode 14，20 # Add post description (optional)
tags: [LeetCode, Software] # add tag
---

Now I'm trying to find a job in the USA, although I have already worked for many years my friends suggest to me that I should do some LeetCode.So Let's do it!

### LeetCode 14 Longest Common Prefix

https://leetcode.com/problems/longest-common-prefix/

{% highlight java %}
public String longestCommonPrefix(String[] strs) {
    if (strs == null || strs.length == 0){
        return "";
    }
    String element = strs[0];
    int j = element.length();
    for (int i = 0;i < strs.length;i++){
        while (strs[i].indexOf(element.substring(0,j)) != 0){
            j--;
            if(j < 0){
                return "";
            }
        }
    }
    return element.substring(0,j);
}
{% endhighlight  %}

It means we can compare the first two elements and find the longest prefix, then we use it to compare next.

{% highlight java %}
//concice
public String longestCommonPrefix(String[] strs) {
    if (strs == null || strs.length == 0) {
        return "";
    }
    String element = strs[0];
    for (int i = 0; i < strs.length; i++) {
        while (strs[i].indexOf(element) != 0) {
            element = element.substring(0, element.length() - 1);
            if (element.isEmpty()) {
                return "";
            }
        }
    }
    return element;
}
{% endhighlight  %}

### LeetCode 20 Valid Parentheses
https://leetcode.com/problems/valid-parentheses/

One solution is like  this, quite simple and smart
{% highlight java %}
public boolean isValid(String s) {
    while (s.contains("[]") || s.contains("{}") || s.contains("()")){
        s = s.replace("[]","");
        s = s.replace("{}","");
        s = s.replace("()","");
    }
    return s.equals("");
}
{% endhighlight  %}

Another Solution which use stack may more efficiently
{% highlight java %}

Stack<Character> stack = new Stack<>();
     char[] chars = s.toCharArray();

     Map<Character, Character> map = new HashMap();
     map.put(')', '(');
     map.put('}', '{');
     map.put(']', '[');

     for (int i = 0; i < chars.length; i++) {
         if (map.containsKey(chars[i])) {
             char topElement = stack.isEmpty() ? '#' : stack.pop();
             if (topElement != map.get(chars[i])) {
                 return false;
             }
         } else {
             stack.push(chars[i]);
         }
     }

     return stack.empty();
{% endhighlight  %}
