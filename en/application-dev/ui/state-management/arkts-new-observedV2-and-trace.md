# \@ObservedV2 and \@Trace Decorators: Observing Class Property Changes
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

To enable the state management framework to observe properties in class objects, you can use the \@ObservedV2 and \@Trace decorators to decorate classes and properties in classes.


\@ObservedV2 and \@Trace provide the capability of directly observing the property changes of nested objects. They are one of the core capabilities of state management V2. Before reading this topic, you are advised to read [State Management Overview](./arkts-state-management-overview.md) to have a basic understanding of the overall capability architecture of state management V2.

>**NOTE**
>
> The \@ObservedV2 and \@Trace decorators are supported since API version 12.
>
> The \@ObservedV2 and \@Trace decorators can be used in ArkTS widgets since API version 12.
>
> The \@ObservedV2 and \@Trace decorators can be used in atomic services since API version 12.

## Overview

The \@ObservedV2 and \@Trace decorators are used to decorate classes and properties in classes so that changes to the classes and properties can be observed.

- \@ObservedV2 and \@Trace must come in pairs. Using either of them alone does not work.
- When a property decorated with \@Trace changes, only the component bound to that property will re-render.
- In a nested class, changes to a property trigger UI re-rendering only when the property is decorated with \@Trace and the class is decorated with \@ObservedV2.
- In an inherited class, changes to a property of the parent or child class trigger UI re-rendering only when the property is decorated with \@Trace and the owning class is decorated with \@ObservedV2.
- Attributes that are not decorated by \@Trace cannot detect changes nor trigger UI re-renders.
- Classes decorated with \@ObservedV2 and \@Trace must be instantiated using the **new** operator to have change observation capabilities.

## Limitations of State Management V1 on Observability of Properties in Nested Class Objects

With state management V1, properties of nested class objects are not directly observable.

<!-- @[Observed_Limitations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/overview/Limitations.ets) -->

``` TypeScript
@Observed
class Father {
  public son: Son;

  constructor(name: string, age: number) {
    this.son = new Son(name, age);
  }
}

@Observed
class Son {
  public name: string;
  public age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

@Entry
@Component
struct Index {
  @State father: Father = new Father('John', 8);

  build() {
    Row() {
      Column() {
        Text(`name: ${this.father.son.name} age: ${this.father.son.age}`)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            this.father.son.age++;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```


In the preceding example, clicking the **Text** component increases the value of **age**, but does not trigger UI re-renders. The reason is that the **age** property in a nested class is not observable to the current state management framework. To resolve this issue, state management V1 uses [\@ObjectLink](arkts-observed-and-objectlink.md) with custom components.

<!-- @[Realize_Observation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/overview/RealizeObservation.ets) -->

``` TypeScript
@Observed
class Father {
  public son: Son;

  constructor(name: string, age: number) {
    this.son = new Son(name, age);
  }
}

@Observed
class Son {
  public name: string;
  public age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

@Component
struct Child {
  @ObjectLink son: Son;

  build() {
    Row() {
      Column() {
        Text(`name: ${this.son.name} age: ${this.son.age}`)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            this.son.age++;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}

@Entry
@Component
struct Index {
  @State father: Father = new Father('John', 8);

  build() {
    Column() {
      Child({ son: this.father.son })
    }
  }
}
```


Yet, this approach has its drawbacks: If the nesting level is deep, the code becomes unnecessarily complicated and the usability poor. This is where the class decorator \@ObservedV2 and member property decorator \@Trace come into the picture.

## Decorator Description

| \@ObservedV2 Decorator| Description                                                 |
| ------------------ | ----------------------------------------------------- |
| Parameters        | N/A                                                   |
| Class decorator          | Decorates a class. You must use **new** to create a class object before defining the class.|

