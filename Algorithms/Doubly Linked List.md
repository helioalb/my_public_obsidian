```python

class Node:
  def __init__(self, key, previous = None, next = None):
    self.key = key
    self.previous = previous
    self.next = next

class DoublyLinkedList:
  def __init__(self):
    self.head = None

  def add(self, key):
    if self.head is None:
      self.head = Node(key)
    elif key < self.head.key:
      self.head = Node(key, None, self.head)


  def show(self):
    cursor = self.head
    while cursor is not None:
      print(cursor.key)
      cursor = cursor.next


doubly_linked_list = DoublyLinkedList()

doubly_linked_list.add(2)
doubly_linked_list.add(1)

doubly_linked_list.show()
```
