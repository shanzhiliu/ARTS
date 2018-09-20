###leedcode141 - Linked List Cycle
- 方法一: 一个指针一次移动2个位置,一个指针一个位置,如果有环,会相遇的.

```
  
  bool hasCycle(ListNode *head) {

    if(head == NULL)
    {
        return false;
    }
        
    ListNode *fast_head = head -> next;

    while (fast_head && head)
    {

        if(fast_head == head)
        {
            return true;
        }
        head = head->next;
        fast_head = fast_head ->next;
        if(fast_head)
        {
            fast_head = fast_head ->next;
        }
    }

    return false;
}

     
```

- 方法二 : 遍历时候存储每个节点,如果有环,会在set中找到

```
    std::set<ListNode *> save_data;
    while (head)
    {
        
        if(save_data.find(head) != save_data.end())
        {
            return true;
        }
        save_data.insert(head);
        head = head->next;

    }

    return false;
    
    ```
