### 链表反转
· 迭代法
由于语法错误，指针的表达形式错误，使得没有产生正确的结果`p->next` 改变为 `p.next`
```
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        p = head
        q = None
        while p:
            pr = p.next
            p.next = q
            q = p
            p = pr
        return q
```
· 递归法
```
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        p = head
        q = None
        while p:
            pr = p.next
            p.next = q
            q = p
            p = pr
        return q
    def reverseListv1(self,head):
        if head == None or head.next == None:   --等同于 if not head or not head.next
            return head
        pp = self.reverseList(head.next)
        head.next.next = head
        head.next = None
        return pp

```
· 完整版实现
```
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None


def reverseList(head):  # 循环的方法反转链表
    if head is None or head.next is None:
        return head
    p = head
    q = None
    while p:
        pr = p.next
        p.next = q
        q = p
        p = pr
    return q


head = ListNode(1)  # 给链表存入数据
p1 = ListNode(2) # 建立链表1->2->3->4->None;
p2 = ListNode(3)
p3 = ListNode(4)
head.next = p1
p1.next = p2
p2.next = p3
pp = reverseList(head)  # 输出链表 4->3->2->1->None
while pp:
    print(pp.val)
    pp = pp.next
```
