## Implement a stack using an array in JavaScript. Include the necessary methods such as push, pop, and isEmpty

```
class Stack {
  constructor() {
    this.items = [];
  }

  push(element) {
    this.items.push(element);
  }

  pop() {
    if (this.isEmpty()) {
      return "Stack is empty";
    }
    return this.items.pop();
  }

  isEmpty() {
    return this.items.length === 0;
  }
}

const stack = new Stack();
stack.push(1);
stack.push(2);
stack.push(3);

console.log(stack.pop()); // Output: 3
console.log(stack.pop()); // Output: 2
console.log(stack.isEmpty()); // Output: false

```
## Implement a queue using an array in JavaScript. Include the necessary methods such as enqueue, dequeue, and isEmpty.

```
class Queue {
  constructor() {
    this.items = [];
  }

  enqueue(element) {
    this.items.push(element);
  }

  dequeue() {
    if (this.isEmpty()) {
      return "Queue is empty";
    }
    return this.items.shift();
  }

  isEmpty() {
    return this.items.length === 0;
  }
}


const queue = new Queue();
queue.enqueue(1);
queue.enqueue(2);


console.log(queue.dequeue()); // Output: 1
console.log(queue.dequeue()); // Output: 2
console.log(queue.isEmpty()); // Output: false

```