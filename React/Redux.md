我们可以用Object这样的数据结构去描述app的state。

To change something in the **state**, you need to dispatch an **action**.

To tie **state** and **actions** together, we write a function called a **reducer**.

**reducer** is just a function that takes state and action as arguments, and returns the next state of the app.

**Actions** are payloads of information 

Actions are plain JavaScript objects.

Actions must have a `type` property   