## Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well. You must not use any built-in exponent function or operator. 

```
int mySqrt(int x) {
        long long int sqrt = 0;
        long long int i = 1;
        while(i*i<=x){
            sqrt = i;
            i++;
        }
        return sqrt;
    }

```

## You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

## You may assume the two numbers do not contain any leading zero, except the number 0 itself.

```
ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode dummy(0);
        ListNode* node = &dummy;
        int c = 0;
        while(l1 || l2 || c){
            int sum = (l1?l1->val:0)+(l2?l2->val:0)+c;
            c = sum/10;
            node->next = new ListNode(sum%10);
            node=node->next;
            l1=l1?l1->next:l1;
            l2=l2?l2->next:l2;
        }
        return dummy.next;
    }

```