# Iterator

So, you know how sometimes we have a list of things we want to do something with, like a list of chores we need to do around the house?

Well, imagine we have a program that needs to do something with a list of things, but we don't want to have to go through the whole list at once. It might be too big or too complicated to handle all at once.

That's where the iterator pattern comes in. It's like having a special helper that helps us go through the list one thing at a time, so we don't have to worry about everything all at once.

The iterator pattern is just a way to organize our code so that we can easily move through a collection of things, like a list or an array, without having to know all the details about how the collection is set up or how it works.

Basically, an iterator is an object that lets us loop through a collection one item at a time. So instead of having to write a lot of code to go through the whole list and figure out what to do with each item, we can just use the iterator to go through each item one by one and do something with it.

That's the basics of the iterator pattern. It's just a way to make it easier to work with lists or collections of things by breaking them down into smaller pieces that we can handle more easily.

## Code

```ts
class MyList {
  private items: number[] = [];

  addItem(item: number) {
    this.items.push(item);
  }

  // This method returns an iterator object
  getIterator() {
    return new MyIterator(this.items);
  }
}

class MyIterator {
  private index = 0;

  constructor(private items: number[]) {}

  // This method returns whether there are more items to iterate over
  hasNext() {
    return this.index < this.items.length;
  }

  // This method returns the next item in the iteration
  getNext() {
    if (this.hasNext()) {
      return this.items[this.index++];
    }
    return null;
  }
}

// Example usage
const myList = new MyList();
myList.addItem(1);
myList.addItem(2);
myList.addItem(3);

const myIterator = myList.getIterator();

while (myIterator.hasNext()) {
  const currentItem = myIterator.getNext();
  console.log(currentItem);
}
```