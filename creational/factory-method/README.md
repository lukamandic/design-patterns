# Factory Method

So, imagine you want to make a lot of pizzas. You could make each pizza by hand, but that would take a long time and be really tiring. Instead, you could use a machine to make the pizzas for you!

In programming, we sometimes want to create objects (like a pizza) in a way that's efficient and easy to manage. That's where the Factory Method Design Pattern comes in.

The Factory Method is like a pizza-making machine. Instead of creating objects one by one, we use a factory method to create them for us. The factory method is a special function that creates objects of a certain type, based on some inputs.

This way, we can easily create new objects without having to write a lot of code every time. It's like having a pizza machine that can make any kind of pizza we want, just by pressing a few buttons.

## Difference between Factory Method and Abstract Factory

The Factory Method is a pattern where we define an interface or an abstract class for creating objects, but let the subclasses decide which class to instantiate. This means that we can create different objects of the same type by simply changing the subclass. For example, if we have a pizza factory, we might have a "Pizza" interface or abstract class, with different subclasses like "CheesePizza" or "PepperoniPizza". The Factory Method lets us create these different types of pizzas by calling a single method, without worrying about the details of how each pizza is made.

On the other hand, the Abstract Factory Method is a pattern that provides an interface for creating families of related or dependent objects, without specifying their concrete classes. This means that we can create entire families of related objects with a single method call. For example, if we have a car factory, we might have an "AbstractCarFactory" interface or abstract class, with different concrete factories like "SportsCarFactory" or "SUVFactory". Each concrete factory would create a family of related objects, such as wheels, engines, and interiors, that work together to create a complete car.

So, to sum up, the Factory Method lets us create different types of objects by changing the subclass, while the Abstract Factory Method lets us create families of related objects by calling a single method that creates all the necessary components.

## Code

```ts
// Define the interface for the product we want to create
interface Pizza {
  prepare(): void;
  bake(): void;
}

// Define the concrete implementations of the product
class CheesePizza implements Pizza {
  prepare() {
    console.log("Preparing cheese pizza...");
  }

  bake() {
    console.log("Baking cheese pizza...");
  }
}

class PepperoniPizza implements Pizza {
  prepare() {
    console.log("Preparing pepperoni pizza...");
  }

  bake() {
    console.log("Baking pepperoni pizza...");
  }
}

// Define the factory interface
interface PizzaFactory {
  createPizza(): Pizza;
}

// Define the concrete implementations of the factory
class CheesePizzaFactory implements PizzaFactory {
  createPizza() {
    return new CheesePizza();
  }
}

class PepperoniPizzaFactory implements PizzaFactory {
  createPizza() {
    return new PepperoniPizza();
  }
}

// Example usage
const cheesePizzaFactory = new CheesePizzaFactory();
const cheesePizza = cheesePizzaFactory.createPizza();
cheesePizza.prepare();
cheesePizza.bake();

const pepperoniPizzaFactory = new PepperoniPizzaFactory();
const pepperoniPizza = pepperoniPizzaFactory.createPizza();
pepperoniPizza.prepare();
pepperoniPizza.bake();

```