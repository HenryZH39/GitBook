# DFS
---
description: SELF - LEARNIG NOTES
---
- Pre-order : root – left – right
```java
stack.push(root)

while (stack not empty):

            curr = stack.pop();

            add to listl

            if has right node

               stack.push(curr.right)

            if has left node

               stack.push(curr.left)
```
- In-order : left – root – right
```java
curr = root

while (stack not empty || curr != null):

	while (curr != null):
	
		stack.push(curr)

        curr = curr.left

        pop the last node and add to List

        if node.right has right node

           curr  = curr. right
```
- Post-order : left – right – root
```java
curr = root;

while (curr != null || stack not empty):
	if curr != null

		stack.push(curr)

		curr = curr.left;

	else

		check the stack.peek node

		if  has right node and not visited the node

			curr = peek.right

		else

			record the right node have visited

			lastvist  = stack.pop()

```
