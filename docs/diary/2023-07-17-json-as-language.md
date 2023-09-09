---
title: JSON as Language
author: Xie Yuheng
date: 2023-07-17
---

Maybe we should not just embed a schema language in JSON,
but we should embed a dependently typed programming language in JSON.

We will keep the constraint of "one file one module".

And we can view an array as a program
with a list of statements and a return value.

Program can be nested and lexical scope can be supported.


`User.json`:

```json
[
  { "@import": "Phone", "from": "./Phone.json" },
  { "@let": "Address", "body": { "city": "string", "street": "string" } },
  { "@return": { "address": "Address", "phone": "Phone" } }
]
```

We also need to support abstraction over value.

`Tree.json`:

Concrete syntax:

```
datatype Tree(T: Type) {
  Node(leaf: Tree(T), right: Tree(T)): Tree(T)
  Leaf(value: T): Tree(T)
}
```

Embedded in JSON:

```json
{
  "@datatype": "Tree",
  "argTypes": { "T": "Type" },
  "cases": {
    "Node": {
      "argTypes": {
        "leaf": { "@apply": "Tree", "args": ["T"] },
        "right": { "@apply": "Tree", "args": ["T"] }
      },
      "returnType": { "@apply": "Tree", "args": ["T"] }
    }
    "Leaf": {
      "argTypes": { "value": "T" },
      "returnType": { "@apply": "Tree", "args": ["T"] }
    }
  }
}
```
