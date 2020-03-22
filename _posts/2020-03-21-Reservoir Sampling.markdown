---
title: Reservoir Sampling algorithm
date: 2020-03-21 22:17:32
categories:
- LeetCode
tags: 
- probability
- algorithm
---

Learnt from LeetCode question [Linked List Random Node](<https://leetcode.com/problems/linked-list-random-node/>). 

##### Scenario:

 We want to make sure each element from a group is picked out with same probability, even when dealing with a group of elements with dynamic-increasing size. This is where Reservoir Sampling algorithm come on the scene.



##### Algorithm Description:

**Problem:**

Choose `k` entries from `n` numbers. Make sure each number is selected with the probability of `k/n`.

**Basic Idea:**

* Choose `1, 2, 3, ..., k` first and put them into the reservoir.
* For `k+1`, pick it with a probability of `k/(k+1)`, and randomly replace a number in the reservoir.
* For `k+i`, pick it with a probability of `k/(k+i)`, and randomly replace a number in the reservoir.
* Repeat until `k+i` reaches `n`

**Explanation:**

* Choose `3` numbers from `[111, 222, 333, 444]`. Make sure each number is selected with a probability of `3/4`

* First, choose `[111, 222, 333]` as the initial reservior

* Then choose `444` with a probability of `3/4`

* For `111`, it stays with a probability of

  P(444 is not selected)` + `P(444 is selected but it replaces 222 or 333)

  = `1/4` + `3/4`*`2/3`

  = `3/4`

* The same case with `222` and `333`

* Now all the numbers have the probability of `3/4` to be picked



##### As to This Problem:

**Description:**

>Given a singly linked list, return a random node's value from the linked list. Each node must have the **same probability** of being chosen.
>
>**Follow up:**
>What if the linked list is extremely large and its length is unknown to you? Could you solve this efficiently without using extra space?
>
>**Example:**
>
>```java
>// Init a singly linked list [1,2,3].
>ListNode head = new ListNode(1);
>head.next = new ListNode(2);
>head.next.next = new ListNode(3);
>Solution solution = new Solution(head);
>
>// getRandom() should return either 1, 2, or 3 randomly. Each element should have equal probability of returning.
>solution.getRandom();
>```

The k here is 1, which will be a special case of Reservoir Sampling algorithm.

**Code:**

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {

    /** @param head The linked list's head.
        Note that the head is guaranteed to be not null, so it contains at least one node. */
    ListNode h;
    Random random;
    public Solution(ListNode head) {
        h = head;
        random = new Random();
    }
    
    /** Returns a random node's value. */
    public int getRandom() {
        ListNode cur = h;
        int res = cur.val;
        int cnt = 1;
        
        while(cur.next!=null){
            cur = cur.next;
            if(random.nextInt(cnt+1)==cnt) res = cur.val;
            cnt++;
        }
        return res;
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(head);
 * int param_1 = obj.getRandom();
 */
```



---

Other links for reference:

[wiki](<https://en.wikipedia.org/wiki/Reservoir_sampling>)

[Youtube: Reservoir Sampling](<<https://www.youtube.com/watch?v=A1iwzSew5QY>>)

[Brief explanation for Reservoir Sampling](<https://leetcode.com/problems/linked-list-random-node/discuss/85659/Brief-explanation-for-Reservoir-Sampling>)

