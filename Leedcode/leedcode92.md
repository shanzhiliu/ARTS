###leedcode92 - Reverse Linked List II
```
 ListNode* reverseBetween(ListNode* head, int m, int n) {
        
        
        
    ListNode *result = head;
    ListNode *pre_head = head;
    int changeLen = (n-m+1);

    for (int i = 0 ; i< (m -1) ; i++)
    {
        pre_head = head;
        head = head->next;
    }

    ListNode *last_head =  head;
    ListNode *new_head = NULL;
    ListNode *next = NULL;


    for (int j = 0; j < changeLen; ++j) {

        next = head->next;
        head->next = new_head;
        new_head = head;
        head = next;
    }

    last_head->next = next;

    if(m != 1)
    {
        pre_head->next = new_head;
    }

    else
    {
        result = new_head;
    }

    return result;
        
    }
    
```
