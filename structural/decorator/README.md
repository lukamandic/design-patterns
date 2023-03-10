# Decorator

Okay, imagine you have a plain, boring notebook. You want to make it look cool and unique, so you decide to add some decorations to it.

One way you could do this is by adding stickers to the cover. Each sticker adds a different design or pattern to the notebook, making it more interesting to look at. You can even add more stickers later if you want to change the look of the notebook again.

In programming, we can use a similar idea called the decorator pattern. Just like with the notebook, we start with a basic object (like a class or function) and then add extra functionality to it by "decorating" it with additional code.

So just like adding stickers to a notebook, using decorators in TypeScript lets us add extra functionality to our classes without changing the original class itself.

## Code

```js
class Pizza {
  constructor(public name: string, public price: number) {}
  getDescription() {
    return `${this.name}: $${this.price}`;
  }
}

function logMethods(target: any) {
  const originalMethods = Object.getOwnPropertyNames(target.prototype);
  originalMethods.forEach(method => {
    const originalFunc = target.prototype[method];
    target.prototype[method] = function(...args: any[]) {
      console.log(`[${new Date()}] ${target.name}.${method}(${args.join(", ")})`);
      return originalFunc.apply(this, args);
    }
  });
}

@logMethods
class Pizza {
  constructor(public name: string, public price: number) {}
  getDescription() {
    return `${this.name}: $${this.price}`;
  }
}

const pepperoniPizza = new Pizza("Pepperoni", 12.99);
console.log(pepperoniPizza.getDescription()); // [2023-03-10T12:00:00.000Z] Pizza.getDescription()

```