# \@Monitor Decorator: Listening for Value Changes of the State Variables
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

You can use the \@Monitor method decorator in state management V2 to enhance the framework's capability to observe state variable changes.


\@Monitor provides the ability to observe state variables in V2. Before reading this topic, it is recommended to familiarize yourself with [\@ComponentV2](./arkts-new-componentV2.md), [\@ObservedV2 and \@Trace](./arkts-new-observedV2-and-trace.md), and [\@Local](./arkts-new-local.md).

>**NOTE**
>
> The \@Monitor decorator is supported since API version 12.
>
> This decorator can be used in atomic services since API version 12.

## Overview

To observe value changes of state variables at a granular level, you can use the \@Monitor decorator:

- The \@Monitor decorator can be used in custom components decorated with \@ComponentV2. However, it cannot observe changes to state variables that are not decorated with these decorators: [\@Local](arkts-new-local.md), [\@Param](arkts-new-param.md), [\@Provider](arkts-new-provider-and-consumer.md), [\@Consumer](arkts-new-provider-and-consumer.md), and [\@Computed](arkts-new-computed.md).

- The \@Monitor decorator can be used in a class along with [\@ObservedV2 and \@Trace](arkts-new-observedV2-and-trace.md) decorators. However, it cannot be used in a class that is not decorated with \@ObservedV2. \@Monitor cannot observe properties that are not decorated with \@Trace.
- When an observed property changes, the callback defined by \@Monitor is invoked. Strict equality (===) is used to determine property changes. If **false** is returned, the \@Monitor-decorated callback is triggered. When a property changes multiple times within an event, the initial value is compared with the final value to determine if the property has changed.
- A single \@Monitor decorator can observe changes to multiple properties simultaneously. When these properties change together within an event, the \@Monitor callback method is triggered only once.
- The \@Monitor decorator provides granular observation capability and can monitor changes to specific items in nested classes, multi-dimensional arrays, and object arrays. This requires that \@ObservedV2 decorates the nested class and \@Trace decorates member properties in object arrays.
- When \@Monitor observes an entire array, changes to individual array items are not observed. Changes caused by API calls of built-in types (Array, Map, Date, and Set) cannot be observed.
- In inheritance scenarios, you can define \@Monitor for the same property in both parent and child components. When the property changes, the \@Monitor callbacks defined in both components are called.
- Similar to the [\@Watch](arkts-watch.md) decorator, you must define the callback functions yourself. The difference is that \@Watch uses the function name as a parameter, while \@Monitor directly decorates the callback function. For a detailed comparison between \@Monitor and \@Watch, see [Comparing \@Monitor with \@Watch](#comparing-monitor-with-watch).

## Limitations of the \@Watch Decorator in State Management V1

The V1 version cannot observe changes to objects, individual properties in arrays, or array items. It also cannot retrieve the value before the change.

```ts
@Observed
class Info {
  name: string = 'Tom';
  age: number = 25;
}
@Entry
@Component
struct Index {
  @State @Watch('onInfoChange') info: Info = new Info();
  @State @Watch('onNumArrChange') numArr: number[] = [1,2,3,4,5];

  onInfoChange() {
    console.info(`info after change name: ${this.info.name}, age: ${this.info.age} `);
  }
  onNumArrChange() {
    console.info(`numArr after change ${this.numArr}`);
  }
  build() {
    Row() {
      Column() {
        Button('change info name')
          .onClick(() => {
            this.info.name = 'Jack';
          })
        Button('change info age')
          .onClick(() => {
            this.info.age = 30;
          })
        Button('change numArr[2]')
          .onClick(() => {
            this.numArr[2] = 5;
          })
        Button('change numArr[3]')
          .onClick(() => {
            this.numArr[3] = 6;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

In the preceding example, when you click **change info name** to modify the **name** property in **info**, or click **change info age** to change **age**, the \@Watch callback registered for **info** is triggered. When you click **change numArr[2]** to modify the third element in **numArr**, or click **change numArr[3]** to change the fourth element, the \@Watch callback registered for **numArr** is triggered. In both callbacks, the value before the data change cannot be obtained. This makes it inconvenient to track variable changes in complex scenarios, as you cannot determine which property or element change triggered the \@Watch event. Therefore, the \@Monitor decorator is introduced to observe changes to objects, individual properties in arrays, or array items, and to retrieve the value before the change.

## Decorator Description

| \@Monitor Property Decorator| Description                                                        |
| ------------------- | ------------------------------------------------------------ |
| Parameters         | Object property names of string type. Multiple properties can be observed simultaneously, separated by commas (,), for example, @Monitor('prop1', 'prop2'). Additionally, properties such as elements in multi-dimensional arrays, properties in nested objects, and properties in object arrays can be observed at a granular level. For details, see [Observed Changes](#observed-changes).|
| Decorated object           | \@Monitor-decorated member method. This callback is triggered when an observed property changes. The callback method takes a variable of the [IMonitor type](../../reference/apis-arkui/arkui-ts/ts-state-management-watch-monitor.md#imonitor12) as a parameter, from which you can retrieve information before and after the change.|

## Available APIs

For details about the APIs of the IMonitor and IMonitorValue\<T\> types, see [State Variable Change Listening](../../reference/apis-arkui/arkui-ts/ts-state-management-watch-monitor.md).

## Observed Changes

### Using \@Monitor in Custom Components Decorated with \@ComponentV2

When state variables observed by \@Monitor change, the callback is triggered.

- Variables observed by \@Monitor must be decorated with \@Local, \@Param, \@Provider, \@Consumer, or \@Computed. Otherwise, their changes cannot be detected. \@Monitor can observe multiple state variables simultaneously, with names separated by commas (,).

  ```ts
  @Entry
  @ComponentV2
  struct Index {
    @Local message: string = 'Hello World';
    @Local name: string = 'Tom';
    @Local age: number = 24;
    @Monitor('message', 'name')
    onStrChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`${path} changed from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      });
    }
    build() {
      Column() {
        Button('change string')
          .onClick(() => {
            this.message += '!';
            this.name = 'Jack';
        })
      }
    }
  }
  ```

- When the state variable observed by \@Monitor is a class object, only changes to the entire object can be detected. To observe changes to class properties, those properties must be decorated with \@Trace.

  ```ts
  class Info {
    name: string;
    age: number;
    constructor(name: string, age: number) {
      this.name = name;
      this.age = age;
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    @Local info: Info = new Info('Tom', 25);
    @Monitor('info')
    infoChange(monitor: IMonitor) {
      console.info(`info change`);
    }
    @Monitor('info.name')
    infoPropertyChange(monitor: IMonitor) {
      console.info(`info name change`);
    }
    build() {
      Column() {
        Text(`name: ${this.info.name}, age: ${this.info.age}`)
        Button('change info')
          .onClick(() => {
            this.info = new Info('Lucy', 18); // Can be observed
          })
        Button('change info.name')
          .onClick(() => {
            this.info.name = 'Jack'; // Cannot be observed
          })
      }
    }
  }
  ```

### Using \@Monitor in Classes Decorated with \@ObservedV2

When properties observed by \@Monitor change, the callback is triggered.

- Object properties observed by \@Monitor should be decorated with \@Trace. Otherwise, property changes cannot be detected. \@Monitor can observe multiple properties simultaneously, separated by commas (,).

  ```ts
  @ObservedV2
  class Info {
    @Trace name: string = 'Tom';
    @Trace region: string = 'North';
    @Trace job: string = 'Teacher';
    age: number = 25;
    // name is decorated with @Trace. Changes can be observed
    @Monitor('name')
    onNameChange(monitor: IMonitor) {
      console.info(`name change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
    // age is not decorated with @Trace. Changes cannot be observed
    @Monitor('age')
    onAgeChange(monitor: IMonitor) {
      console.info(`age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
    // region and job are decorated with @Trace. Changes can be observed
    @Monitor('region', 'job')
    onChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      })
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    info: Info = new Info();
    build() {
      Column() {
        Button('change name')
          .onClick(() => {
            this.info.name = 'Jack'; // Triggers onNameChange
          })
        Button('change age')
          .onClick(() => {
            this.info.age = 26; // Does not trigger onAgeChange
          })
        Button('change region')
          .onClick(() => {
            this.info.region = 'South'; // Triggers onChange
          })
        Button('change job')
          .onClick(() => {
            this.info.job = 'Driver'; // Triggers onChange
          })
      }
    }
  }
  ```

- \@Monitor can observe changes to nested properties, which must be decorated with @Trace.

  ```ts
  @ObservedV2
  class Inner {
    @Trace num: number = 0;
  }
  @ObservedV2
  class Outer {
    inner: Inner = new Inner();
    @Monitor('inner.num')
    onChange(monitor: IMonitor) {
      console.info(`inner.num change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    outer: Outer = new Outer();
    build() {
      Column() {
        Button('change num')
          .onClick(() => {
            this.outer.inner.num = 100; // Triggers onChange
          })
      }
    }
  }
  ```

- In inheritance scenarios, you can observe the same property multiple times in the inheritance chain.

  ```ts
  @ObservedV2
  class Base {
    @Trace name: string;
    // Observe the name property in the base class
    @Monitor('name')
    onBaseNameChange(monitor: IMonitor) {
      console.info(`Base Class name change`);
    }
    constructor(name: string) {
      this.name = name;
    }
  }
  @ObservedV2
  class Derived extends Base {
    // Observe the name property in the derived class
    @Monitor('name')
    onDerivedNameChange(monitor: IMonitor) {
      console.info(`Derived Class name change`);
    }
    constructor(name: string) {
      super(name);
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    derived: Derived = new Derived('AAA');
    build() {
      Column() {
        Button('change name')
          .onClick(() => {
            this.derived.name = 'BBB'; // Triggers onBaseNameChange and onDerivedNameChange sequentially
          })
      }
    }
  }
  ```

### General Observation Capabilities

\@Monitor also provides general observation capabilities.

- \@Monitor can observe items in arrays, including multi-dimensional arrays and object arrays. \@Monitor cannot observe changes caused by calling APIs of built-in types (Array, Map, Date, and Set). When \@Monitor observes an entire array, only value changes to the entire array can be detected. However, you can observe changes to the array's length to determine if items have been inserted or deleted. Currently, only dot notation (.) can be used to observe nested properties and array items.

  ```ts
  @ObservedV2
  class Info {
    @Trace name: string;
    @Trace age: number;
    
    constructor(name: string, age: number) {
      this.name = name;
      this.age = age;
    }
  }
  @ObservedV2
  class ArrMonitor {
    @Trace dimensionTwo: number[][] = [[1,1,1],[2,2,2],[3,3,3]];
    @Trace dimensionThree: number[][][] = [[[1],[2],[3]],[[4],[5],[6]],[[7],[8],[9]]];
    @Trace infoArr: Info[] = [new Info('Jack', 24), new Info('Lucy', 18)];
    // dimensionTwo is a two-dimensional array decorated with @Trace. Element changes can be observed
    @Monitor('dimensionTwo.0.0', 'dimensionTwo.1.1')
    onDimensionTwoChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`dimensionTwo path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      })
    }
    // dimensionThree is a three-dimensional array decorated with @Trace. Element changes can be observed
    @Monitor('dimensionThree.0.0.0', 'dimensionThree.1.1.0')
    onDimensionThreeChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`dimensionThree path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      })
    }
    // name and age properties are decorated with @Trace. Changes can be observed
    @Monitor('infoArr.0.name', 'infoArr.1.age')
    onInfoArrPropertyChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`infoArr path:${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      })
    }
    // infoArr is decorated with @Trace. Value changes can be observed
    @Monitor('infoArr')
    onInfoArrChange(monitor: IMonitor) {
      console.info(`infoArr whole change`);
    }
    // Array length changes can be observed
    @Monitor('infoArr.length')
    onInfoArrLengthChange(monitor: IMonitor) {
      console.info(`infoArr length change`);
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    arrMonitor: ArrMonitor = new ArrMonitor();
    build() {
      Column() {
        Button('Change dimensionTwo')
          .onClick(() => {
            // Triggers onDimensionTwoChange
            this.arrMonitor.dimensionTwo[0][0]++; 
            this.arrMonitor.dimensionTwo[1][1]++; 
          })
        Button('Change dimensionThree')
          .onClick(() => {
            // Triggers onDimensionThreeChange
            this.arrMonitor.dimensionThree[0][0][0]++;
            this.arrMonitor.dimensionThree[1][1][0]++; 
          })
        Button('Change info property')
          .onClick(() => {
            // Triggers onInfoArrPropertyChange
            this.arrMonitor.infoArr[0].name = 'Tom'; 
            this.arrMonitor.infoArr[1].age = 19; 
          })
        Button('Change whole infoArr')
          .onClick(() => {
            // Triggers onInfoArrChange, onInfoArrPropertyChange, and onInfoArrLengthChange
            this.arrMonitor.infoArr = [new Info('Cindy', 8)]; 
          })
        Button('Push new info to infoArr')
          .onClick(() => {
            // Triggers onInfoArrPropertyChange and onInfoArrLengthChange
            this.arrMonitor.infoArr.push(new Info('David', 50)); 
          })
      }
    }
  }
  ```

- When the entire object changes but the observed property remains unchanged, the \@Monitor callback is not triggered.

  The following code describes the behavior when executing instructions in the sequence of Step 1, Step 2, and Step 3.

  If you only execute Step 2 or Step 3 to change **name** or **age** values, the **onNameChange** and **onAgeChange** methods are triggered.

  ```ts
  @ObservedV2
  class Info {
    @Trace person: Person;
    @Monitor('person.name')
    onNameChange(monitor: IMonitor) {
      console.info(`name change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
    @Monitor('person.age')
    onAgeChange(monitor: IMonitor) {
      console.info(`age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
    constructor(name: string, age: number) {
      this.person = new Person(name, age);
    }
  }
  @ObservedV2
  class Person {
    @Trace name: string;
    @Trace age: number;
    constructor(name: string, age: number) {
      this.name = name;
      this.age = age;
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    info: Info = new Info('Tom', 25);
    build() {
      Column() {
        Button('Step1: Only change name')
          .onClick(() => {
            this.info.person = new Person('Jack', 25); // Triggers onNameChange but not onAgeChange
          })
        Button('Step2: Only change age')
          .onClick(() => {
            this.info.person = new Person('Jack', 18); // Triggers onAgeChange but not onNameChange
          })
        Button('Step3: Change name and age')
          .onClick(() => {
            this.info.person = new Person('Lucy', 19); // Triggers both onNameChange and onAgeChange
          })
      }
    }
  }
  ```

- If a property observed by \@Monitor changes multiple times within an event, the last change is used.

  ```ts
  @ObservedV2
  class Frequency {
    @Trace count: number = 0;
  
    @Monitor('count')
    onCountChange(monitor: IMonitor) {
      console.info(`count change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
  }
  
  @Entry
  @ComponentV2
  struct Index {
    frequency: Frequency = new Frequency();
  
    build() {
      Column() {
        Button('change count to 1000')
          .onClick(() => {
            for (let i = 1; i <= 1000; i++) {
              this.frequency.count = i;
            }
          })
        Button('change count to 0 then to 1000')
          .onClick(() => {
            for (let i = 999; i >= 0; i--) {
              this.frequency.count = i;
            }
            this.frequency.count = 1000; // onCountChange is not triggered
          })
      }
    }
  }
  ```

After clicking **change count to 1000**, the **onCountChange** method is triggered, logging `count change from 0 to 1000`. After clicking **change count to 0 then to 1000**, **onCountChange** is not triggered because the **count** property value remains 1000 before and after the event.

## Constraints

Observe the following constraints when using \@Monitor:

- Avoid observing the same property multiple times within a class. When a property is observed multiple times, only the last observation method takes effect.

  ```ts
  @ObservedV2
  class Info {
    @Trace name: string = 'Tom';
    @Monitor('name')
    onNameChange(monitor: IMonitor) {
      console.info(`onNameChange`);
    }
    @Monitor('name')
    onNameChangeDuplicate(monitor: IMonitor) {
      console.info(`onNameChangeDuplicate`);
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    info: Info = new Info();
    build() {
      Column() {
        Button('change name')
          .onClick(() => {
            this.info.name = 'Jack'; // Only triggers onNameChangeDuplicate
          })
      }
    }
  }
  ```

- When @Monitor receives multiple path parameters, the system determines duplicate observation based on the full combination result of the parameters. Spaces are added between parameters during full combination to distinguish them. For example, the full combination of 'ab' and 'c' is 'ab c', while 'a' and 'bc' becomes 'a bc'. These results are not equal. In the following example, Monitor 1, Monitor 2, and Monitor 3 all observe the name attribute. Monitor 2 and Monitor 3 have identical parameters (name position), so Monitor 2 does not take effect and only Monitor 3 works. When name changes, both onNameAgeChange and onNamePositionChangeDuplicate are triggered simultaneously. However, note that Monitor 2 and Monitor 3 implementations are still considered multiple @Monitor observations of the same attribute in the same class, which is not recommended.

  ```ts
  @ObservedV2
  class Info {
    @Trace name: string = 'Tom';
    @Trace age: number = 25;
    @Trace position: string = 'North';
    @Monitor('name', 'age') // Monitor 1
    onNameAgeChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`onNameAgeChange path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      });
    }
    @Monitor('name', 'position') // Monitor 2
    onNamePositionChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`onNamePositionChange path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      });
    }
    // name and position are observed repeatedly. Only the last definition takes effect
    @Monitor('name', 'position') // Monitor3
    onNamePositionChangeDuplicate(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        console.info(`onNamePositionChangeDuplicate path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      });
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    info: Info = new Info();
    build() {
      Column() {
        Button('change name')
          .onClick(() => {
            this.info.name = 'Jack'; // Triggers both onNameAgeChange and onNamePositionChangeDuplicate
          })
      }
    }
  }
  ```

- The \@Monitor parameter must be a string specifying the property name to observe. Only string literals, **const** constants, and **enum** values can be used as parameters. If a variable is used as a parameter, only the property corresponding to the variable's value during \@Monitor initialization is observed. When the variable changes, \@Monitor cannot dynamically update the observed property. The target property is determined during initialization and cannot be changed dynamically. Avoid using variables as \@Monitor parameters.

  ```ts
  const t2: string = 't2'; // const constant
  enum ENUM {
    T3 = 't3' // enum value
  };
  let t4: string = 't4'; // Variable
  @ObservedV2
  class Info {
    @Trace t1: number = 0;
    @Trace t2: number = 0;
    @Trace t3: number = 0;
    @Trace t4: number = 0;
    @Trace t5: number = 0;
    @Monitor('t1') // String literal
    onT1Change(monitor: IMonitor) {
      console.info(`t1 change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
    @Monitor(t2)
    onT2Change(monitor: IMonitor) {
      console.info(`t2 change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
    @Monitor(ENUM.T3)
    onT3Change(monitor: IMonitor) {
      console.info(`t3 change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
    @Monitor(t4)
    onT4Change(monitor: IMonitor) {
      console.info(`t4 change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    info: Info = new Info();
    build() {
      Column() {
        Button('Change t1')
          .onClick(() => {
            this.info.t1++; // Triggers onT1Change
          })
        Button('Change t2')
          .onClick(() => {
            this.info.t2++; // Triggers onT2Change
          })
        Button('Change t3')
          .onClick(() => {
            this.info.t3++; // Triggers onT3Change
          })
        Button('Change t4')
          .onClick(() => {
            this.info.t4++; // Triggers onT4Change
          })
        Button('Change var t4 to t5')
          .onClick(() => {
            t4 = 't5'; // Change variable value to 't5'
          })
        Button('Change t5')
          .onClick(() => {
            this.info.t5++; // onT4Change still observes t4. Does not trigger
          })
        Button('Change t4 again')
          .onClick(() => {
            this.info.t4++; // Triggers onT4Change
          })
      }
    }
  }
  ```

- Modifying the observed property within \@Monitor again may cause infinite loops and is not recommended.

  ```ts
  @ObservedV2
  class Info {
    @Trace count: number = 0;
    @Monitor('count')
    onCountChange(monitor: IMonitor) {
      this.count++; // Avoid this - may cause infinite loops
    }
  }
  ```

## Comparing \@Monitor with \@Watch

The following table compares the usage and functionality of \@Monitor and \@Watch.

|                    | \@Watch                                 | \@Monitor                                                    |
| ------------------ | --------------------------------------- | ------------------------------------------------------------ |
| Parameter              | Callback method name                             | Observed state variable name and property name                                      |
| Number of Observation Targets        | Single state variable                   | Multiple state variables                                      |
| Observation Capability          | Top-level state variables          | Granular state variables                                |
| Obtain Value Before Change| No                     | Yes                                            |
| Observation Condition          | Observed object is a state variable                     | Observed object is a state variable or class member property decorated with \@Trace               |
| Constraints          | Only in \@Component-decorated custom components| In \@ComponentV2-decorated custom components and \@ObservedV2-decorated classes|

## Use Scenarios

### Observing Granular Property Changes

\@Monitor can observe granular property changes and categorize them based on values before and after changes.

In the following example, changes to the **value** property are observed, and the display style of the **Text** component is adjusted based on the change amplitude.

```ts
@ObservedV2
class Info {
  @Trace value: number = 50;
}
@ObservedV2
class UIStyle {
  info: Info = new Info();
  @Trace color: Color = Color.Black;
  @Trace fontSize: number = 45;
  @Monitor('info.value')
  onValueChange(monitor: IMonitor) {
    let lastValue: number = monitor.value()?.before as number;
    let curValue: number = monitor.value()?.now as number;
    if (lastValue != 0) {
      let diffPercent: number = (curValue - lastValue) / lastValue;
      if (diffPercent > 0.1) {
        this.color = Color.Red;
        this.fontSize = 50;
      } else if (diffPercent < -0.1) {
        this.color = Color.Green;
        this.fontSize = 40;
      } else {
        this.color = Color.Black;
        this.fontSize = 45;
      }
    }
  }
}
@Entry
@ComponentV2
struct Index {
  textStyle: UIStyle = new UIStyle();
  build() {
    Column() {
      Text(`Important Value: ${this.textStyle.info.value}`)
        .fontColor(this.textStyle.color)
        .fontSize(this.textStyle.fontSize)
      Button('change!')
        .onClick(() => {
          this.textStyle.info.value = Math.floor(Math.random() * 100) + 1;
        })
    }
  }
}
```

## FAQs

### Effective and Expiration Time of Variable Observation by \@Monitor in Custom Components

When \@Monitor is defined in a custom component decorated with \@ComponentV2, it takes effect after the state variable is initialized and becomes invalid when the component is destroyed.

```ts
@ObservedV2
class Info {
  @Trace message: string = 'not initialized';

  constructor() {
    console.info('in constructor message change to initialized');
    this.message = 'initialized';
  }
}
@ComponentV2
struct Child {
  @Param info: Info = new Info();
  @Monitor('info.message')
  onMessageChange(monitor: IMonitor) {
    console.info(`Child message change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
  aboutToAppear(): void {
    this.info.message = 'Child aboutToAppear';
  }
  aboutToDisappear(): void {
    console.info('Child aboutToDisappear');
    this.info.message = 'Child aboutToDisappear';
  }
  build() {
    Column() {
      Text('Child')
      Button('change message in Child')
        .onClick(() => {
          this.info.message = 'Child click to change Message';
        })
    }
    .borderColor(Color.Red)
    .borderWidth(2)

  }
}
@Entry
@ComponentV2
struct Index {
  @Local info: Info = new Info();
  @Local flag: boolean = false;
  @Monitor('info.message')
  onMessageChange(monitor: IMonitor) {
    console.info(`Index message change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }

  build() {
    Column() {
      Button('show/hide Child')
        .onClick(() => {
          this.flag = !this.flag
        })
      Button('change message in Index')
        .onClick(() => {
          this.info.message = 'Index click to change Message';
        })
      if (this.flag) {
        Child({ info: this.info })
      }
    }
  }
}
```

In the preceding example, you can create and destroy a **Child** component to observe the effective and expiration time of \@Monitor defined in custom components. Follow these steps:

- When the **Index** component creates an instance of the **Info** class, the log outputs: `in constructor message change to initialized`. At this point, the \@Monitor in the **Index** component has not been successfully initialized, so it cannot observe message changes.
- After the **Index** component is created and the page loads, click **change message in Index**. \@Monitor can now observe changes, and the log outputs: `Index message change from initialized to Index click to change Message`.
- Click **show/hide Child** to create a **Child** component. After this component initializes the \@Param-decorated variables and \@Monitor, the **aboutToAppear** callback changes the message. Both the **Index** and **Child** components' \@Monitor instances can observe the change, logging: `Index message change from Index click to change Message to Child aboutToAppear` and `Child message change from Index click to change Message to Child aboutToAppear`.
- Click **change message in Child** to change the message. Both \@Monitor instances can observe the change, logging: `Index message change from Child aboutToAppear to Child click to change Message` and `Child message change from Child aboutToAppear to Child click to change Message`.
- Click **show/hide Child** to destroy the **Child** component and call the **aboutToDisappear** callback to change the message. Both \@Monitor instances can observe the change, logging: `Child aboutToDisappear, Index message change from Child click to change Message to Child aboutToDisappear`, and `Child message change from Child click to change Message to Child aboutToDisappear`.
- Click **change message in Index** to change the message. The **Child** component is destroyed and its \@Monitor is deregistered. Only the **Index** component's \@Monitor can observe changes, logging: `Index message change from Child aboutToDisappear to Index click to change Message`.

These steps demonstrate that \@Monitor defined in the **Child** component takes effect when the component is created and initialized, and becomes invalid when the component is destroyed.

### Effective and Expiration Time of Variable Observation by \@Monitor in Classes

When \@Monitor is defined in a class decorated with \@ObservedV2, it takes effect after the class instance is created and becomes invalid when the class instance is destroyed.

```ts
@ObservedV2
class Info {
  @Trace message: string = 'not initialized';

  constructor() {
    this.message = 'initialized';
  }
  @Monitor('message')
  onMessageChange(monitor: IMonitor) {
    console.info(`message change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
}

@Entry
@ComponentV2
struct Index {
  info: Info = new Info();

  aboutToAppear(): void {
    this.info.message = 'Index aboutToAppear';
  }

  build() {
    Column() {
      Button('change message')
        .onClick(() => {
          this.info.message = 'Index click to change message';
        })
    }
  }
}
```

In the preceding example, \@Monitor takes effect after the **info** class is created, which occurs after the class **constructor** but before the custom component's **aboutToAppear**. After the page loads, click **change message** to modify the message variable. The logs output:

```ts
message change from initialized to Index aboutToAppear
message change from Index aboutToAppear to Index click to change message
```

\@Monitor defined in a class becomes invalid when the class is destroyed. However, garbage collection determines when a class is actually destroyed and released. Even if the custom component is destroyed, the class might not be destroyed accordingly, causing \@Monitor to continue observing changes.

```ts
@ObservedV2
class InfoWrapper {
  info?: Info;
  constructor(info: Info) {
    this.info = info;
  }
  @Monitor('info.age')
  onInfoAgeChange(monitor: IMonitor) {
    console.info(`age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
}
@ObservedV2
class Info {
  @Trace age: number;
  constructor(age: number) {
    this.age = age;
  }
}
@ComponentV2
struct Child {
  @Param @Require infoWrapper: InfoWrapper;
  aboutToDisappear(): void {
    console.info('Child aboutToDisappear', this.infoWrapper.info?.age);
  }
  build() {
    Column() {
      Text(`${this.infoWrapper.info?.age}`)
    }
  }
}
@Entry
@ComponentV2
struct Index {
  dataArray: Info[] = [];
  @Local showFlag: boolean = true;
  aboutToAppear(): void {
    for (let i = 0; i < 5; i++) {
      this.dataArray.push(new Info(i));
    }
  }
  build() {
    Column() {
      Button('change showFlag')
        .onClick(() => {
          this.showFlag = !this.showFlag;
        })
      Button('change number')
        .onClick(() => {
          console.info('click to change age');
          this.dataArray.forEach((info: Info) => {
            info.age += 100;
          });
        })
      if (this.showFlag) {
        Column() {
          Text('Childs')
          ForEach(this.dataArray, (info: Info) => {
            Child({ infoWrapper: new InfoWrapper(info) })
          })
        }
        .borderColor(Color.Red)
        .borderWidth(2)
      }
    }
  }
}
```

In the preceding example, when you click **change showFlag** to toggle the **if** component condition, the **Child** component is destroyed. However, when you click **change number** to modify **age** values, the \@Monitor callback defined in **InfoWrapper** is still triggered. This occurs because although the **Child** custom component has executed **aboutToDisappear**, its member variable **infoWrapper** is not immediately destroyed. When variables change, the **onInfoAgeChange** method in **infoWrapper** can still be invoked, so the \@Monitor callback continues to be triggered.

Relying on garbage collection to cancel \@Monitor observation produces unstable results. Use either of the following methods to manage \@Monitor's expiration time:

1. Define \@Monitor in the custom component. When a custom component is destroyed, the state management framework automatically cancels \@Monitor observation. Therefore, after the custom component calls **aboutToDisappear**, the \@Monitor callback won't be triggered even if the component's data persists.

```ts
@ObservedV2
class InfoWrapper {
  info?: Info;
  constructor(info: Info) {
    this.info = info;
  }
}
@ObservedV2
class Info {
  @Trace age: number;
  constructor(age: number) {
    this.age = age;
  }
}
@ComponentV2
struct Child {
  @Param @Require infoWrapper: InfoWrapper;
  @Monitor('infoWrapper.info.age')
  onInfoAgeChange(monitor: IMonitor) {
    console.info(`age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
  aboutToDisappear(): void {
    console.info('Child aboutToDisappear', this.infoWrapper.info?.age);
  }
  build() {
    Column() {
      Text(`${this.infoWrapper.info?.age}`)
    }
  }
}
@Entry
@ComponentV2
struct Index {
  dataArray: Info[] = [];
  @Local showFlag: boolean = true;
  aboutToAppear(): void {
    for (let i = 0; i < 5; i++) {
      this.dataArray.push(new Info(i));
    }
  }
  build() {
    Column() {
      Button('change showFlag')
        .onClick(() => {
          this.showFlag = !this.showFlag;
        })
      Button('change number')
        .onClick(() => {
          console.info('click to change age');
          this.dataArray.forEach((info: Info) => {
            info.age += 100;
          })
        })
      if (this.showFlag) {
        Column() {
          Text('Childs')
          ForEach(this.dataArray, (info: Info) => {
            Child({ infoWrapper: new InfoWrapper(info) })
          })
        }
        .borderColor(Color.Red)
        .borderWidth(2)
      }
    }
  }
}
```

2. Clear the observed object. When the custom component is about to be destroyed, set the \@Monitor-observed object to empty. This prevents \@Monitor from observing changes to the original object, effectively canceling the observation.

```ts
@ObservedV2
class InfoWrapper {
  info?: Info;
  constructor(info: Info) {
    this.info = info;
  }
  @Monitor('info.age')
  onInfoAgeChange(monitor: IMonitor) {
    console.info(`age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
}
@ObservedV2
class Info {
  @Trace age: number;
  constructor(age: number) {
    this.age = age;
  }
}
@ComponentV2
struct Child {
  @Param @Require infoWrapper: InfoWrapper;
  aboutToDisappear(): void {
    console.info('Child aboutToDisappear', this.infoWrapper.info?.age);
    this.infoWrapper.info = undefined; // Prevent InfoWrapper from observing info.age
  }
  build() {
    Column() {
      Text(`${this.infoWrapper.info?.age}`)
    }
  }
}
@Entry
@ComponentV2
struct Index {
  dataArray: Info[] = [];
  @Local showFlag: boolean = true;
  aboutToAppear(): void {
    for (let i = 0; i < 5; i++) {
      this.dataArray.push(new Info(i));
    }
  }
  build() {
    Column() {
      Button('change showFlag')
        .onClick(() => {
          this.showFlag = !this.showFlag;
        })
      Button('change number')
        .onClick(() => {
          console.info('click to change age');
          this.dataArray.forEach((info: Info) => {
            info.age += 100;
          })
        })
      if (this.showFlag) {
        Column() {
          Text('Childs')
          ForEach(this.dataArray, (info: Info) => {
            Child({ infoWrapper: new InfoWrapper(info) })
          })
        }
        .borderColor(Color.Red)
        .borderWidth(2)
      }
    }
  }
}
```

### Passing Correct Input Parameters to \@Monitor

\@Monitor cannot verify input parameters during compilation. Currently, the following scenarios don't meet observation conditions but still trigger \@Monitor. Developers must correctly pass \@Monitor input parameters and avoid passing non-state variables to prevent function exceptions or unexpected behavior.

**Incorrect Usage 1**

```ts
@ObservedV2
class Info {
  name: string = 'John';
  @Trace age: number = 24;
  @Monitor('age', 'name') // Observe both state variable age and non-state variable name
  onPropertyChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`property path:${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
    })
  }
}
@Entry
@ComponentV2
struct Index {
  info: Info = new Info();
  build() {
    Column() {
      Button('change age&name')
        .onClick(() => {
          this.info.age = 25; // Change both state variable age and non-state variable name
          this.info.name = 'Johny';
        })
    }
  }
}
```

In this code, when state variable **age** and non-state variable **name** change simultaneously, the following log is generated:

```
property path:age change from 24 to 25
property path:name change from John to Johny
```

Actually, the **name** attribute is not observable and shouldn't be added to \@Monitor input parameters. Remove observation of the **name** attribute or decorate it with \@Trace to make it a state variable.

**Correct Usage 1**

```ts
@ObservedV2
class Info {
  name: string = 'John';
  @Trace age: number = 24;
  @Monitor('age') // Observe only the state variable age
  onPropertyChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`property path:${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
    })
  }
}
@Entry
@ComponentV2
struct Index {
  info: Info = new Info();
  build() {
    Column() {
      Button('change age&name')
        .onClick(() => {
          this.info.age = 25; // The state variable "age" is changed
          this.info.name = 'Johny';
        })
    }
  }
}
```

**Incorrect Usage 2**

```ts
@ObservedV2
class Info {
  name: string = 'John';
  @Trace age: number = 24;
  get myAge() {
    return this.age; // age is a state variable
  }
  @Monitor('myAge') // Observe a getter accessor not decorated with @Computed
  onPropertyChange() {
    console.info('age changed');
  }
}
@Entry
@ComponentV2
struct Index {
  info: Info = new Info();
  build() {
    Column() {
      Button('change age')
        .onClick(() => {
          this.info.age = 25; // The state variable "age" is changed
        })
    }
  }
}
```

In this code, the \@Monitor parameter is a **getter** accessor name. This accessor is not decorated with \@Computed and is not an observable variable. However, it uses a state variable for computation. When the state variable changes, **myAge** changes, invoking the \@Monitor callback. Add \@Computed to **myAge** or directly observe the state variable itself when the **getter** accessor returns a state variable.

**Correct Usage 2**

Make **myAge** a state variable:

```ts
@ObservedV2
class Info {
  name: string = 'John';
  @Trace age: number = 24;
  @Computed // Add @Computed to make myAge a state variable
  get myAge() {
    return this.age;
  }
  @Monitor('myAge') // Observe the @Computed-decorated getter accessor
  onPropertyChange() {
    console.info('age changed');
  }
}
@Entry
@ComponentV2
struct Index {
  info: Info = new Info();
  build() {
    Column() {
      Button('change age')
        .onClick(() => {
          this.info.age = 25; // The state variable "age" is changed
        })
    }
  }
}
```

Alternatively, observe the state variable directly:

```ts
@ObservedV2
class Info {
  name: string = 'John';
  @Trace age: number = 24;
  @Monitor('age') // Observe the state variable age directly
  onPropertyChange() {
    console.info('age changed');
  }
}
@Entry
@ComponentV2
struct Index {
  info: Info = new Info();
  build() {
    Column() {
      Button('change age')
        .onClick(() => {
          this.info.age = 25; // The state variable "age" is changed
        })
    }
  }
}
```
### Variables Cannot Be Observed During Accessibility Changes
\@Monitor only saves values when variables are accessible. When a state variable becomes inaccessible, value changes aren't recorded. In the following example, clicking any of the three buttons does not trigger the onChange callback.
If you need to observe accessibility changes (from accessible to inaccessible or vice versa), use [addMonitor](./arkts-new-addMonitor-clearMonitor.md#listening-for-variable-accessibility-changes).

```ts
@ObservedV2
class User {
  @Trace age: number = 10;
}

@Entry
@ComponentV2
struct Page {
  @Local user: User | undefined | null = new User();

  @Monitor('user.age')
  onChange(mon: IMonitor) {
    mon.dirty.forEach((path: string) => {
      console.info(`onChange: User property ${path} change from ${mon.value(path)?.before} to ${mon.value(path)?.now}`);
    });
  }

  build() {
    Column() {
      Text(`User age ${this.user?.age}`).fontSize(20)
      Button('set user to undefined').onClick(() => {
        // age: accessible -> inaccessible
        this.user = undefined;
      })
      Button('set user to User').onClick(() => {
        // age: inaccessible -> accessible
        this.user = new User();
      })
      Button('set user to null').onClick(() => {
        // age: accessible -> inaccessible
        this.user = null;
      })
    }
  }
}
```