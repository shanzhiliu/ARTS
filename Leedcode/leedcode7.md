###leedcode7 - Reverse Integer
#####题目:
> Given a 32-bit signed integer, reverse digits of an integer.

> Example 1:

> Input: 123
> Output:  321
> Example 2:

> Input: -123
> Output: -321
> Example 3:

> Input: 120
>Output: 21
> Note:
> Assume we are dealing with an environment which could only hold integers within the 32-bit signed integer range. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.


- 实现思路是先将每一位数字,放到链表中,在遍历链表从第一个值不为零的节点,计算出最后的值,要注意计算的值用long long 保存,然后可判断是否超出了整数的范围.

```
     
struct  Node {
    int val;
    Node *next;
};

int getCount(Node *head) {
    int count = 0;
    while (head)
    {
        count ++;
        head = head->next;
    }
    return count;
}


int reverse(int x) {


    Node *first = new Node;
    Node *head = first;
    head->next = NULL;
    int flag = 1;

    if(x < 0)
    {
        flag = -1;
    }
    x = abs(x);
    int y;
    while (x)
    {
        y = x % 10;
        x = x / 10;
        Node *temp = new  Node;
        temp->val = y;
        temp->next = NULL;

        head->next = temp;
        head = head->next;
    }

    first =  first ->next;
    while (first)
    {
        if(first->val != 0)
        {
            break;
        }
        first = first->next;
    }
    long long  all = 0;
    int count = getCount(first);
    for (int i = count - 1; i >=0 ; i--) {
        int temp = first->val;
        long long   tmc= temp * pow(10,i);
        all = all + tmc;
        if(all > INT_MAX || all < INT_MIN)
        {
            return 0;
        }

        first = first->next;
    }
    all = all * flag;


    return  (int)all;

}

```
