# Chain of Responsibility

In software development, we might have a group of objects that need to handle requests. Each object in the chain has the ability to handle the request, but if it can't, it passes it to the next object in the chain. This continues until an object is found that can handle the request.

The chain of responsibility pattern is useful because it allows us to handle requests or tasks in a flexible way. We can easily add or remove objects from the chain, and we can change the order of the objects as needed. This makes our code more modular and easier to maintain over time.

## Code

```ts
// Define the PaymentProcessor class
class PaymentProcessor {
  private maximumAmount: number;
  private nextProcessor: PaymentProcessor | null;

  constructor(maximumAmount: number) {
    this.maximumAmount = maximumAmount;
    this.nextProcessor = null;
  }

  // Set the next processor in the chain
  public setNextProcessor(processor: PaymentProcessor) {
    this.nextProcessor = processor;
  }

  // Handle the payment request
  public processPayment(amount: number) {
    if (amount <= this.maximumAmount) {
      console.log(`Payment processed by processor with maximum amount of ${this.maximumAmount}`);
    } else if (this.nextProcessor) {
      console.log(`Payment passed to next processor in chain with maximum amount of ${this.nextProcessor.maximumAmount}`);
      this.nextProcessor.processPayment(amount);
    } else {
      console.log('Payment could not be processed by any processor in the chain');
    }
  }
}

// Create the payment processors and set the chain
const processor1 = new PaymentProcessor(50);
const processor2 = new PaymentProcessor(100);
const processor3 = new PaymentProcessor(200);

processor1.setNextProcessor(processor2);
processor2.setNextProcessor(processor3);

// Test the payment processors
processor1.processPayment(25);
processor1.processPayment(75);
processor1.processPayment(150);
processor1.processPayment(250);

/*
Payment processed by processor with maximum amount of 50
Payment processed by processor with maximum amount of 100
Payment passed to next processor in chain with maximum amount of 200
Payment could not be processed by any processor in the chain
*/
```