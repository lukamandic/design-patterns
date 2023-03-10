# Bridge



## Code

```ts
interface Shape {
  draw(): void;
  setColor(color: string): void;
}

class Circle implements Shape {
  draw() {
    console.log("Drawing a circle...");
  }

  setColor(color: string) {
    console.log(`Setting circle color to ${color}`);
  }
}

class Square implements Shape {
  draw() {
    console.log("Drawing a square...");
  }

  setColor(color: string) {
    console.log(`Setting square color to ${color}`);
  }
}

abstract class ShapeBridge {
  protected shape: Shape;

  constructor(shape: Shape) {
    this.shape = shape;
  }

  abstract draw(): void;
}

class SolidShape extends ShapeBridge {
  draw() {
    this.shape.draw();
  }

  setSolidColor(color: string) {
    this.shape.setColor(color);
  }
}

class PatternShape extends ShapeBridge {
  draw() {
    console.log("Drawing a patterned shape...");
    this.shape.draw();
  }

  setPatternColor(color: string) {
    console.log(`Setting pattern color to ${color}`);
    this.shape.setColor(color);
  }
}

const circle = new Circle();
const square = new Square();

const solidCircle = new SolidShape(circle);
solidCircle.setSolidColor("red");
solidCircle.draw();

const patternedSquare = new PatternShape(square);
patternedSquare.setPatternColor("green");
patternedSquare.draw();

```

This allows us to change the way the shapes are drawn and colored without having to modify the Shape or ShapeBridge classes. We can also easily add new types of shapes and bridges without affecting the existing code.