###leedcode142 - Linked List Cycle II

> Given a linked list, return the node where the cycle begins. If there is no cycle, return null. </br>
Note: Do not modify the linked list. </br>
Follow up:</br>
Can you solve it without using extra space?

- 方法一: </br>

> 第一种方法,和找出一个链表是否有环是一个思想,遍历链表,查找这个节点是否在集合中,如果不在,加入集合.如果在就是存在环,而且这个节点就是环的第一个节点.


```
	  ListNode *detectCycle(ListNode *head) {
        
        std::set<ListNode *> save_data;
    while (head)
    {

        if(save_data.find(head) != save_data.end())
        {
            return head;
        }
        save_data.insert(head);
        head = head->next;

    }

    return NULL;
        
```

- 方法2: </br>

> 第二种方法(这种方法臣妾确实想不到,网上看了下原理),就是使用快慢指针,快指针一次走两个,慢指针一次走一个.




如下: 3 4 5 6 是一个环 6 指向3

```
1 -> 2 -> 3 -> 4 -> 5 -> 6 --->
          |                    |
           <-------------------

```
他们走的路线就是
慢指针A:  2 3 4 5 6 </br>
快指针B:  3 5 3 5 3

它们在5这个节点相遇
快指针走的路程 是 慢指针的2倍,(ps : 时间一样,速度是二倍)

#####我们设置几段 ( '[' 和 ']' 标示 包含该节点, '(' 和 ')' 不包含该节点)
- 第一段  a (从第一个节点 -> 环的第一个节点) (第二个节点 到 环的第一个节点的前一个)
- 第二段  b [环的第一个节点 相遇那个点]
- 第三段  c (环的第一个节点 相遇那个点)

> A 走的距离 * 2 = B 走的距离
> (a + b) * 2 = a + b + c + b  =>  a = c  </br>
>  即: 从第一个节点(first_point)到环的第一个节点,和相遇节点(meet_point)到环的第一个节点距离一样,遍历这两个指针(first_point, meet_point),当相等的时候,就是环的第一个节点.

 

```
 ListNode *detectCycle(ListNode *head) {
        
    ListNode *fast_head = head;

    ListNode *meet = NULL;
        
    ListNode *result = head;    
    
    while (fast_head && head)
    {
        head = head->next;
        fast_head = fast_head ->next;
        if(fast_head)
        {
            fast_head = fast_head ->next;
        }
        else
        {
            return NULL;
        }

        if(fast_head == head)
        {
            meet = head;
            break;
        }

    }
    
    while(meet)
    {
       if(result == meet)
       {
           return meet;
       }
        result =  result->next;
        meet = meet->next;
    }
    return NULL;
        
        
    }
         
```
