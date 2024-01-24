---
tags:
  - algorithms
---

## binary-search-tree property
Let `x` be a node in a binary search tree. If `y`is a node in the left subtree of `y`, then `y.key <= x.key`. If `y` is a node in the right subtree of *x*, then `y.key >= x.key`.  [[Cormen]]

## Diferenças entre os algoritimos de "walk"

Tudo é em relação ao node root.

- O in-order é: esquerda, **root**, direita.
- No pré-order, o **root** vem antes (por isso o "pré"): **root**, esquerda, direita.
- No pós-order, o **root** vem depois de tudo (por isso o "pós"): esquerda, direita, **root**
## Exemplo de in order

```php
<?php
class Node{
    public int $key;
    public ?Node $left;
    public ?Node $right;

    public function __construct(int $key, ?Node $left = null, ?Node $right = null) {
        $this->key = $key;
        $this->left = $left;
        $this->right = $right;
    }
}

$three = new Node(3);
$five = new Node(5);
$four = new Node(4, $three, $five);

$eight = new Node(8);
$seven = new Node(7, null, $eight);

$six_root = new Node(6, $four, $seven);

function inOrder(?Node $node) {
    if (is_null($node))
        return;

    inOrder($node->left);
    echo $node->key . ' ';
    inOrder($node->right);
}

inOrder($six_root);
```

## Exemplo de pré order [[Python]]

```python
class Node:
  def __init__(self, key, left = None, right = None):
    self.key = key
    self.left = left
    self.right = right

three = Node(3);
five = Node(5);
four = Node(4, three, five);

eight = Node(8);
seven = Node(7, None, eight);

six_root = Node(6, four, seven);


def pre_order(node: Node) -> None:
  if node is None:
    return

  print(node.key)
  pre_order(node.left)
  pre_order(node.right)


pre_order(six_root)
```

## Exemplo pós order [[Javascript]]

```javascript
class Node {
  constructor(key, left, right) {
    this.key = key;
    this.left = left;
    this.right = right;
  }
}

three = new Node(3);
five = new Node(5);
four = new Node(4, three, five);

eight = new Node(8);
seven = new Node(7, null, eight);

six_root = new Node(6, four, seven);

function postOrder(node) {
  if (node == null)
    return;

  postOrder(node.left);
  postOrder(node.right);
  console.log(node.key);
}

postOrder(six_root);
```
