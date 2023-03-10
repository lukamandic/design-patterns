# Observer

So, let's imagine that you're at a party with your friends. You all start dancing, but then you notice that one of your friends, let's call her Sarah, isn't dancing with the rest of the group. Instead, she's sitting in the corner, looking sad.

You decide to check on Sarah and ask her what's wrong. She tells you that she's upset because she broke up with her boyfriend. You listen to her and try to cheer her up by telling her jokes and making her laugh. Eventually, she starts to feel better and joins the rest of the group on the dance floor.

Now, let's think about this situation in terms of the observer pattern. You were the observer, and Sarah was the subject being observed. You noticed that something was wrong with her and took action to help her feel better. In this way, you were acting as an observer, and Sarah was the subject that you were observing.

In computer science, the observer pattern is a design pattern that allows an object, the observer, to watch another object, the subject, and be notified when the subject's state changes. The observer can then take action based on the new state of the subject. It's like being a good friend who notices when someone is upset and takes action to help them feel better.

So, that's the observer pattern! It's a way for objects in a program to communicate with each other and take action based on changes in each other's states.

## Code

```ts
interface TemperatureSensor {
  addObserver(observer: TemperatureObserver): void;
  removeObserver(observer: TemperatureObserver): void;
  notifyObservers(): void;
}

interface TemperatureObserver {
  update(temperature: number): void;
}

class WeatherStation implements TemperatureSensor {
  private observers: TemperatureObserver[] = [];
  private temperature: number = 0;

  addObserver(observer: TemperatureObserver): void {
    this.observers.push(observer);
  }

  removeObserver(observer: TemperatureObserver): void {
    const index = this.observers.indexOf(observer);
    if (index !== -1) {
      this.observers.splice(index, 1);
    }
  }

  notifyObservers(): void {
    for (const observer of this.observers) {
      observer.update(this.temperature);
    }
  }

  setTemperature(temperature: number): void {
    this.temperature = temperature;
    this.notifyObservers();
  }
}

class TemperatureDisplay implements TemperatureObserver {
  private temperature: number = 0;

  update(temperature: number): void {
    this.temperature = temperature;
    console.log(`The current temperature is ${this.temperature} degrees Celsius`);
  }
}

const weatherStation = new WeatherStation();
const temperatureDisplay = new TemperatureDisplay();

weatherStation.addObserver(temperatureDisplay);

weatherStation.setTemperature(20);
// Output: The current temperature is 20 degrees Celsius

```