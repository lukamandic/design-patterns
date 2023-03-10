# Interpreter

Imagine you're trying to communicate with someone who speaks a different language than you. Even though you might not understand their language, you might be able to figure out what they're saying by looking at their body language and gestures.

The Interpreter pattern works in a similar way, but for computer programs. It helps us understand and interpret complex expressions or sentences written in a programming language.

Here's an example: imagine you have a program that needs to perform calculations based on user input. The user might enter something like "5 + 3 * 2", which needs to be interpreted and evaluated correctly.

The Interpreter pattern helps us break down this expression into smaller parts and figure out what each part means. We can create different "interpreters" for each part of the expression, like one for addition and one for multiplication.

By breaking down the expression and interpreting each part, we can solve the problem and perform the correct calculations. It's like understanding the different parts of a sentence to figure out the meaning of the whole thing.

## Code

```ts
// Base expression interpreter
abstract class Expression {
  abstract interpret(): number;
}

// Interpreter for numeric expressions
class NumberExpression extends Expression {
  constructor(private value: number) {
    super();
  }
  interpret(): number {
    return this.value;
  }
}

// Interpreter for addition
class AdditionExpression extends Expression {
  constructor(private expression1: Expression, private expression2: Expression) {
    super();
  }
  interpret(): number {
    return this.expression1.interpret() + this.expression2.interpret();
  }
}

// Interpreter for multiplication
class MultiplicationExpression extends Expression {
  constructor(private expression1: Expression, private expression2: Expression) {
    super();
  }
  interpret(): number {
    return this.expression1.interpret() * this.expression2.interpret();
  }
}

// Interpreter for subtraction
class SubtractionExpression extends Expression {
  constructor(private expression1: Expression, private expression2: Expression) {
    super();
  }
  interpret(): number {
    return this.expression1.interpret() - this.expression2.interpret();
  }
}

// Create the expression tree
const expression = new SubtractionExpression(
  new AdditionExpression(
    new NumberExpression(3),
    new MultiplicationExpression(
      new NumberExpression(4),
      new NumberExpression(2)
    )
  ),
  new NumberExpression(1)
);

// Evaluate the expression
const result = expression.interpret();
console.log(result); // Output: 10
```