---
title: JSON as language
author: Xie Yuheng
date: 2023-07-17
---

We will keep the constraint of "one file one schema".

And we can view an array as a program
with a list of statements and a return schema.

Program can be nested and lexical scope can be supported.

We also need to support abstraction over schema and value.

`User.schema.json`:

```json
[
  { "@import": "Phone", "@from": "./Phone.schema.json" },
  { "@let": "Address", "=": { "city": "string", "street": "string" } },
  { "@return": { "address": "Address", "phone": "Phone" } }
]
```

`Tree.schema.json`:

```json
{
  "@self": "Tree",
  "@type": "lambda",
  "@args": { "T": "Schema" },
  "@body": [
    {
      "@let": "Node", "=": {
        "left": { "@apply": "Tree", "@to": "T" },
        "right": { "@apply": "Tree", "@to": "T" }
      }
    },
    { "@let": "Leaf", "=": "T" },
    {
      "@return": {
        "@union": [
          { "@apply": "Node", "@to": "T" },
          { "@apply": "Leaf", "@to": "T" }
        ]
      }
    }
  ]
}
```

This is absurd, because we could just implement
a new dependently typed language.

```
datatype Tree(T: Type) {
  Node(leaf: Tree(T), right: Tree(T)): Tree(T)
  Leaf(value: T): Tree(T)
}
```
