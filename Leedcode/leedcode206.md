###leedcode206-Reverse Linked List

#### 题目链接:[click](https://leetcode.com/problems/reverse-linked-list/description/)

####实现方法
-  单项链表的反转比较简单,核心的逻辑代码只有4行
    - 保存 next 指针
    - 头指针指向新的节点
    - 新的节点指向头指针
    - 头指针指向next


```
    ListNode* reverseList(ListNode* head) {
        
        ListNode* next = NULL;
        ListNode* newHead = NULL;
        
        while(head)
        {
            next = head->next;
            head->next = newHead;
            newHead = head;
            head  = next;
        }
        
        return  newHead;
            
    }
    
```
