---
layout: post
title: LeetCode Day2
date: 2020-01-23 16:00:00 -0500
description: LeetCode 21,82,83 # Add post description (optional)
tags: [LeetCode, Software] # add tag
---

### LeetCode 21 Merge Two Sorted Lists

https://leetcode.com/problems/merge-two-sorted-lists

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
