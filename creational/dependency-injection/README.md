# Dependency Injection

Let's say you have a program that needs some objects or functions to work correctly. Instead of creating these objects or functions within the program, you ask someone else to give them to you. This someone else is called the "dependency injector," and the objects or functions you need are called "dependencies."

The dependency injector will bring the dependencies to your program, and your program can use them to do its work. This makes your program more modular and easier to maintain because you can replace the dependencies with new ones without changing the code of your program.

In summary, Dependency Injection is a pattern that allows you to separate the creation of dependencies from the code that uses them, making your code more flexible and easier to maintain. It's like asking your friend for the ingredients you need to bake a cake instead of going to the store yourself.

## Code

```ts
interface ILogger {
  log(message: string): void;
}

class Calculator {
  private logger: ILogger;

  constructor() {
    this.logger = new ConsoleLogger();
  }

  add(a: number, b: number): number {
    const result = a + b;
    this.logger.log(`The result of ${a} + ${b} is ${result}.`);
    return result;
  }
}

class Calculator {
  private logger: ILogger;

  constructor(logger: ILogger) {
    this.logger = logger;
  }

  add(a: number, b: number): number {
    const result = a + b;
    this.logger.log(`The result of ${a} + ${b} is ${result}.`);
    return result;
  }
}

class FileLogger implements ILogger {
  log(message: string): void {
    // Log message to a file...
  }
}

const logger = new FileLogger();
const calculator = new Calculator(logger);
calculator.add(2, 3);
```