---
title: Knuth–Morris–Pratt (KMP) algorithm
date: 2020-03-02 17:24:32
categories:
- LeetCode
tags: 
- String
- algorithm
- KMP
- time complexity 
---

Learnt from LeetCode question [Linked List in Binary Tree](<https://leetcode.com/problems/linked-list-in-binary-tree/>). A faster way to check string patten against a given text. 

First round, iterate through **pattern** to generate a new array for later use. Intuition behind this is to find same suffix and prefix so at the second round we don't go back in **given text** for duplicate substring.

![credit to [Tushar Roy - Coding Made Simple](https://www.youtube.com/channel/UCZLJf_R2sWyUtXSKiKlyvAw)](<https://tva1.sinaimg.cn/large/00831rSTgy1gcgjhclzlkj30wm0flq96.jpg>)



Second round, we compare **given text** against **pattern** with the help of the generated array.

![credit to [Tushar Roy - Coding Made Simple](https://www.youtube.com/channel/UCZLJf_R2sWyUtXSKiKlyvAw)](<https://tva1.sinaimg.cn/large/00831rSTgy1gcgjy8by4nj30zv0k2dna.jpg>)



The total time complexity will be O(m+n), m being the length of **given text** and n being the length of **pattern**, which is a large improvement compared with the brute force way (O(m*n)).

---

Other links for reference:

[wiki](<https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm>)

[Solution_Factory](<https://www.solutionfactory.in/posts/Knuth-Morris-Pratt-Substring-Search-Algorithm-with-Java-Example>)