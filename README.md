# TEXT-EDITOR
## Introduction
I have made this project to apply the concept of **stack** datastructure to create a basic text editor.

View the project at:https://rishikaghosh.github.io/TEXT-EDITOR/
## Basic Idea
The two main characteristics of a stack datastructure are it's **push** and **pull** operations.

If you notice carefully,in a text editor,the most basic operations include **inserting element in a sequential order**(i.e one after an another) and **deleting them one by one**.
Also, in a text editor, you are able to perform the **undo operation** to retrieve the elements you deleted by mistake.

So, my idea was to use the push, pull operations to achieve these 3 basic tasks.
## The Logic
### Using Buffer
In the stack constructor, I have included a buffer.
``` js
this.buffer = 4;
```
1.Buffer objects are used to represent a fixed length sequence of bytes.


2.It restricts the the number of undo operations done by the stack.

So basically, it makes sure that the undo operations are performed sequentially.