| \@Trace member property decorator| Description                                                        |
| --------------------- | ------------------------------------------------------------ |
| Parameters           | N/A                                                          |
| Supported type         | Member properties in classes in any of the following types: Member properties in classes in any of the following types: number, string, boolean, class, [Array](#decorating-an-array-of-a-built-in-type-with-trace), [Date](#decorating-a-property-of-the-date-type-with-trace), [Map](#decorating-a-property-of-the-map-type-with-trace), and [Set](#decorating-a-property-of-the-set-type-with-trace). \@Trace does not support the observation of data of the function type. If the data of the function type decorated by \@Trace is modified, the UI is not refreshed.|

## Observed Changes

In classes decorated by \@ObservedV2, properties decorated by \@Trace are observable. This means that, any of the following changes can be observed and will trigger UI re-renders of bound components:

- Changes to properties decorated by \@Trace in nested classes decorated by \@ObservedV2

<!-- @[Observe_Changes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/overview/ObserveChanges.ets) -->

``` TypeScript
@ObservedV2
class Son {
  @Trace public age: number = 100;
}

class Father {
  public son: Son = new Son();
}

@Entry
@ComponentV2
struct Index {
  father: Father = new Father();

  build() {
    Column() {
      // If age is changed, the Text component is re-rendered.
      Text(`${this.father.son.age}`)
        .onClick(() => {
          this.father.son.age++;
        })
    }
  }
}
```

- Changes to properties decorated by \@Trace in inherited classes decorated by \@ObservedV2

<!-- @[Inherited_Changes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/overview/InheritedChanges.ets) -->

``` TypeScript
@ObservedV2
class Father {
  @Trace public name: string = 'Tom';
}

class Son extends Father {
}

@Entry
@ComponentV2
struct Index {
  son: Son = new Son();

  build() {
    Column() {
      // If name is changed, the Text component is re-rendered.
      Text(`${this.son.name}`)
        .onClick(() => {
          this.son.name = 'Jack';
        })
    }
  }
}
```

- Changes to static properties decorated by \@Trace in classes decorated by \@ObservedV2

<!-- @[Static_Attribute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/overview/StaticAttribute.ets) -->

``` TypeScript
@ObservedV2
class Manager {
  @Trace public static count: number = 1;
}

@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      // If count is changed, the Text component is re-rendered.
      Text(`${Manager.count}`)
        .onClick(() => {
          Manager.count++;
        })
    }
  }
}
```

- Changes caused by the APIs listed below to properties of built-in types decorated by \@Trace

  | Type | Change-Triggering API                                             |
  | ----- | ------------------------------------------------------------ |
  | Array | push, pop, shift, unshift, splice, copyWithin, fill, reverse, sort|
  | Date  | setFullYear, setMonth, setDate, setHours, setMinutes, setSeconds, setMilliseconds, setTime, setUTCFullYear, setUTCMonth, setUTCDate, setUTCHours, setUTCMinutes, setUTCSeconds, setUTCMilliseconds |
  | Map   | set, clear, delete                                           |
  | Set   | add, clear, delete                                           |

## Usage restriction

Note the following constraints when using the \@ObservedV2 and \@Trace decorators:

- The member property that is not decorated by \@Trace cannot trigger UI re-renders.

<!-- @[UiRefresh_CannotTriggered](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/usagerestrictions/UiRefreshCannotTriggered.ets) -->

``` TypeScript
@ObservedV2
class Person {
  public id: number = 0;
  @Trace public age: number = 8;
}

@Entry
@ComponentV2
struct Index {
  person: Person = new Person();

  build() {
    Column() {
      // age is decorated by @Trace and can trigger re-renders when used in the UI.
      Text(`${this.person.age}`)
        .onClick(() => {
          this.person.age++; // The click event can trigger a UI re-render.
        })
      // id is not decorated by @Trace and cannot trigger re-renders when used in the UI.
      Text(`${this.person.id}`) // UI is not re-rendered when id changes.
        .onClick(() => {
          this.person.id++; // The click event cannot trigger a UI re-render.
        })
    }
  }
}
```

- \@ObservedV2 can decorate only classes.

```ts
@ObservedV2 // Incorrect usage. An error is reported during compilation.
struct Index {
  build() {
  }
}
```

- \@Trace cannot be used in classes that are not decorated by \@ObservedV2.

```ts
class User {
  id: number = 0;
  @Trace name: string = 'Tom'; // Incorrect usage. An error is reported at compile time.
}
```

- \@Trace is a decorator for properties in classes and cannot be used in a struct.

```ts
@ComponentV2
struct Comp {
  @Trace message: string = 'Hello World'; // Incorrect usage. An error is reported at compile time.

  build() {
  }
}
```

- \@ObservedV2 and \@Trace cannot be used together with [\@Observed](arkts-observed-and-objectlink.md) and [\@Track](arkts-track.md).

```ts
@Observed
class User {
  @Trace name: string = 'Tom'; // Incorrect usage. An error is reported at compile time.
}

@ObservedV2
class Person {
  @Track name: string = 'Jack'; // Incorrect usage. An error is reported at compile time.
}
```

- Classes decorated by @ObservedV2 and @Trace cannot be used together with [\@State](arkts-state.md) or other decorators of V1. Otherwise, an error is reported at compile time.

<!-- @[Use_Mixture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/usagerestrictions/UseMixture.ets) -->

``` TypeScript
// @State is used as an example.
@ObservedV2
class Job {
  @Trace public jobName: string = 'Teacher';
}

@ObservedV2
class Info {
  @Trace public name: string = 'Tom';
  @Trace public age: number = 25;
  public job: Job = new Job();
}

@Entry
@ComponentV2
struct Index {
  // @State info: Info = new Info(); As @State is not allowed here, an error is reported at compile time.
  @Local info: Info = new Info();

  build() {
    Column() {
      Text(`name: ${this.info.name}`)
      Text(`age: ${this.info.age}`)
      Text(`jobName: ${this.info.job.jobName}`)
      Button('change age')
        .onClick(() => {
          this.info.age++;
        })
      Button('Change job')
        .onClick(() => {
          this.info.job.jobName = 'Doctor';
        })
    }
  }
}
```

- Classes extended from \@ObservedV2 cannot be used together with [\@State](arkts-state.md) or other decorators of V1. Otherwise, an error is reported during running.

<!-- @[Inheritance_Mixture](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/usagerestrictions/InheritanceMixture.ets) -->

``` TypeScript
// @State is used as an example.
@ObservedV2
class Job {
  @Trace public jobName: string = 'Teacher';
}

@ObservedV2
class Info {
  @Trace public name: string = 'Tom';
  @Trace public age: number = 25;
  public job: Job = new Job();
}

class Message extends Info {
  constructor() {
    super();
  }
}

@Entry
@Component
struct Index {
  // @State message: Message = new Message();  @State is not allowed here, an error is reported during running.
  message: Message = new Message();

  build() {
    Column() {
      Text(`name: ${this.message.name}`)
      Text(`age: ${this.message.age}`)
      Text(`jobName: ${this.message.job.jobName}`)
      Button('change age')
        .onClick(() => {
          this.message.age++;
        })
      Button('Change job')
        .onClick(() => {
          this.message.job.jobName = 'Doctor';
        })
    }
  }
}
```

- Classes decorated with \@ObservedV2 and \@Trace must be instantiated using the **new** operator to have change observation capabilities.
- The class instance of \@ObservedV2 cannot be directly deserialized using JSON.parse (the object obtained by directly deserializing JSON.parse cannot observe attribute changes). You can use the third-party library [class-transformer](https://gitcode.com/openharmony-tpc/openharmony_tpc_samples/tree/master/class-transformer) to deserialize the object and observe attribute changes. For details, see [Serialization and Deserialization of Objects Decorated with \@ObservedV2](#serialization-and-deserialization-of-objects-decorated-with-observedv2).

## When to Use

### Nested Class

In the following example, **Pencil** is the innermost class in the **Son** class. As **Pencil** is decorated by \@ObservedV2 and its **length** property is decorated by \@Trace, changes to **length** can be observed.

The example demonstrates how \@Trace is stacked up against [\@Track](arkts-track.md) and [\@State](arkts-state.md) under the existing state management framework: The @Track decorator offers property-level update capability for classes, but not deep observability; \@State can only observe the changes of the object itself and changes at the first layer; in multi-layer nesting scenarios, you must encapsulate custom components and use [\@Observed](arkts-observed-and-objectlink.md) and [\@ObjectLink](arkts-observed-and-objectlink.md) to observe the changes.

* Click **Button('change length')**, in which **length** is a property decorated by \@Trace. The change of **length** can trigger the re-render of the associated UI component, that is, **UINode (1)**, and output the log "id: 1 renderTimes: x" whose **x** increases according to the number of clicks.
* Because **son** on the custom component **page** is a regular variable, no change is observed for clicks on **Button('assign Son')**.
* Clicks on **Button('assign Son')** and **Button('change length')** do not trigger UI re-renders. The reason is that, the change to **son** is not updated to the bound component.

<!-- @[Nested_Class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/usagescenarios/NestedClass.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0001;
const TAG = 'ArktsObservedV2AndTrace';

@ObservedV2
class Pencil {
  @Trace public length: number = 21; // If length changes, the bound component is re-rendered.
}

class Bag {
  public width: number = 50;
  public height: number = 60;
  public pencil: Pencil = new Pencil();
}

class Son {
  public age: number = 5;
  public school: string = 'some';
  public bag: Bag = new Bag();
}

@Entry
@ComponentV2
struct Page {
  son: Son = new Son();
  renderTimes: number = 0;

  isRender(id: number): number {
    hilog.info(DOMAIN, TAG, `id: ${id} renderTimes: ${this.renderTimes}`);
    this.renderTimes++;
    return 40;
  }

  build() {
    Column() {
      Text('pencil length' + this.son.bag.pencil.length)
        .fontSize(this.isRender(1)) // UINode (1)
      Button('change length')
        .onClick(() => {
          // The value of length is changed upon a click, which triggers a re-render of UINode (1).
          this.son.bag.pencil.length += 100;
        })
      Button('assign Son')
        .onClick(() => {
          // Changes to the regular variable son do not trigger UI re-renders of UINode (1).
          this.son = new Son();
        })
    }
  }
}
```


### Inheritance

Properties in base or derived classes are observable only when decorated by \@Trace.

In the following example, classes **GrandFather**, **Father**, **Uncle**, **Son**, and **Cousin** are declared. The following figure shows the inheritance relationship.

![arkts-old-state-management](figures/arkts-new-observed-and-track-extend-sample.png)


Create instances of the **Son** and **Cousin** classes. Clicks on **Button('change Son age')** and **Button('change Cousin age')** can trigger UI re-renders.

<!-- @[Inheritance_Class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/usagescenarios/InheritanceClass.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0001;
const TAG = 'ArktsObservedV2AndTrace';

@ObservedV2
class GrandFather {
  @Trace public age: number = 0;

  constructor(age: number) {
    this.age = age;
  }
}

class Father extends GrandFather {
  constructor(father: number) {
    super(father);
  }
}

class Uncle extends GrandFather {
  constructor(uncle: number) {
    super(uncle);
  }
}

class Son extends Father {
  constructor(son: number) {
    super(son);
  }
}

class Cousin extends Uncle {
  constructor(cousin: number) {
    super(cousin);
  }
}

@Entry
@ComponentV2
struct Index {
  son: Son = new Son(0);
  cousin: Cousin = new Cousin(0);
  renderTimes: number = 0;

  isRender(id: number): number {
    hilog.info(DOMAIN, TAG, `id: ${id} renderTimes: ${this.renderTimes}`);
    this.renderTimes++;
    return 40;
  }

  build() {
    Row() {
      Column() {
        Text(`Son ${this.son.age}`)
          .fontSize(this.isRender(1))
          .fontWeight(FontWeight.Bold)
        Text(`Cousin ${this.cousin.age}`)
          .fontSize(this.isRender(2))
          .fontWeight(FontWeight.Bold)
        Button('change Son age')
          .onClick(() => {
            this.son.age++;
          })
        Button('change Cousin age')
          .onClick(() => {
            this.cousin.age++;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```


### Decorating an Array of a Built-in Type with \@Trace

With an array of a built-in type decorated by \@Trace, changes caused by supported APIs can be observed. For details about the supported APIs, see [Observed Changes](#observed-changes).

In the following example, the **numberArr** property in the \@ObservedV2 decorated **Arr** class is an \@Trace decorated array. If an array API is used to operate **numberArr**, the change caused can be observed. Perform length checks on arrays to prevent out-of-bounds access.

<!-- @[Decoration_Foundation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/usagescenarios/DecorationFoundation.ets) -->

``` TypeScript
let nextId: number = 0;

@ObservedV2
class Arr {
  public id: number = 0;
  @Trace public numberArr: number[] = [];

  constructor() {
    this.id = nextId++;
    this.numberArr = [0, 1, 2];
  }
}

@Entry
@ComponentV2
struct Index {
  arr: Arr = new Arr();

  build() {
    Column() {
      Text(`length: ${this.arr.numberArr.length}`)
        .fontSize(40)
      Divider()
      if (this.arr.numberArr.length >= 3) {
        Text(`${this.arr.numberArr[0]}`)
          .fontSize(40)
          .onClick(() => {
            this.arr.numberArr[0]++;
          })
        Text(`${this.arr.numberArr[1]}`)
          .fontSize(40)
          .onClick(() => {
            this.arr.numberArr[1]++;
          })
        Text(`${this.arr.numberArr[2]}`)
          .fontSize(40)
          .onClick(() => {
            this.arr.numberArr[2]++;
          })
      }

      Divider()

      ForEach(this.arr.numberArr, (item: number, index: number) => {
        Text(`${index} ${item}`)
          .fontSize(40)
      })

      Button('push')
        .onClick(() => {
          this.arr.numberArr.push(50);
        })

      Button('pop')
        .onClick(() => {
          this.arr.numberArr.pop();
        })

      Button('shift')
        .onClick(() => {
          this.arr.numberArr.shift();
        })

      Button('splice')
        .onClick(() => {
          this.arr.numberArr.splice(1, 0, 60);
        })


      Button('unshift')
        .onClick(() => {
          this.arr.numberArr.unshift(100);
        })

      Button('copywithin')
        .onClick(() => {
          this.arr.numberArr.copyWithin(0, 1, 2);
        })

      Button('fill')
        .onClick(() => {
          this.arr.numberArr.fill(0, 2, 4);
        })

      Button('reverse')
        .onClick(() => {
          this.arr.numberArr.reverse();
        })

      Button('sort')
        .onClick(() => {
          this.arr.numberArr.sort();
        })
    }
  }
}
```


### Decorating an Object Array with \@Trace

* In the following example, the **personList** object array and the **age** property in the **Person** class are decorated by \@Trace. As such, changes to **personList** and **age** can be observed.
* Clicking the **Text** component changes the value of **age** and thereby triggers a UI re-render of the **Text** component

<!-- @[Decorative_Object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/usagescenarios/DecorativeObject.ets) -->

``` TypeScript
let nextId: number = 0;

@ObservedV2
class Person {
  @Trace public age: number = 0;

  constructor(age: number) {
    this.age = age;
  }
}

@ObservedV2
class Info {
  public id: number = 0;
  @Trace public personList: Person[] = [];

  constructor() {
    this.id = nextId++;
    this.personList = [new Person(0), new Person(1), new Person(2)];
  }
}

@Entry
@ComponentV2
struct Index {
  info: Info = new Info();

  build() {
    Column() {
      Text(`length: ${this.info.personList.length}`)
        .fontSize(40)
      Divider()
      if (this.info.personList.length >= 3) {
        Text(`${this.info.personList[0].age}`)
          .fontSize(40)
          .onClick(() => {
            this.info.personList[0].age++;
          })

        Text(`${this.info.personList[1].age}`)
          .fontSize(40)
          .onClick(() => {
            this.info.personList[1].age++;
          })

        Text(`${this.info.personList[2].age}`)
          .fontSize(40)
          .onClick(() => {
            this.info.personList[2].age++;
          })
      }

      Divider()

      ForEach(this.info.personList, (item: Person, index: number) => {
        Text(`${index} ${item.age}`)
          .fontSize(40)
      })
    }
  }
}
```

### Decorating a Property of the Map Type with \@Trace

* With a property of the Map type decorated by \@Trace, changes caused by supported APIs, such as **set**, **clear**, and **delete**, can be observed.
* In the following example, the **Info** class is decorated with \@ObservedV2 and its **memberMap** property is decorated with \@Trace; as such, changes to the **memberMap** property caused by clicking **Button('init map')** can be observed.

<!-- @[Decoration_Map](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/usagescenarios/DecorationMap.ets) -->

``` TypeScript
@ObservedV2
class Info {
  @Trace public memberMap: Map<number, string> = new Map([[0, 'a'], [1, 'b'], [3, 'c']]);
}

@Entry
@ComponentV2
struct MapSample {
  info: Info = new Info();

  build() {
    Row() {
      Column() {
        ForEach(Array.from(this.info.memberMap.entries()), (item: [number, string]) => {
          Text(`${item[0]}`)
            .fontSize(30)
          Text(`${item[1]}`)
            .fontSize(30)
          Divider()
        })
        Button('init map')
          .onClick(() => {
            this.info.memberMap = new Map([[0, 'a'], [1, 'b'], [3, 'c']]);
          })
        Button('set new one')
          .onClick(() => {
            this.info.memberMap.set(4, 'd');
          })
        Button('clear')
          .onClick(() => {
            this.info.memberMap.clear();
          })
        Button('set the key: 0')
          .onClick(() => {
            this.info.memberMap.set(0, 'aa');
          })
        Button('delete the first one')
          .onClick(() => {
            this.info.memberMap.delete(0);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### Decorating a Property of the Set Type with \@Trace

* With a property of the Set type decorated by \@Trace, changes caused by supported APIs, such as **add**, **clear**, and **delete**, can be observed.
* In the following example, the **Info** class is decorated with \@ObservedV2 and its **memberSet** property is decorated with \@Trace; as such, changes to the **memberSet** property caused by clicking **Button('init set')** can be observed.

<!-- @[Decoration_Set](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/usagescenarios/DecorationSet.ets) -->

``` TypeScript
@ObservedV2
class Info {
  @Trace public memberSet: Set<number> = new Set([0, 1, 2, 3, 4]);
}

@Entry
@ComponentV2
struct SetSample {
  info: Info = new Info();

  build() {
    Row() {
      Column() {
        ForEach(Array.from(this.info.memberSet.entries()), (item: [number, number]) => {
          Text(`${item[0]}`)
            .fontSize(30)
          Divider()
        })
        Button('init set')
          .onClick(() => {
            this.info.memberSet = new Set([0, 1, 2, 3, 4]);
          })
        Button('set new one')
          .onClick(() => {
            this.info.memberSet.add(5);
          })
        Button('clear')
          .onClick(() => {
            this.info.memberSet.clear();
          })
        Button('delete the first one')
          .onClick(() => {
            this.info.memberSet.delete(0);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```


### Decorating a Property of the Date Type with \@Trace

* With a property of the Date type decorated by \@Trace, changes caused by the following APIs can be observed: setFullYear, setMonth, setDate, setHours, setMinutes, setSeconds, setMilliseconds, setTime, setUTCFullYear, setUTCMonth, setUTCDate, setUTCHours, setUTCMinutes, setUTCSeconds, setUTCMilliseconds.
* In the following example, the **Info** class is decorated with \@ObservedV2 and its **selectedDate** property is decorated with \@Trace; as such, changes to the **selectedDate** property caused by clicking **Button('set selectedDate to 2023-07-08')** can be observed.

<!-- @[Decorate_Date](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/usagescenarios/DecorateDate.ets) -->

``` TypeScript
@ObservedV2
class Info {
  @Trace public selectedDate: Date = new Date('2021-08-08');
}

@Entry
@ComponentV2
struct DateSample {
  info: Info = new Info();

  build() {
    Column() {
      Button('set selectedDate to 2023-07-08')
        .margin(10)
        .onClick(() => {
          this.info.selectedDate = new Date('2023-07-08');
        })
      Button('increase the year by 1')
        .margin(10)
        .onClick(() => {
          this.info.selectedDate.setFullYear(this.info.selectedDate.getFullYear() + 1);
        })
      Button('increase the month by 1')
        .margin(10)
        .onClick(() => {
          this.info.selectedDate.setMonth(this.info.selectedDate.getMonth() + 1);
        })
      Button('increase the day by 1')
        .margin(10)
        .onClick(() => {
          this.info.selectedDate.setDate(this.info.selectedDate.getDate() + 1);
        })
      DatePicker({
        start: new Date('1970-1-1'),
        end: new Date('2100-1-1'),
        selected: this.info.selectedDate
      })
    }.width('100%')
  }
}
```

## FAQs

### Serialization and Deserialization of Objects Decorated with \@ObservedV2

After an object decorated with \@ObservedV2 is serialized, the **__ob_** prefix is added to the attributes decorated with \@Trace.

```ts
@ObservedV2
class Info {
  @Trace name: string = 'Tom';
  @Trace age: number = 24;
}

let realInfo: Info = new Info();
let jsonResult: string = JSON.stringify(realInfo); // '{"__ob_name":"Tom","__ob_age":24}'
```

After an object decorated with @ObservedV2 is serialized by using JSON.stringify and then deserialized by using JSON.parse, the observation capability is lost.

```ts
@ObservedV2
class Info {
  @Trace name: string = 'Tom';
  @Trace age: number = 24;
}

let realInfo: Info = new Info();
let jsonResult: string = JSON.stringify(realInfo); // '{"__ob_name":"Tom","__ob_age":24}'
let parseInfo: Info = JSON.parse(jsonResult);

// Different from the object created using the new operator, the object obtained by JSON.parse is not an instance of Info. Therefore, the attribute observation capability is unavailable.
let isInfoByNew: boolean = realInfo instanceof Info; // true
let isInfoByParse: boolean = parseInfo instanceof Info; // false
```

You can use the third-party library [class-transformer](https://gitcode.com/openharmony-tpc/openharmony_tpc_samples/tree/master/class-transformer) to implement observation after deserialization.

You can run the following command to install class-transformer:

```text
ohpm install class-transformer
```

```ts
import { plainToInstance } from 'class-transformer'; // Import the third-party library.
@ObservedV2
class Info {
  @Trace name: string = 'Tom';
  @Trace age: number = 24;
}
let realInfo: Info = new Info();
let jsonResult: string = JSON.stringify(realInfo); // '{"__ob_name":"Tom","__ob_age":24}'
let parseInfo: Info = JSON.parse(jsonResult);

let transformedInfo: Info = plainToInstance(Info, parseInfo);
let isInfoByTransformed: boolean = transformedInfo instanceof Info; // true
```

If multiple layers of objects are nested, the following operations are required:

- Remove the **__ob_** prefix from the serialization result. Otherwise, the inner object cannot be correctly converted.
- Use the @Type decorator provided by the class-transformer library (re-named as **TypeFromLibrary** in the example for distinguishing from [@Type](arkts-new-type.md) in state management V2) to mark the type of the inner object.

To use the @Type decorator of the third-party library, you need to install [reflect-metadata](https://gitcode.com/openharmony-tpc/openharmony_tpc_samples/tree/master/reflect-metadata).

You can run the following command to install reflect-metadata:

```text
ohpm install reflect-metadata@0.2.1
```

```ts
import { plainToInstance, Type as TypeFromLibrary} from 'class-transformer'; // Import the third-party library.
import 'reflect-metadata'; // The @Type decorator of the third-party library is required.
@ObservedV2
class Info {
  @Trace name: string = 'Tom';
  @Trace age: number = 24;
}
@ObservedV2
class InfoWrapper {
  // Use the @Type decorator (renamed to TypeFromLibrary) of the third-party library to mark the type of the inner attribute.
  @TypeFromLibrary(() => Info)
  @Trace info: Info = new Info();
}
let realWrapper: InfoWrapper = new InfoWrapper();
let infoWrapperJson: string = JSON.stringify(realWrapper); // '{"__ob_info":{"__ob_name":"Tom","__ob_age":24}}'
// Remove the '__ob_' prefix from the attribute key. This is only an example. You need to remove the '__ob_' prefix from the key based on the actual type definition.
let jsonHandled = infoWrapperJson.replaceAll('__ob_', ''); // '{"info":{"name":"Tom","age":24}}'
let wrapperHandled = plainToInstance(InfoWrapper, JSON.parse(jsonHandled));

let isWrapper: boolean = wrapperHandled instanceof InfoWrapper; // true
let isInfo: boolean = (wrapperHandled.info) instanceof Info; // true
```

The following is a complete example.

<!-- @[Serialization_And_Deserialization](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/faqs/SerializationAndDeserialization.ets) -->

``` TypeScript
import { plainToInstance, Type as TypeFromLibrary } from 'class-transformer'; // Import the third-party library.
import 'reflect-metadata'; // The @Type decorator of the third-party library is required.

// Simulate the JSON key-value pair object.
let testJSON: Record<string, ESObject> = {
  'id': 1,
  'info': {
    'name': 'Tom',
    'age': 24
  },
  'friends': [
    {
      'name': 'John',
      'age': 23
    },
    {
      'name': 'Mary',
      'age': 24
    }
  ]
}

@ObservedV2
class Info {
  @Trace public name?: string;
  @Trace public age?: number;
}

@ObservedV2
class Person {
  public id?: number;
  // Use the @Type decorator (renamed to TypeFromLibrary) of the third-party library to mark the type of the inner attribute.
  @TypeFromLibrary(() => Info)
  @Trace public info?: Info;
  // Use the @Type decorator (renamed to TypeFromLibrary) of the third-party library to mark the type of the inner attribute.
  @TypeFromLibrary(() => Info)
  @Trace public friends?: Info[];
}

@Entry
@ComponentV2
struct SerializationAndDeserialization {
  @Local person: Person | undefined = undefined;
  aboutToAppear(): void {
    this.person = plainToInstance(Person, testJSON); // Use plainToInstance to convert the object to a Person instance.
  }

  build() {
    Column() {
      Text(`name: ${this.person?.info?.name}, age: ${this.person?.info?.age}`)
        .onClick(() => {
          if (this.person?.info?.age) {
            this.person!.info!.age++; // Modify the observable object.
          }
        })
      ForEach(this.person?.friends, (item: Info) => {
        Text(`friend name: ${item.name}, age: ${item.age}`)
          .onClick(() => {
            if (item.age) {
              item.age++; // Modify the observable object.
            }
          })
      })

      Button('Refresh Info')
        .onClick(() => {
          let json: string =
            `{
              "id":12,
                "__ob_info":
                  {
                    "__ob_name":"Jimmy",
                    "__ob_age":35
                   },
              "__ob_friends":[
                {
                  "__ob_name":"Bob",
                  "__ob_age":30
                },
                {
                  "__ob_name":"Kevin",
                  "__ob_age":33
                }
              ]
            }`;
          // Remove the '__ob_' prefix and convert the JSON string to a Person object using JSON.parse and plainToInstance.
          this.person = plainToInstance(Person, JSON.parse(json.replaceAll('__ob_', '')));
        })
    }
  }
}
```

### @ObservedV2 Type Transferred by router Is Abnormal

The @ObservedV2 class transferred by router cannot be directly converted to the @ObservedV2 instance through the **as** type because the attribute name generated after serialization is different from the original attribute name in the class. Instead, deserialization needs to be performed to generate a new @ObservedV2 instance. For details about deserialization, see [Serialization and Deserialization of Objects Decorated with \@ObservedV2](#serialization-and-deserialization-of-objects-decorated-with-observedv2).

**Incorrect Usage**

```ts
// Content of the pages/faqs/RouterIndex.ets file.

@ObservedV2
export class RouterModel {
  @Trace id: number = -1;
  @Trace info: string = 'default';
}

@Entry
@ComponentV2
struct RouterIndex {
  @Local paramsInfo: RouterModel = new RouterModel();
  onJumpClick(): void {
    this.paramsInfo.id = 0;
    this.paramsInfo.info = 'RouterModel';
    this.getUIContext().getRouter().pushUrl({
      url: 'pages/faqs/ChildPage',
      params: this.paramsInfo // Pass the @ObservedV2 instance to the subpage.
    }, (err) => {
      if (err) {
        console.error(`Invoke pushUrl failed, code is ${err.code}, message is ${err.message}`);
        return;
      }
      console.info('Invoke pushUrl succeeded.');
    })
  }

  build() {
    Column() {
      Text('Parent page')
      Button('Jump')
        .onClick(() => {
          this.onJumpClick();
        })
    }
  }
}
```

```ts
// Content of the pages/faqs/ChildPage.ets file.

import { RouterModel } from './RouterIndex';

@Entry
@ComponentV2
struct Detail {
  @Local params?: RouterModel
  aboutToAppear(): void {
    //Incorrect usage. @ObservedV2 types cannot be directly converted when being passed through the router.
    this.params = this.getUIContext().getRouter().getParams() as RouterModel;
  }
  build() {
    Column() {
      Text(`Detail Page: ${this.params?.id} ${this.params?.info}`) // If the data fails to be transferred, undefined is displayed.
    }
  }
}
```

**Correct Usage**

<!-- @[Router_Index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/faqs/RouterIndex.ets) -->

``` TypeScript
@ObservedV2
export class RouterModel {
  @Trace public id: number = -1;
  @Trace public info: string = 'default';
}

@Entry
@ComponentV2
struct RouterIndex {
  @Local paramsInfo: RouterModel = new RouterModel();
  onJumpClick(): void {
    this.paramsInfo.id = 0;
    this.paramsInfo.info = 'RouterModel';
    this.getUIContext().getRouter().pushUrl({
      url: 'pages/faqs/ChildPage',
      params: this.paramsInfo // Pass the @ObservedV2 instance to the subpage.
    }, (err) => {
      if (err) {
        console.error(`Invoke pushUrl failed, code is ${err.code}, message is ${err.message}`);
        return;
      }
      console.info('Invoke pushUrl succeeded.');
    })
  }

  build() {
    Column() {
      Text('Parent page')
      Button('Jump')
        .onClick(() => {
          this.onJumpClick();
        })
    }
  }
}
```

<!-- @[Child_Page](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/arktsobservedv2andtrace/entry/src/main/ets/pages/faqs/ChildPage.ets) -->

``` TypeScript
import { RouterModel } from './RouterIndex';
import { plainToInstance } from 'class-transformer'; // Import the third-party library.

@Entry
@ComponentV2
struct Detail {
  @Local params?: RouterModel
  aboutToAppear(): void {
    this.params =
      plainToInstance(RouterModel, JSON.parse(JSON.stringify(this.getUIContext().getRouter().getParams())));
  }
  build() {
    Column() {
      Text(`Detail Page: ${this.params?.id} ${this.params?.info}`)
    }
  }
}
```

![observedv2_router_deserialize.gif](./figures/observedv2_router_deserialize.gif)
