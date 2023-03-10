# Builder

The builder pattern is a way to build complex objects in a program. Think of it like building with Lego bricks - you can use different types of bricks to build all sorts of cool structures.

In the same way, with the builder pattern, you can use different building blocks or "parts" to build an object in a specific way. For example, let's say you want to build a car. You might need different parts, like wheels, a steering wheel, an engine, and so on.

The builder pattern lets you choose which parts you want to use and how you want to put them together to build your car. This way, you can customize your car to fit your needs.

Using the builder pattern can make it easier to build complex objects, because you don't have to worry about all the details yourself. You can just focus on choosing the parts you want and let the builder pattern take care of the rest.

## Code

```ts
class User {
  name: string;
  email: string;
  password: string;
  age?: number; // optional property

  constructor(builder: UserBuilder) {
    this.name = builder.name;
    this.email = builder.email;
    this.password = builder.password;
    this.age = builder.age;
  }
}

class UserBuilder {
  name: string;
  email: string;
  password: string;
  age?: number; // optional property

  constructor(name: string, email: string, password: string) {
    this.name = name;
    this.email = email;
    this.password = password;
  }

  setAge(age: number) {
    this.age = age;
    return this;
  }

  build() {
    return new User(this);
  }
}

// Usage example
const user1 = new UserBuilder("John Doe", "john.doe@example.com", "password123")
  .setAge(30)
  .build();

const user2 = new UserBuilder("Jane Smith", "jane.smith@example.com", "password456")
  .build();

console.log(user1);
console.log(user2);

```