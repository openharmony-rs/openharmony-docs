# \@Track Decorator: Implementing Class Object Property-level Updates
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->


\@Track is a decorator used to decorate properties of class objects. Any changes to the properties decorated by \@Track will trigger only updates to the UI associated with those properties.


Before reading this topic, you are advised to read [\@State](./arkts-state.md) to have an understanding of the basic observation capabilities of state management.

> **NOTE**
>
> This decorator is supported in ArkTS widgets since API version 11.
>
> This decorator can be used in atomic services since API version 12.


## Overview

\@Track enables property-level update for the class object. When a class object is a state variable, the change of the \@Track decorated property triggers only the update of the property associated UI. If the class uses the \@Track decorator, the properties that are not decorated by \@Track cannot be used in the UI. Otherwise, a runtime error is reported.

## Class Property-Level Update

In state management V1, decorators such as \@State support the observation of the changes of the first-layer attributes by default. Although the changes of the first-layer attributes can trigger updates, the observation at the class attribute level cannot be implemented. The following example shows this limitation:

```ts
class Info {
  name: string = 'Jack';
  age: number = 12;
}

@Entry
@Component
struct Index {
  @State info: Info = new Info();

  // Use the log printing of getFontSize to determine which component triggers rendering.
  getFontSize(id: number): number {
    console.info(`Component ${id} render`);
    return 30;
  }

  build() {
    Column() {
      Text(`name: ${this.info.name}`)
        .fontSize(this.getFontSize(1))
      Text(`age: ${this.info.age}`)
        .fontSize(this.getFontSize(2))

      // Click the current button. You can find that only the name attribute is changed.
      // However, the two Text components are still refreshed.
      // Text(`age: ${this.info.age}`) is redundant refresh.
      Button('change name').onClick(() => {
        this.info.name = 'Jane';
      })

      // Click the current button. You can find that only the age attribute is changed.
      // However, the two Text components are still refreshed.
      // Text(`name: ${this.info.name}`) is redundant refresh.
      Button('change age').onClick(() => {
        this.info.age++;
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

> **NOTE**
>
> When the UI is refreshed, the attribute setting method of the component is executed. You can determine whether the current component is refreshed by checking whether the getFontSize method is called.

- After the UI is rendered for the first time, the following log is generated:
```
Component 1 render
Component 2 render
```
- When you click Button('change name'), even if only info.name is modified, the two Text components are still rendered again. The Text(`age: ${this.info.age}`) component does not use the name attribute, but is still refreshed because info.name is changed. Therefore, the refresh is redundant. The output logs are as follows:
```
Component 1 render
Component 2 render
```
-  Similarly, when you click Button('change age'), the Text(`name: ${this.info.name}`) component is refreshed. The output logs are as follows:
```
Component 1 render
Component 2 render
```

The root cause of the preceding redundant refresh is that the \@State decorator in the status management V1 cannot accurately observe the access and change of class attributes. To accurately observe class object attributes, the \@Track decorator is introduced.


## Decorator Description

| \@Track Decorator | Description                 |
| ------------------ | -------------------- |
| Decorator parameters  | None.|
| Allowed variable types| Non-static properties of class objects.|



## Observed Changes and Behavior

When a class object is a state variable, any changes to its properties decorated by \@Track will trigger only updates to the UI associated with those properties.

> **NOTE**
>
> When no property in the class object is decorated with \@Track, the behavior remains unchanged. \@Track is unable to observe changes of nested objects.

Using the @Track decorator can avoid redundant updates.

```ts
class LogTrack {
  @Track str1: string;
  @Track str2: string;

  constructor(str1: string) {
    this.str1 = str1;
    this.str2 = 'World';
  }
}

class LogNotTrack {
  str1: string;
  str2: string;

  constructor(str1: string) {
    this.str1 = str1;
    this.str2 = 'World';
  }
}

@Entry
@Component
struct AddLog {
  @State logTrack: LogTrack = new LogTrack('Hello');
  @State logNotTrack: LogNotTrack = new LogNotTrack('Hello');

  isRender(index: number) {
    console.log(`Text ${index} is rendered`);
    return 50;
  }

