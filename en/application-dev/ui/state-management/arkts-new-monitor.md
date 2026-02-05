# \@Monitor Decorator: Listening for Value Changes of the State Variables
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

You can use \@Monitor, a method decorator in state management V2, to enhance the capability of the state management framework to listen for the state variable changes


\@Monitor provides the capability of listening for state variables of V2. Before reading this topic, it is recommended to familiarize yourself with [\@ComponentV2](./arkts-create-custom-components.md#componentv2), [\@ObservedV2 and \@Trace](./arkts-new-observedV2-and-trace.md), and [\@Local](./arkts-new-local.md).

>**NOTE**
>
> The \@Monitor decorator is supported since API version 12.
>
> This decorator can be used in atomic services since API version 12.
>
> This decorator can be used in ArkTS widgets since API version 23.

## Overview

To listen for value changes of the state variables in a lower level, you can use the \@Monitor decorator:

- The \@Monitor decorator can be used in custom components decorated by \@ComponentV2. But it cannot listen for the changes of the state variables that are not decorated by these decorators: [\@Local](arkts-new-local.md), [\@Param](arkts-new-param.md), [\@Provider](arkts-new-provider-and-consumer.md), [\@Consumer](arkts-new-provider-and-consumer.md) and [\@Computed](arkts-new-computed.md).

- The \@Monitor decorator can be used in a class together with [\@ObservedV2 and \@Trace](arkts-new-observedV2-and-trace.md) decorators. But it cannot be used in a class that is not decorated by \@ObservedV2. \@Monitor cannot listen for the properties that are not decorated by \@Trace.
- When the listened property changes, the callback defined by \@Monitor will be called. Strict equality (===) is used to determine whether a property is changed. If **false** is return, the \@Monitor decorated callback is triggered. When a property is changed for multiple times in an event, the initial value will be compared with the final value to determine whether the property is changed.
- A single \@Monitor decorator can listen for the changes of multiple properties at the same time. When these properties change together in an event, the \@Monitor callback method is triggered only once.
- The \@Monitor decorator has lower-level listening capability and can listen for changes of specified items in nested classes, multi-dimensional arrays, and object arrays. The observation requires that \@ObservedV2 decorate the nested class and \@Trace decorate the member properties in an object array.
- When \@Monitor observes an entire array, changes to individual array items are not observed. \@Monitor cannot listen for changes caused by calling APIs of built-in types (Array, Map, Date, and Set).
- In the inheritance scenario, you can define \@Monitor for the same property in the parent and child components for listening. When the property changes, the \@Monitor callback defined in the parent and child components is called.
- Similar to the [\@Watch](arkts-watch.md) decorator, you should define the callback functions by yourselves. The difference is that the \@Watch decorator uses the function name as a parameter, while the \@Monitor directly decorates the callback function. For details about the comparison between \@Monitor and \@Watch, see [Comparing \@Monitor with \@Watch](#comparing-monitor-with-watch).

## Limitations of the \@Watch decorator in State Management V1

This V1 version cannot listen for the changes of an object, a single property in an array, or array items. It also cannot obtain the value before change.
<!-- @[monitor_watch_decorator_limitations_v1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/WatchDecoratorLimitationsV1.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@Observed
class Info {
  public name: string = 'Tom';
  public age: number = 25;
}

@Entry
@Component
struct Index {
  @State @Watch('onInfoChange') info: Info = new Info();
  @State @Watch('onNumArrChange') numArr: number[] = [1, 2, 3, 4, 5];

  onInfoChange() {
    hilog.info(0xFF00, 'testTag', '%{public}s', `info after change name: ${this.info.name}, age: ${this.info.age} `);
  }

  onNumArrChange() {
    hilog.info(0xFF00, 'testTag', '%{public}s', `numArr after change ${this.numArr}`);
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

In the preceding code, when you click **change info name** to change the **name** property in **info**, or click **change info age** to change **age**, the **info** registered \@Watch callback is triggered. When you click **change numArr[2]** to change the third element in **numArr**, or click **change numArr[3]** to change the fourth element, the **numArr** registered \@Watch callback is triggered. In these two callbacks, the value before data change cannot be obtained. This makes it inconvenient for you to listen for the variable changes because you cannot find out which property or element is changed to trigger \@Watch event in a more complex scenario. Therefore, the \@Monitor decorator comes into the picture to listen for the changes of an object, a single property in an array, or an array item and obtain the value before change.

## Decorator Description

| \@Monitor Property Decorator| Description                                                        |
| ------------------- | ------------------------------------------------------------ |
| Parameters         | Object property name of the string type. This decorator can listen for multiple object properties at the same time. Each property is separated by commas (,), for example, @Monitor('prop1', 'prop2'). In addition, properties such as an element in a multi-dimensional array, a property in a nested object, and a property in an object array can be listened in a lower level. For details, see [Listened Changes](#listened-changes).|
| Decorated object           | \@Monitor decorated member method. This callback is triggered when the listened property changes. The callback method takes a variable of the [IMonitor type](../../reference/apis-arkui/arkui-ts/ts-state-management-watch-monitor.md#imonitor12) as a parameter, from which you can retrieve information before and after the change.|

## Available APIs

For details about the APIs of the IMonitor and IMonitorValue\<T\> types, see [State Variable Change Listening](../../reference/apis-arkui/arkui-ts/ts-state-management-watch-monitor.md).

## Listened Changes

### Using \@Monitor in Custom Components Decorated by \@ComponentV2

When the state variables listened by \@Monitor change, the callback is triggered.

- Variables listened by \@Monitor need to be decorated by \@Local, \@Param, \@Provider, \@Consumer, and \@Computed. Otherwise, they cannot be listened when they change. \@Monitor can listen for multiple state variables at the same time. Names of these variables are separated by commas (,).

  <!-- @[monitor_decorator_multi_watch_comp_v2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorDecoratorMultiWatchCompV2.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  @Entry
  @ComponentV2
  struct Index {
    @Local message: string = 'Hello World';
    @Local name: string = 'Tom';
    @Local age: number = 24;
  
    @Monitor('message', 'name')
    onStrChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        hilog.info(0xFF00, 'testTag', '%{public}s',
          `${path} changed from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
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

- When the state variable listened by \@Monitor is a class object, only the overall object changes can be listened. To listen for the changes of a class property, this property should be decorated by \@Trace.

  <!-- @[monitor_decorator_object_trace_comp_v2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorDecoratorObjectTraceCompV2.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  class Info {
    public name: string;
    public age: number;
  
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
      hilog.info(0xFF00, 'testTag', '%{public}s', `info change`);
    }
  
    @Monitor('info.name')
    infoPropertyChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s', `info name change`);
    }
  
    build() {
      Column() {
        Text(`name: ${this.info.name}, age: ${this.info.age}`)
        Button('change info')
          .onClick(() => {
            this.info = new Info('Lucy', 18); // Can listen for the change.
          })
        Button('change info.name')
          .onClick(() => {
            this.info.name = 'Jack'; // Cannot listen for the change.
          })
      }
    }
  }
  ```

### Using \@Monitor in Classes Decorated by \@ObservedV2

When the properties listened by \@Monitor change, the callback is triggered.

- The object property listened by \@Monitor should be decorated by \@Trace. Otherwise, the property cannot be listened. \@Monitor can listen for multiple properties at the same time. These properties are separated by commas (,).
  <!-- @[monitor_decorator_multi_watch_observed_v2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorDecoratorMultiWatchObservedV2.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  @ObservedV2
  class Info {
    @Trace public name: string = 'Tom';
    @Trace public region: string = 'North';
    @Trace public job: string = 'Teacher';
    public age: number = 25;
  
    // name is decorated by @Trace. Can listen for the change.
    @Monitor('name')
    onNameChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s',
        `name change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
  
    // age is not decorated by @Trace. Cannot listen for the change.
    @Monitor('age')
    onAgeChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s',
        `age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
  
    // region and job are decorated by @Trace. Can listen for the change.
    @Monitor('region', 'job')
    onChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        hilog.info(0xFF00, 'testTag', '%{public}s',
          `${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
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
            this.info.name = 'Jack'; // Can trigger the onNameChange method.
          })
        Button('change age')
          .onClick(() => {
            this.info.age = 26; // Cannot trigger the onAgeChange method.
          })
        Button('change region')
          .onClick(() => {
            this.info.region = 'South'; // Can trigger the onChange method.
          })
        Button('change job')
          .onClick(() => {
            this.info.job = 'Driver'; // Can trigger the onChange method.
          })
      }
    }
  }
  ```

- \@Monitor can listen for the changes of lower-level properties which should be decorated by @Trace.
  <!-- @[monitor_decorator_object_trace_observed_v2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorDecoratorObjectTraceObservedV2.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  @ObservedV2
  class Inner {
    @Trace public num: number = 0;
  }
  
  @ObservedV2
  class Outer {
    public inner: Inner = new Inner();
  
    @Monitor('inner.num')
    onChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s',
        `inner.num change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
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
            this.outer.inner.num = 100; // Can trigger the onChange method.
          })
      }
    }
  }
  ```

- In the inheritance class scenario, you can listen for the same property for multiple times in the inheritance chain.
  <!-- @[monitor_decorator_inheritance_support_observed_v2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorDecoratorInheritanceSupportObservedV2.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  @ObservedV2
  class Base {
    @Trace public name: string;
  
    // Listen for the name property of the base class.
    @Monitor('name')
    onBaseNameChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s', `Base Class name change`);
    }
  
    constructor(name: string) {
      this.name = name;
    }
  }
  
  @ObservedV2
  class Derived extends Base {
    // Listen for the name property of the inheritance class.
    @Monitor('name')
    onDerivedNameChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s', `Derived Class name change`);
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
            this.derived.name = 'BBB'; // Can trigger the onBaseNameChange and onDerivedNameChange methods in sequence.
          })
      }
    }
  }
  ```

### General Listening Capability

\@Monitor also has some general listening capabilities.

- \@Monitor can listen for items in arrays, including multi-dimensional arrays and object arrays. \@Monitor cannot listen for changes caused by calling APIs of built-in types (Array, Map, Date, and Set). When \@Monitor listens for the entire array, only the value changes to the entire array can be observed. But you can listen for the length change of the array to determine whether the array is inserted or deleted. Currently, only periods (.) can be used to listen for lower-level properties and array items.
  <!-- @[monitor_decorator_array_support](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorDecoratorArraySupport.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  @ObservedV2
  class Info {
    @Trace public name: string;
    @Trace public age: number;
  
    constructor(name: string, age: number) {
      this.name = name;
      this.age = age;
    }
  }
  
  @ObservedV2
  class ArrMonitor {
    @Trace public dimensionTwo: number[][] = [[1, 1, 1], [2, 2, 2], [3, 3, 3]];
    @Trace public dimensionThree: number[][][] = [[[1], [2], [3]], [[4], [5], [6]], [[7], [8], [9]]];
    @Trace public infoArr: Info[] = [new Info('Jack', 24), new Info('Lucy', 18)];
  
    // dimensionTwo is a two-dimensional simple array and is decorated by @Trace. Can observe the element changes.
    @Monitor('dimensionTwo.0.0', 'dimensionTwo.1.1')
    onDimensionTwoChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        hilog.info(0xFF00, 'testTag', '%{public}s',
          `dimensionTwo path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      })
    }
  
    // dimensionThree is a three-dimensional simple array and is decorated by @Trace. Can observe the element changes.
    @Monitor('dimensionThree.0.0.0', 'dimensionThree.1.1.0')
    onDimensionThreeChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        hilog.info(0xFF00, 'testTag', '%{public}s',
          `dimensionThree path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      })
    }
  
    // name and age properties of the info class are decorated by @Trace. Can listen for the change.
    @Monitor('infoArr.0.name', 'infoArr.1.age')
    onInfoArrPropertyChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        hilog.info(0xFF00, 'testTag', '%{public}s',
          `infoArr path:${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      })
    }
  
    // infoArr is decorated by @Trace. Can listen for the value changes.
    @Monitor('infoArr')
    onInfoArrChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s', `infoArr whole change`);
    }
  
    // Can listen for the length change of the infoArr.
    @Monitor('infoArr.length')
    onInfoArrLengthChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s', `infoArr length change`);
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
            // Can trigger the onDimensionTwoChange method.
            this.arrMonitor.dimensionTwo[0][0]++;
            this.arrMonitor.dimensionTwo[1][1]++;
          })
        Button('Change dimensionThree')
          .onClick(() => {
            // Can trigger the onDimensionThreeChange method.
            this.arrMonitor.dimensionThree[0][0][0]++;
            this.arrMonitor.dimensionThree[1][1][0]++;
          })
        Button('Change info property')
          .onClick(() => {
            // Can trigger the onInfoArrPropertyChange method.
            this.arrMonitor.infoArr[0].name = 'Tom';
            this.arrMonitor.infoArr[1].age = 19;
          })
        Button('Change whole infoArr')
          .onClick(() => {
            // Can trigger the onInfoArrChange, onInfoArrPropertyChange, and onInfoArrLengthChange methods.
            this.arrMonitor.infoArr = [new Info('Cindy', 8)];
          })
        Button('Push new info to infoArr')
          .onClick(() => {
            // Can trigger the onInfoArrPropertyChange and onInfoArrLengthChange methods.
            this.arrMonitor.infoArr.push(new Info('David', 50));
          })
      }
    }
  }
  ```

- When the entire object changes but the listened property remains unchanged, the \@Monitor callback is not triggered.

  The following code represents the behavior in the comment when you execute the instructions in the sequence of Step 1, Step 2 and Step 3.

  If you only execute the instruction of Step 2 or Step 3 to change the values of **name** or **age**, the **onNameChange** and **onAgeChange** methods are triggered.
  <!-- @[monitor_decorator_object_support](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorDecoratorObjectSupport.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  @ObservedV2
  class Info {
    @Trace public person: Person;
  
    @Monitor('person.name')
    onNameChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s',
        `name change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
  
    @Monitor('person.age')
    onAgeChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s',
        `age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
  
    constructor(name: string, age: number) {
      this.person = new Person(name, age);
    }
  }
  
  @ObservedV2
  class Person {
    @Trace public name: string;
    @Trace public age: number;
  
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
            this.info.person = new Person('Jack', 25); // Can trigger the onNameChange method, but not the onAgeChange method.
          })
        Button('Step2: Only change age')
          .onClick(() => {
            this.info.person = new Person('Jack', 18); // Can trigger the onAgeChange method, but not the onNameChange method.
          })
        Button('Step3: Change name and age')
          .onClick(() => {
            this.info.person = new Person('Lucy', 19); // Can trigger the onNameChange and onAgeChange methods.
          })
      }
    }
  }
  ```

- If the property listened by \@Monitor is changed for multiple times in an event, the last change is used.
  <!-- @[monitor_decorator_last_write](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorDecoratorLastWrite.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  @ObservedV2
  class Frequency {
    @Trace public count: number = 0;
  
    @Monitor('count')
    onCountChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s',
        `count change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
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
            this.frequency.count = 1000; // Cannot trigger the onCountChange method at last.
          })
      }
    }
  }
  ```

After you click **change count to 1000**, the **onCountChange** method is triggered and the **count change from 0 to 1000** log is output. After you click **change count to 0 then to 1000**, the **onCountChange** method is not triggered because the value of **count** property remains 1000 before and after the event.

## Constraints

Pay attention to the following constraints when using \@Monitor:

- Do not listen for the same property for multiple times in a class. When a property in a class is listened for multiple times, only the last listening method takes effect.
  <!-- @[monitor_limitation_last_listener_wins](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorLimitationLastListenerWins.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  @ObservedV2
  class Info {
    @Trace public name: string = 'Tom';
  
    @Monitor('name')
    onNameChange(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s', `onNameChange`);
    }
  
    @Monitor('name')
    onNameChangeDuplicate(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s', `onNameChangeDuplicate`);
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
            this.info.name = 'Jack'; // Only the onNameChangeDuplicate method is triggered.
          })
      }
    }
  }
  ```

- When @Monitor receives multiple path parameters, the system determines duplicate observation based on the full combination result of the parameters. Spaces are added between parameters during full combination to distinguish them. For example, the full combination of 'ab' and 'c' is 'ab c', while 'a' and 'bc' becomes 'a bc'. These results are not equal. In the following example, Monitor 1, Monitor 2, and Monitor 3 all observe the name attribute. The input parameters of Monitor 2 and Monitor 3 are the same (name position), so only Monitor 3 takes effect. When name changes, both onNameAgeChange and onNamePositionChangeDuplicate are triggered simultaneously. However, note that Monitor 2 and Monitor 3 implementations are still considered multiple @Monitor observations of the same attribute in the same class, which is not recommended.
  <!-- @[monitor_limitation_multiple_path_params](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorLimitationMultiplePathParams.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  @ObservedV2
  class Info {
    @Trace public name: string = 'Tom';
    @Trace public age: number = 25;
    @Trace public position: string = 'North';
  
    @Monitor('name', 'age') // Monitor 1
    onNameAgeChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        hilog.info(0xFF00, 'testTag', '%{public}s',
          `onNameAgeChange path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      });
    }
  
    @Monitor('name', 'position') // Monitor 2
    onNamePositionChange(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        hilog.info(0xFF00, 'testTag', '%{public}s',
          `onNamePositionChange path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
      });
    }
  
    // name and position are observed repeatedly. Only the last definition takes effect
    @Monitor('name', 'position') // Monitor3
    onNamePositionChangeDuplicate(monitor: IMonitor) {
      monitor.dirty.forEach((path: string) => {
        hilog.info(0xFF00, 'testTag', '%{public}s',
          `onNamePositionChangeDuplicate path: ${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
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

- The \@Monitor parameter must be a string that listens for the property name. Only string literals, **const** constants, and **enum** enumerated values can be used as parameters. If a variable is used as a parameter, only the property corresponding to the variable value during \@Monitor initialization is listened. When a variable is changed, \@Monitor cannot change the listened property in real time. That is, the target property listened by \@Monitor is determined during initialization and cannot be dynamically changed. Do not use variables as \@Monitor parameters for initialization.

  <!-- @[monitor_limitation_parameter_string_constraint](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorLimitationParameterStringConstraint.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  
  const t2: string = 't2'; // Constant
  
  enum ENUM {
    T3 = 't3' // Enum
  };
  let t4: string = 't4'; // Variable
  
  @ObservedV2
  class Info {
    @Trace public t1: number = 0;
    @Trace public t2: number = 0;
    @Trace public t3: number = 0;
    @Trace public t4: number = 0;
    @Trace public t5: number = 0;
  
    // String literal
    @Monitor('t1')
    onT1Change(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s', `t1 change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
  
    @Monitor(t2)
    onT2Change(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s', `t2 change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
  
    @Monitor(ENUM.T3)
    onT3Change(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s', `t3 change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
  
    @Monitor(t4)
    onT4Change(monitor: IMonitor) {
      hilog.info(0xFF00, 'testTag', '%{public}s', `t4 change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
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
            this.info.t1++; // Can trigger the onT1Change method.
          })
        Button('Change t2')
          .onClick(() => {
            this.info.t2++; // Can trigger the onT2Change method.
          })
        Button('Change t3')
          .onClick(() => {
            this.info.t3++; // Can trigger the onT3Change method.
          })
        Button('Change t4')
          .onClick(() => {
            this.info.t4++; // Can trigger the onT4Change method.
          })
        Button('Change var t4 to t5')
          .onClick(() => {
            t4 = 't5'; // Change the variable value to "t5".
          })
        Button('Change t5')
          .onClick(() => {
            this.info.t5++; // The onT4Change still listens for t4. Cannot trigger the method.
          })
        Button('Change t4 again')
          .onClick(() => {
            this.info.t4++; // Can trigger the onT4Change method.
          })
      }
    }
  }
  ```

- Changing the listened property in \@Monitor again may cause infinite loops, which is not recommended.

  ```ts
  @ObservedV2
  class Info {
    @Trace count: number = 0;
    @Monitor('count')
    onCountChange(monitor: IMonitor) {
      this.count++; // Avoid using this method because it may cause infinite loops.
    }
  }
  ```

## Comparing \@Monitor with \@Watch

The following table compares the usage and functions of \@Monitor and \@Watch.

| Usage              | \@Watch                                   | \@Monitor                                                    |
| ------------------ | ----------------------------------------- | ------------------------------------------------------------ |
| Parameter              | Callback method name.                             | Listened state variable name and property name.                                    |
| Number of listened targets        | A single state variable.                   | Multiple state variables.                                    |
| Listening capability          | Listen for the top-level state variables.           | Listen for the lower-level state variables.                              |
| Obtain the value before change| No.                     | Yes.                                          |
| Listening Condition          | The listened object is a state variable.                     | The listened object is a state variable or a class member property decorated by \@Trace.             |
| Constraints          | Used only in \@Component decorated custom components.| Used in \@ComponentV2 decorated custom components and \@ObservedV2 decorated classes.|

## When to Use

### Listening for Lower-level Property Changes

\@Monitor can listen for the lower-level property changes and classify them based on the values before and after the changes.

In the following example, the change of property **value** is listened and the display style of the **Text** component is changed based on the change amplitude.

<!-- @[monitor_scene_deep_attribute_changes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorSceneDeepAttributeChanges.ets) -->

``` TypeScript
@ObservedV2
class Info {
  @Trace public value: number = 50;
}

@ObservedV2
class UIStyle {
  public info: Info = new Info();
  @Trace public color: Color = Color.Black;
  @Trace public fontSize: number = 45;

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

## Common Issue

### Effective and Expiration Time of Variable Listening by the \@Monitor in the Custom Component

When \@Monitor is defined in a custom component decorated by \@ComponentV2, \@Monitor takes effect after the state variable is initialized and becomes invalid when the component is destroyed.

<!-- @[monitor_problem_effect_time_comp_v2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorProblemEffectTimeCompV2.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@ObservedV2
class Info {
  @Trace public message: string = 'not initialized';

  constructor() {
    hilog.info(0xFF00, 'testTag', '%{public}s', 'in constructor message change to initialized');
    this.message = 'initialized';
  }
}

@ComponentV2
struct Child {
  @Param info: Info = new Info();

  @Monitor('info.message')
  onMessageChange(monitor: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s',
      `Child message change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }

  aboutToAppear(): void {
    this.info.message = 'Child aboutToAppear';
  }

  aboutToDisappear(): void {
    hilog.info(0xFF00, 'testTag', '%{public}s', 'Child aboutToDisappear');
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
    hilog.info(0xFF00, 'testTag', '%{public}s',
      `Index message change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
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

In the preceding example, you can create and destroy a **Child** component to observe the effective and expiration time of the \@Monitor defined in the custom component. You are advised to follow the steps below:

- When the **Index** component creates an instance of the **Info** class, the log outputs the message: **in constructor message change to initialized**. At this time, the \@Monitor of the **Index** component has not been initialized successfully, so \@Monitor cannot listen for the message change.
- After the **Index** component is created and the page is loaded, click **change message in Index** button. \@Monitor now can listen for the change and the log outputs the message "Index message change from initialized to Index click to change Message".
- Click the **show/hide Child** button to create a **Child** component. After this component initializes the \@Param decorated variables and \@Monitor, call the **aboutToAppear** callback of the **Child** component to change the message. In this case, the \@Monitor of the **Index** and **Child** components can listen for the change, and the logs outputs the messages "Index message change from Index click to change Message to Child aboutToAppear" and "Child message change from Index click to change Message to Child aboutToAppear."
- Click **change message in Child** button to change the message. In this case, the \@Monitor of the **Index** and **Child** components can listen for the change, and the log outputs the messages "Index message change from Child aboutToAppear to Child click to change Message" and "Child message change from Child aboutToAppear to Child click to change Message."
- Click the **show/hide Child** button to destroy the **Child** component and call the **aboutToDisappear** callback to change the message. In this case, the \@Monitor of the **Index** and **Child** components can listen for the change, and the log outputs the messages "Child aboutToDisappear, Index message change from Child click to change Message to Child aboutToDisappear", and "Child message change from Child click to change Message to Child aboutToDisappear."
- Click **change message in Index** button to change the message. In this case, the **Child** component is destroyed, and the \@Monitor is deregistered. Only the \@Monitor of the **Index** component can listen for the changes and the log outputs the message "Index message change from Child aboutToDisappear to Index click to change Message."

The preceding steps indicate that the \@Monitor defined in the **Child** component takes effect when the **Child** component is created and initialized, and becomes invalid when the **Child** component is destroyed.

### Effective and Expiration Time of Variable Listening by the \@Monitor in the Class

When \@Monitor is defined in class decorated with \@ObservedV2, it takes effect after the class instance is created and becomes invalid when the class instance is destroyed.

<!-- @[monitor_problem_effect_time_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorProblemEffectTimeClass.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@ObservedV2
class Info {
  @Trace public message: string = 'not initialized';

  constructor() {
    this.message = 'initialized';
  }

  @Monitor('message')
  onMessageChange(monitor: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s',
      `message change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
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

In the preceding example, \@Monitor takes effect after the **info** class is created, which is later than the **constructor** of the class and earlier than the **aboutToAppear** of the custom component. After the page is loaded, click **change message** button to modify the message variable. The log outputs the messages as below:

```ts
message change from initialized to Index aboutToAppear
message change from Index aboutToAppear to Index click to change message
```

\@Monitor defined in a class becomes invalid when the class is destroyed. However, the garbage collection mechanism determines whether a class is actually destroyed and released. Even if the custom component is destroyed, the class is not destroyed accordingly. As a result, the \@Monitor defined in the class still listens for changes.

<!-- @[monitor_problem_class_delayed](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorProblemClassDelayed.ets) --> 

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@ObservedV2
class InfoWrapper {
  public info?: Info;

  constructor(info: Info) {
    this.info = info;
  }

  @Monitor('info.age')
  onInfoAgeChange(monitor: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s',
      `age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
}

@ObservedV2
class Info {
  @Trace public age: number;

  constructor(age: number) {
    this.age = age;
  }
}

@ComponentV2
struct Child {
  @Param @Require infoWrapper: InfoWrapper;

  aboutToDisappear(): void {
    hilog.info(0xFF00, 'testTag', '%{public}s', 'Child aboutToDisappear', this.infoWrapper.info?.age);
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
          hilog.info(0xFF00, 'testTag', '%{public}s', 'click to change age');
          this.dataArray.forEach((info: Info) => {
            info.age += 100;
          });
        })
      if (this.showFlag) {
        Column() {
          Text('Children')
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

In the preceding example, when you click **change showFlag** to switch the condition of the **if** component, the **Child** component is destroyed. But when you click **change number** to change the value of **age**, the \@Monitor callback defined in **InfoWrapper** is still triggered. This is because the custom component **Child** has executed **aboutToDisappear**, but its member variable **infoWrapper** is not destroyed immediately. When the variable changes, the **onInfoAgeChange** method defined in **infoWrapper** can still be called, therefore, the \@Monitor callback is still triggered.

The result is unstable when you use the garbage collection mechanism to cancel the listening of \@Monitor. You can use either of the following methods to manage the expiration time of the \@Monitor:

1. Define \@Monitor in the custom component. When a custom component is destroyed, the state management framework cancels the listening of \@Monitor. Therefore, after the custom component calls **aboutToDisappear**, the \@Monitor callback will not be triggered even though the data of the custom component may not be released.

<!-- @[monitor_problem_class_failure_time_set_comp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorProblemClassFailureTimeSetComp.ets) --> 

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@ObservedV2
class InfoWrapper {
  public info?: Info;

  constructor(info: Info) {
    this.info = info;
  }
}

@ObservedV2
class Info {
  @Trace public age: number;

  constructor(age: number) {
    this.age = age;
  }
}

@ComponentV2
struct Child {
  @Param @Require infoWrapper: InfoWrapper;

  @Monitor('infoWrapper.info.age')
  onInfoAgeChange(monitor: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s',
      `age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }

  aboutToDisappear(): void {
    hilog.info(0xFF00, 'testTag', '%{public}s', 'Child aboutToDisappear', this.infoWrapper.info?.age);
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
          hilog.info(0xFF00, 'testTag', '%{public}s', 'click to change age');
          this.dataArray.forEach((info: Info) => {
            info.age += 100;
          })
        })
      if (this.showFlag) {
        Column() {
          Text('Children')
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

2. Set the listened object to empty. When the custom component is about to be destroyed, the \@Monitor listened object is set empty. In this way, the \@Monitor cannot listen for the changes of the original object, so that the listening is cancelled.

<!-- @[monitor_problem_class_failure_time_empty_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorProblemClassFailureTimeEmptyObject.ets) --> 

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@ObservedV2
class InfoWrapper {
  public info?: Info;

  constructor(info: Info) {
    this.info = info;
  }

  @Monitor('info.age')
  onInfoAgeChange(monitor: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s',
      `age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
}

@ObservedV2
class Info {
  @Trace public age: number;

  constructor(age: number) {
    this.age = age;
  }
}

@ComponentV2
struct Child {
  @Param @Require infoWrapper: InfoWrapper;

  aboutToDisappear(): void {
    hilog.info(0xFF00, 'testTag', '%{public}s', 'Child aboutToDisappear', this.infoWrapper.info?.age);
    this.infoWrapper.info = undefined; // Disable the InfoWrapper from listening for info.age.
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
          hilog.info(0xFF00, 'testTag', '%{public}s', 'click to change age');
          this.dataArray.forEach((info: Info) => {
            info.age += 100;
          })
        })
      if (this.showFlag) {
        Column() {
          Text('Children')
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

\@Monitor cannot verify input parameters during compilation. Currently, the following statements do not meet the listening condition, but \@Monitor is still triggered. Developers must correctly pass \@Monitor input parameters and avoid passing non-state variables to prevent function exceptions or unexpected behavior.

[Incorrect Usage 1]

<!-- @[monitor_problem_param_counter_example_1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorProblemParamCounterExample1.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@ObservedV2
class Info {
  public name: string = 'John';
  @Trace public age: number = 24;

  // Observe both state variable age and non-state variable name
  @Monitor('age', 'name')
  onPropertyChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      hilog.info(0xFF00, 'testTag', '%{public}s',
        `property path:${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
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
          this.info.age = 25; // Change both state variable age and non-state variable name.
          this.info.name = 'Johny';
        })
    }
  }
}
```

In the preceding code, when state variable **age** and non-state variable **name** are changed at the same time, the following log is generated:

```text
property path:age change from 24 to 25
property path:name change from John to Johny
```

Actually, the **name** attribute is not an observable variable and should not be added to the input parameters of \@Monitor. You are advised to remove the listening from the **name** attribute or use \@Trace to decorate the **name** attribute as a state variable.

[Correct Usage 1]

<!-- @[monitor_problem_param_positive_example_1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorProblemParamPositiveExample1.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@ObservedV2
class Info {
  public name: string = 'John';
  @Trace public age: number = 24;

  // Observe only the state variable age
  @Monitor('age')
  onPropertyChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      hilog.info(0xFF00, 'testTag', '%{public}s',
        `property path:${path} change from ${monitor.value(path)?.before} to ${monitor.value(path)?.now}`);
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
          this.info.age = 25; // The state variable "age" is changed.
          this.info.name = 'Johny';
        })
    }
  }
}
```

[Negative example 2]

<!-- @[monitor_problem_param_counter_example_2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorProblemParamCounterExample2.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@ObservedV2
class Info {
  public name: string = 'John';
  @Trace public age: number = 24;

  get myAge() {
    return this.age; // age is a state variable.
  }

  // Observe a getter accessor not decorated with @Computed
  @Monitor('myAge')
  onPropertyChange() {
    hilog.info(0xFF00, 'testTag', '%{public}s', 'age changed');
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
          this.info.age = 25; // The state variable "age" is changed.
        })
    }
  }
}
```

In the preceding code, the input parameter of \@Monitor is the name of a **getter** accessor. This accessor is not decorated by \@Computed and is not a variable that can be listened for. However, the state variable is used for computation. After the state variable changes, **myAge** is changed, invoking the \@Monitor callback. You are advised to add an \@Computed decorator to **myAge** or directly listen for the state variable itself when the **getter** accessor returns the state variable.

[Correct Usage 2]

Change **myAge** to a state variable:
<!-- @[monitor_problem_param_positive_example_2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorProblemParamPositiveExample2.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@ObservedV2
class Info {
  public name: string = 'John';
  @Trace public age: number = 24;

  // Add @Computed to make myAge a state variable
  @Computed
  get myAge() {
    return this.age;
  }

  // Observe the @Computed-decorated getter accessor
  @Monitor('myAge')
  onPropertyChange() {
    hilog.info(0xFF00, 'testTag', '%{public}s', 'age changed');
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
          this.info.age = 25; // The state variable "age" is changed.
        })
    }
  }
}
```

Alternatively, listen to the state variable itself.
<!-- @[monitor_problem_param_state_variables](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorProblemParamStateVariables.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@ObservedV2
class Info {
  public name: string = 'John';
  @Trace public age: number = 24;

  // Observe the state variable age directly
  @Monitor('age')
  onPropertyChange() {
    hilog.info(0xFF00, 'testTag', '%{public}s', 'age changed');
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
          this.info.age = 25; // The state variable "age" is changed.
        })
    }
  }
}
```

### Variables Cannot Be Observed During Accessibility Changes
\@Monitor only saves values when variables are accessible. When a state variable becomes inaccessible, value changes aren't recorded. In the following example, clicking any of the three buttons does not trigger the onChange callback.

Since API version 20, If you need to observe accessibility changes (from accessible to inaccessible or vice versa), use [addMonitor](./arkts-new-addMonitor-clearMonitor.md#listening-for-variable-accessibility-changes).

<!-- @[monitor_problem_state_change_use_addMonitor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/monitor/MonitorProblemStateChangeUseAddMonitor.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

@ObservedV2
class User {
  @Trace public age: number = 10;
}

@Entry
@ComponentV2
struct Page {
  @Local user: User | undefined | null = new User();

  @Monitor('user.age')
  onChange(mon: IMonitor) {
    mon.dirty.forEach((path: string) => {
      hilog.info(0xFF00, 'testTag', '%{public}s',
        `onChange: User property ${path} change from ${mon.value(path)?.before} to ${mon.value(path)?.now}`);
    });
  }

  build() {
    Column() {
      Text(`User age ${this.user?.age}`).fontSize(20)
      Button('set user to undefined').onClick(() => {
        // age: from accessible to inaccessible
        this.user = undefined;
      })
      Button('set user to User').onClick(() => {
        // age: from inaccessible to accessible
        this.user = new User();
      })
      Button('set user to null').onClick(() => {
        // age: from accessible to inaccessible
        this.user = null;
      })
    }
  }
}
```
