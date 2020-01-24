---
layout: post
title: LeetCode Day3
date: 2020-01-23 16:00:00 -0500
description: LeetCode 21,28 # Add post description (optional)
tags: [LeetCode, Software] # add tag
---

### LeetCode 21 Merge Two Sorted Lists

https://leetcode.com/problems/merge-two-sorted-lists

When we talk about the linked list we should think in recursion first.
So we have three things about recursion:
First is when we stop recursion, in this term when the l1 or l2 is null, it is done.
Second is return value in every recursion, we returned the sorted linked list every time.
Last is the procession in every recursion, we compare the l1.val and l2.vale, if l1.val smaller we put the next recursion's result behind the l1.next. Otherwise, we put that behind the l2.next.
{% highlight java %}
public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    if (l1 == null) {
        return l2;
    }
    if (l2 == null) {
        return l1;
    }

    if (l2.val > l1.val) {
        l1.next = mergeTwoLists(l1.next, l2);
        return l1;
    } else {
        l2.next = mergeTwoLists(l1, l2.next);
        return l2;
    }
}
{% endhighlight  %}

### LeetCode 26 Remove Duplicates from Sorted Array

https://leetcode.com/problems/remove-duplicates-from-sorted-array/

{% highlight java %}
public int removeDuplicates(int[] nums) {
    if (nums.length == 0) {
        return 0;
    }
    int targetIndex = 0;
    for (int i = 1; i < nums.length; i++) {
        if (nums[targetIndex] != nums[i]) {
            targetIndex++;
            nums[targetIndex] = nums[i];
        }
    }
    return targetIndex + 1;
}
{% endhighlight  %}

### LeetCode 28 Implement strStr()
https://leetcode.com/problems/implement-strstr/

{% highlight java %}
public int strStr(String haystack, String needle) {
    return haystack.indexOf(needle);
}
{% endhighlight  %}

Yeah, it's just a joke, we should use two pointers here.
{% highlight java %}
public int strStr(String haystack, String needle) {
    int targetIndex = 0;
    char[] haystackChars = haystack.toCharArray();
    char[] needleChars = needle.toCharArray();
    for (int i = 0; i < haystackChars.length - needleChars.length + 1; i++) {
        int j = 0;
        for (; j < needleChars.length; j++) {
            if (haystackChars[i + j] != needleChars[j]) {
                break;
            }
        }
        if (j == needleChars.length) {
            return i;
        }
    }
    return -1;
}
{% endhighlight  %}