  build() {
    Row() {
      Column() {
        Text(this.logTrack.str1) // Text1
          .fontSize(this.isRender(1))
          .fontWeight(FontWeight.Bold)
        Text(this.logTrack.str2) // Text2
          .fontSize(this.isRender(2))
          .fontWeight(FontWeight.Bold)
        Button('change logTrack.str1')
          .onClick(() => {
            this.logTrack.str1 = 'Bye';
          })
        Text(this.logNotTrack.str1) // Text3
          .fontSize(this.isRender(3))
          .fontWeight(FontWeight.Bold)
        Text(this.logNotTrack.str2) // Text4
          .fontSize(this.isRender(4))
          .fontWeight(FontWeight.Bold)
        Button('change logNotTrack.str1')
          .onClick(() => {
            this.logNotTrack.str1 = 'Goodbye';
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

In the preceding example:

1. All properties in the **LogTrack** class are decorated by \@Track. After the **change logTrack.str1** button is clicked, **Text1** is updated, but **Text2** is not, as indicated by that only one log record is generated.
    ```ts
    Text 1 is rendered
    ```

2. None of the properties in the **logNotTrack** class is decorated by \@Track. After the **change logNotTrack.str1** button is clicked, both **Text3** and **Text4** are updated, as indicated by that two log records are generated. Redundant updates occur.
    ```ts
    Text 3 is rendered
    Text 4 is rendered
    ```

## Constraints

- If the \@Track decorator is used in a class, the non-\@Track decorated properties in the class cannot be used in the \@Component decorated UI. For example, these properties cannot be bound to components nor be used to initialize child components; otherwise, an error is reported during runtime. For details, see [Improperly Using Non-\@Track Decorated Properties Causes Errors](#improperly-using-non-track-decorated-properties-causes-errors). Non-\@Track decorated properties can be used in non-UI functions, such as event callback functions and lifecycle functions.

- In API version 19 and later, the \@Track decorator is used in the UI of [\@ComponentV2](./arkts-new-componentV2.md). No error is reported during running, but the UI is not refreshed. For details, see [Common Scenarios](./arkts-v1-v2-mixusage.md#observed-decorated-class).

- Whenever possible, avoid any combination of class objects that contain \@Track and those that do not in, for example, union types and class inheritance.


## Use Scenarios

### \@Track and Custom Component Updates

This example is used to clarify the processing steps of custom component updates and \@Track. The **log** object is a state variable decorated by \@State. Its **logInfo** property is decorated by \@Track, but other properties are not, and the values of these other properties are not updated through the UI.


```ts
class Log {
  @Track logInfo: string;
  owner: string;
  id: number;
  time: Date;
  location: string;
  reason: string;

  constructor(logInfo: string) {
    this.logInfo = logInfo;
    this.owner = 'OH';
    this.id = 0;
    this.time = new Date();
    this.location = 'CN';
    this.reason = 'NULL';
  }
}

@Entry
@Component
struct AddLog {
  @State log: Log = new Log('origin info.');

  build() {
    Row() {
      Column() {
        Text(this.log.logInfo)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            // Properties that are not decorated by @Track can be used in click events.
            console.log('owner: ' + this.log.owner +
              ' id: ' + this.log.id +
              ' time: ' + this.log.time +
              ' location: ' + this.log.location +
              ' reason: ' + this.log.reason);
            this.log.time = new Date();
            this.log.id++;

            this.log.logInfo += ' info.';
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

Processing steps:

1. The click event **Text.onClick** of the **AddLog** custom component increases the value of **info**.

2. In response to the change of the \@State decorated variable **log**, the \@Track decorated property **logInfo** is updated, and the **Text** component is re-rendered.

## FAQs

### Improperly Using Non-\@Track Decorated Properties Causes Errors

If a non-\@Track decorated property is used in the UI, an error is reported during runtime.

```ts
class Person {
  // id is decorated by @Track.
  @Track id: number;
  // age is not decorated by @Track.
  age: number;

  constructor(id: number, age: number) {
    this.id = id;
    this.age = age;
  }
}

@Entry
@Component
struct Parent {
  @State parent: Person = new Person(2, 30);

  build() {
    // Property that is not decorated by @Track cannot be used in the UI. Otherwise, an error is reported during runtime.
    Text(`Parent id is: ${this.parent.id} and Parent age is: ${this.parent.age}`)
  }
}
```
