# Adapter

Sometimes you have different pieces of code that can't work together because they have different interfaces (or ways of talking to each other). An adapter acts as a middleman between these different pieces of code and makes them work together by translating the interfaces so that they can understand each other.

For example, let's say you have two classes A and B, but they have different methods and properties. You need to use class A in your code, but it's not compatible with class B. You can create an adapter that translates the methods and properties of class A into those that class B expects. This way, your code can use class A as if it was class B.

The adapter pattern is useful because it allows you to reuse code that would otherwise be incompatible, and it can save you a lot of time and effort in development.

## Code

```ts
interface Target {
  request(): void;
}

class Adapter {
  private readonly adaptee: Adaptee;

  constructor(adaptee: Adaptee) {
    this.adaptee = adaptee;
  }

  request(): void {
    this.adaptee.specificRequest();
  }
}

class Adaptee {
  public specificRequest(): void {
    console.log("Adaptee's specific request method");
  }
}

class Client {
  public run(target: Target): void {
    target.request();
  }
}

const client = new Client();
const adaptee = new Adaptee();
const adapter = new Adapter(adaptee);
client.run(adapter);

```