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
### Inside stack.js
#### Using Buffer
In the stack constructor, I have included a buffer.
``` js
this.buffer = 4;
```
* Buffer objects are used to represent a fixed length sequence of bytes.
* It restricts the the number of undo operations done by the stack.

So basically, it makes sure that the undo operations are performed **sequentially**.
#### The Push() operation
The push operation used in this project is similar to the basic push() operation of a stack with some slight changes.
``` js
    push(type, char){
        if(this.isEmpty()){
            if(type===0)
                this.stack.push([type, char]);
        } else{
            let
            tmp = this.top();
            if(tmp[0]===type && tmp[1].length < this.buffer){
                let top = this.pop();
                top[1] = char + top[1];
                this.stack.push(top);
            } else{
                this.stack.push([type, char]);
            }
        }
        this.size++;
    }
   ```
 * The **type** variable is used to store two kinds of operations
   * push - 0
   * pop - 1
 * It was important to differentiate the two operations in this function like this as the undo operation messes up the order in which the elements were inserted in the stack, once they are popped.
 * Therefore, if we want to push back the popped elements using the undo operation, we need to reverse the order 
     ``` js
     if(tmp[0]===type && tmp[1].length < this.buffer){
                let top = this.pop();
                top[1] = char + top[1];
                this.stack.push(top);
            }
    ```
  So, the type value decides whether we need to reverse the order of the elements pushed in the stack after we use the undo operation.
  
