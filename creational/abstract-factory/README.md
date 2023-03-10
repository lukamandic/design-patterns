# Abstract Factory

Think of the abstract factory pattern as a way to create different kinds of things without having to know all the details of how they are made. It's like going to a store and asking for a toy without having to know how the toy was made or what parts it's made of.

In our example, we have a bunch of characters in a game, like a warrior, mage, and archer. Instead of creating each character one at a time and knowing all the details about how they're made, we use a CharacterFactory to create them for us.

The CharacterFactory is like a toy store that knows how to make different kinds of characters. We just tell the CharacterFactory what kind of character we want (like a warrior or a mage) and it makes it for us. We don't have to know all the details of how the characters are made, we just need to know what kind of character we want.

By using the abstract factory pattern, we can easily create new kinds of characters in the future without having to change all of our code. We can just add a new type of character to the CharacterFactory and then create it the same way we create the other characters.

Overall, the abstract factory pattern is a way to create different things without having to know all the details of how they're made. It makes it easy to create new things in the future and is a useful pattern for building flexible and extensible programs.

## Code

```ts
// Define the abstract classes for characters
abstract class Character {
  public health: number;
  public attackPower: number;
  public abstract type: string;

  constructor() {
    this.health = 100;
  }

  public attack(): void {
    console.log(`${this.type} attacks with power ${this.attackPower}`);
  }
}

class Warrior extends Character {
  public type = "Warrior";
  constructor() {
    super();
    this.attackPower = 10;
  }
}

class Mage extends Character {
  public type = "Mage";
  constructor() {
    super();
    this.attackPower = 15;
  }
}

class Archer extends Character {
  public type = "Archer";
  constructor() {
    super();
    this.attackPower = 12;
  }
}

// Define the factory class for characters
class CharacterFactory {
  public createWarrior(): Warrior {
    return new Warrior();
  }

  public createMage(): Mage {
    return new Mage();
  }

  public createArcher(): Archer {
    return new Archer();
  }
}

// Create a new instance of the factory class
const factory = new CharacterFactory();

// Create new instances of each type of character using the factory
const warrior = factory.createWarrior();
const mage = factory.createMage();
const archer = factory.createArcher();

// Test the characters by calling their attack methods
warrior.attack(); // output: "Warrior attacks with power 10"
mage.attack(); // output: "Mage attacks with power 15"
archer.attack(); // output: "Archer attacks with power 12"

```