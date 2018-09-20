###leedcode160 
> 题目链接: [跳转](https://leetcode.com/problems/intersection-of-two-linked-lists/description/)

- 方法一: set 先存储一个链表所有节点,遍历第二个链表,如果查询到 返回这个节点就是相遇的节点.

```
 ListNode * LeedCode160::getIntersectionNode(ListNode *headA, ListNode *headB) {

   std::set<ListNode *> save_set;
    while (headA)
    {
        save_set.insert(headA);
        headA = headA->next;
    }

    while(headB)
    {
        if(save_set.find(headB) != save_set.end())
        {
            return headB;
        }
        headB = headB->next;
    }
    return NULL;
}
    
```

- 方法二 链表对其后 遍历查找,先查询A链表的个数 N, 在查询B链表的个数 M, 让链表个数多的先移动 sbs(N-M)个节点,在同时移动A,B链表,找到相遇节点,如果没有返回NULL. 

```
//获取链表有多少个元素
int getCount(ListNode *head) {
    int count = 0;
    while (head)
    {
        count ++;
        head = head->next;
    }
    return count;
}

//将数据多的元素 先空转 (n-m)个
ListNode *changeHeader(ListNode *headA , int changeLen)
{
    for (int i = 0; i < changeLen ; ++i) {
        headA = headA->next;
    }
   return headA;
}

ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {

    int headA_count = getCount(headA);
    int headB_count = getCount(headB);

    if(headA_count > headB_count)
    {
         headA = changeHeader(headA,(headA_count - headB_count));
    }
    else
    {
        headB = changeHeader(headB,(headB_count - headA_count));
    }

    while (headA && headB)
    {

        if(headA == headB)
        {
            return headA;
        }
        headB = headB->next;
        headA = headA->next;
    }

    return NULL;
}
    
```
