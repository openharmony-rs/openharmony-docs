# makeObserved API: Changing Unobservable Data to Observable Data
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

To convert unobservable data into observable data, use the [makeObserved](../../reference/apis-arkui/js-apis-stateManagement.md#makeobserved) API.


**makeObserved** is designed for scenarios where \@Trace cannot be applied. Before reading this topic, it is recommended to familiarize yourself with [\@Trace](./arkts-new-observedV2-and-trace.md).

>**NOTE**
>
>The **makeObserved** API in UIUtils is supported starting from API version 12.

## Overview

- The state management framework provides [@ObservedV2 and @Trace](./arkts-new-observedV2-and-trace.md) decorators to observe class property changes. The **makeObserved** API is primarily used when @ObservedV2 or @Trace cannot be applied. For example:

  - Classes from third-party packages may have unobservable objects. If you cannot manually add the @Trace decorator to the class properties that need observation, use **makeObserved** to make the object observable.

  - When class member properties cannot be modified. @Trace observes class attributes and dynamically modifies them, which is not permitted in classes decorated with [@Sendable](../../arkts-utils/arkts-sendable.md#sendable-decorator). In such cases, use makeObserved.

  - Anonymous objects returned by APIs or JSON.parse lack class declarations. Since @Trace cannot mark attributes in this scenario, use **makeObserved** instead.


- To use the **makeObserved** API, import UIUtils.
  ```ts
  import { UIUtils } from '@kit.ArkUI';
  ```

## Constraints

- **makeObserved** parameters support only non-null object types.
  - Undefined and null: Not supported. The parameter itself is returned without any processing.
  - Non-object types: A compilation error is reported.

  ```ts
  import { UIUtils } from '@kit.ArkUI';
  let res1 = UIUtils.makeObserved(2); // Invalid parameter. Compilation error.
  let res2 = UIUtils.makeObserved(undefined); // Invalid parameter. Returns the parameter itself, i.e., res2 === undefined.
  let res3 = UIUtils.makeObserved(null); // Invalid parameter. Returns the parameter itself, i.e., res3 === null.

  class Info {
    id: number = 0;
  }
  let rawInfo: Info = UIUtils.makeObserved(new Info()); // Correct usage.
  ```

- makeObserved does not support instances of classes decorated with [@ObservedV2](./arkts-new-observedV2-and-trace.md) or [@Observed](./arkts-observed-and-objectlink.md), nor proxy data already encapsulated by makeObserved. To prevent double-proxying, makeObserved returns the input parameter directly if it belongs to any of these types.
  ```ts
  import { UIUtils } from '@kit.ArkUI';
  @ObservedV2
  class Info {
    @Trace id: number = 0;
  }
  // Incorrect usage: If the input instance is from a class decorated with @ObservedV2, makeObserved returns the input object itself.
  let observedInfo: Info = UIUtils.makeObserved(new Info());

  class Info2 {
    id: number = 0;
  }
  // Correct usage. The input object is neither an instance of a class decorated with @ObservedV2/@Observed nor proxy data encapsulated by makeObserved.
  // Returns observable data.
  let observedInfo1: Info2 = UIUtils.makeObserved(new Info2());
  // Incorrect usage. The input object is already proxy data from makeObserved, so no processing occurs.
  let observedInfo2: Info2 = UIUtils.makeObserved(observedInfo1);
  ```
- makeObserved can be used in custom components decorated with [@Component](./arkts-create-custom-components.md#component), but is incompatible with state variable decorators from V1 state management. Using them together will throw a runtime exception.
  ```ts
  // Incorrect usage. Throws a runtime exception.
  @State message: Info = UIUtils.makeObserved(new Info(20));
  ```
  Note: The following message2 does not throw an exception because:
  - this.message is decorated with [@State](./arkts-state.md), which is equivalent to @Observed.
  - If the input parameter to UIUtils.makeObserved is an instance of a class decorated with @Observed, the instance is returned directly.
  
  Therefore, the initial value of message2 is not the proxy object from makeObserved, but this.message decorated with @State.
  ```ts
  import { UIUtils } from '@kit.ArkUI';
  class Person {
    age: number = 10;
  }
  class Info {
    id: number = 0;
    person: Person = new Person();
  }
  @Entry
  @Component
  struct Index {
    @State message: Info = new Info();
    @State message2: Info = UIUtils.makeObserved(this.message); // No exception thrown.
    build() {
      Column() {
        Text(`${this.message2.person.age}`)
          .onClick(() => {
            // UI does not re-render because @State only observes first-level changes.
            this.message2.person.age++;
          })
      }
    }
  }
  ```
### makeObserved Performs Deep Observation on the Input Parameter Object

 - message is decorated with [@Local](./arkts-new-local.md), enabling observation of its own assignments. Its initial value is the return value of **makeObserved**, which supports deep observation. Note that makeObserved only performs deep observation on message, while value changes to message are observed by @Local.
 - Click **change id** to trigger a UI re-render.
 - Click change Info to reassign this.message to unobservable data. Clicking change id again will not refresh the UI.
 - Click change Info1 to reassign this.message to observable data. Clicking change id again will refresh the UI.

  ```ts
  import { UIUtils } from '@kit.ArkUI';
  class Info {
    id: number = 0;
    constructor(id: number) {
      this.id = id;
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    @Local message: Info = UIUtils.makeObserved(new Info(20));
    build() {
      Column() {
        Button(`change id`).onClick(() => {
          this.message.id++;
        })
        Button(`change Info ${this.message.id}`).onClick(() => {
          this.message = new Info(30);
        })
        Button(`change Info1 ${this.message.id}`).onClick(() => {
          this.message = UIUtils.makeObserved(new Info(30));
        })
      }
    }
  }
  ```

## Supported Types and Observable Changes

### Supported Data Types

- Classes not decorated with [\@Observed](./arkts-observed-and-objectlink.md) or [\@ObservedV2](./arkts-new-observedV2-and-trace.md).
- Array, Map, Set, and Date types.
- [collections.Array](../../reference/apis-arkts/arkts-apis-arkts-collections-Array.md), [collections.Set](../../reference/apis-arkts/arkts-apis-arkts-collections-Set.md), and [collections.Map](../../reference/apis-arkts/arkts-apis-arkts-collections-Map.md).
- Objects returned by JSON.parse.
- Classes decorated with @Sendable.

### Observable Changes

- When an instance of a built-in type or collections type is passed to **makeObserved**, the following changes can be observed:

  | Type | Change-Triggering APIs                                             |
  | ----- | ------------------------------------------------------------ |
  | Array | push, pop, shift, unshift, splice, copyWithin, fill, reverse, sort|
  | collections.Array | push, pop, shift, unshift, splice, fill, reverse, sort, shrinkTo, extendTo|
  | Map/collections.Map   | set, clear, delete                                |
  | Set/collections.Set   | add, clear, delete                                |
  | Date  | setFullYear, setMonth, setDate, setHours, setMinutes, setSeconds, setMilliseconds, setTime, setUTCFullYear, setUTCMonth, setUTCDate, setUTCHours, setUTCMinutes, setUTCSeconds, setUTCMilliseconds|

## Use Cases

### Using makeObserved with @Sendable Decorated Classes

[@Sendable](../../arkts-utils/arkts-sendable.md) is used for handling concurrent tasks. Combining makeObserved with @Sendable meets general application development requirements, such as processing large data in worker threads and displaying/observing data in the ViewModel on the UI thread. For details about @Sendable, see [Multithreaded Concurrency Overview (TaskPool and Worker)](../../arkts-utils/multi-thread-concurrency-overview.md).

This section illustrates the following scenarios:
- Using **makeObserved** with @Sendable data enables observability for changes that trigger UI updates.
- Fetching a complete dataset from a worker thread and replacing the observable data in the UI thread.
- Reprocessing data from a worker thread with **makeObserved** to make it observable.
- When passing data from the main thread to a worker thread, only unobservable data should be passed. The return value of **makeObserved** should not be passed directly to worker threads.

Example:

```ts
// SendableData.ets
@Sendable
export class SendableData  {
  name: string = 'Tom';
  age: number = 20;
  gender: number = 1;
  // Other attributes omitted.
  likes: number = 1;
  follow: boolean = false;
}
```

```ts
import { taskpool } from '@kit.ArkTS';
import { SendableData } from './SendableData';
import { UIUtils } from '@kit.ArkUI';


@Concurrent
function threadGetData(param: string): SendableData {
  // Process data in the worker thread.
  let ret = new SendableData();
  console.info(`Concurrent threadGetData, param ${param}`);
  ret.name = param + '-o';
  ret.age = Math.floor(Math.random() * 40);
  ret.likes = Math.floor(Math.random() * 100);
  return ret;
}

@Entry
@ComponentV2
struct ObservedSendableTest {
  // Use makeObserved to add observation to a regular object or a @Sendable object.
  @Local send: SendableData = UIUtils.makeObserved(new SendableData());
  build() {
    Column() {
      Text(this.send.name)
      Button('change name').onClick(() => {
        // Attribute changes can be observed.
        this.send.name += '0';
      })

      Button('task').onClick(() => {
        // Enqueue the function for execution in the task pool, waiting to be dispatched to a worker thread.
        taskpool.execute(threadGetData, this.send.name).then(val => {
          // Used with @Local to observe changes to 'this.send'.
          this.send = UIUtils.makeObserved(val as SendableData);
        })
      })
    }
  }
}
```
**NOTE**<br>Data can be constructed and processed in worker threads. However, observable data can only be processed in the main thread. Therefore, in the preceding example, only the **name** attribute of **this.send** is passed to the worker thread.

### Using makeObserved with collections.Array/collections.Set/collections.Map
**collections** provide ArkTS container classes for high-performance data passing in concurrent scenarios. For details, see [@arkts.collections (ArkTS Collections)](../../reference/apis-arkts/arkts-apis-arkts-collections.md).
makeObserved enables importing observable collections into ArkUI but is incompatible with V1 state management decorators like @State and [@Prop](./arkts-prop.md). Combining them will result in runtime exceptions.

**collections.Array**

The following APIs trigger UI re-rendering:
- Changing array length: push, pop, shift, unshift, splice, shrinkTo, and extendTo
- Changing array items: sort and fill

Other APIs that do not modify the original array will not trigger UI re-rendering.

```ts
import { collections } from '@kit.ArkTS';
import { UIUtils } from '@kit.ArkUI';

@Sendable
class Info {
  id: number = 0;
  name: string = 'cc';

  constructor(id: number) {
    this.id = id;
  }
}


@Entry
@ComponentV2
struct Index {
  scroller: Scroller = new Scroller();
  @Local arrCollect: collections.Array<Info> =
    UIUtils.makeObserved(new collections.Array<Info>(new Info(1), new Info(2)));

  build() {
    Column() {
      // The ForEach API only supports Array<any>, not collections.Array<any>.
      // However, collections.Array provides the necessary array APIs for ForEach implementation. Therefore, you can use the 'as' keyword to assert the type as Array.
      // This assertion does not change the original data type.
      ForEach(this.arrCollect as object as Array<Info>, (item: Info) => {
        Text(`${item.id}`).onClick(() => {
          item.id++;
        })
      }, (item: Info, index) => item.id.toString() + index.toString())
      Divider()
        .color('blue')
      if (this.arrCollect.length > 0) {
        Text(`the first one ${this.arrCollect[0].id}`)
        Text(`the last one ${this.arrCollect[this.arrCollect.length - 1].id}`)
      }
      Divider()
        .color('blue')

      /****************************APIs for Changing Data Length**************************/
      Scroll(this.scroller) {
        Column({space: 10}) {
          // push: adds a new element.
          Button('push').onClick(() => {
            this.arrCollect.push(new Info(30));
          })
          // pop: removes the last element.
          Button('pop').onClick(() => {
            this.arrCollect.pop();
          })
          // shift: removes the first element.
          Button('shift').onClick(() => {
            this.arrCollect.shift();
          })
          // unshift: inserts a new item at the beginning of the array.
          Button('unshift').onClick(() => {
            this.arrCollect.unshift(new Info(50));
          })
          // splice: removes elements starting from the specified position.
          Button('splice').onClick(() => {
            this.arrCollect.splice(1);
          })

          // shrinkTo: reduces the array length to the specified size.
          Button('shrinkTo').onClick(() => {
            this.arrCollect.shrinkTo(1);
          })
          // extendTo: extends the array length to the specified size.
          Button('extendTo').onClick(() => {
            this.arrCollect.extendTo(6, new Info(20));
          })

          Divider()
            .color('blue')

          /****************************************APIs for Changing Array Items*****************/
          // sort: sorts array items in descending order.
          Button('sort').onClick(() => {
            this.arrCollect.sort((a: Info, b: Info) => b.id - a.id);
          })
          // fill: fills a portion of the array with a specified value.
          Button('fill').onClick(() => {
            this.arrCollect.fill(new Info(5), 0, 2);
          })

          /*****************************APIs That Do Not Change the Original Array***************************/
          // slice: returns a new array. Array.slice(start,end) creates a shallow copy and does not modify the original array, so calling slice directly does not trigger UI re-rendering.
          // You can create a case where the shallow-copied return data is assigned to this.arrCollect. Note that makeObserved must be called here; otherwise, the observation capability is lost when this.arr is assigned a common variable.
          Button('slice').onClick(() => {
            this.arrCollect = UIUtils.makeObserved(this.arrCollect.slice(0, 1));
          })
          // map: same principle as above.
          Button('map').onClick(() => {
            this.arrCollect = UIUtils.makeObserved(this.arrCollect.map((value) => {
              value.id += 10;
              return value;
            }))
          })
          // filter: same principle as above.
          Button('filter').onClick(() => {
            this.arrCollect = UIUtils.makeObserved(this.arrCollect.filter((value: Info) => value.id % 2 === 0));
          })

          // concat: same principle as above.
          Button('concat').onClick(() => {
            let array1 = new collections.Array(new Info(100))
            this.arrCollect = UIUtils.makeObserved(this.arrCollect.concat(array1));
          })
        }.height('200%')
      }.height('60%')
    }
    .height('100%')
    .width('100%')
  }
}
```

**collections.Map**

The following APIs trigger UI re-rendering: set, clear, and delete.
```ts
import { collections } from '@kit.ArkTS';
import { UIUtils } from '@kit.ArkUI';

@Sendable
class Info {
  id: number = 0;

  constructor(id: number) {
    this.id = id;
  }
}


@Entry
@ComponentV2
struct CollectionMap {
  mapCollect: collections.Map<string, Info> = UIUtils.makeObserved(new collections.Map<string, Info>([['a', new Info(10)], ['b', new Info(20)]]));

  build() {
    Column() {
      // this.mapCollect.keys() returns an iterator, which ForEach does not support. Therefore, use Array.from to create a shallow copy of the data.
      ForEach(Array.from(this.mapCollect.keys()), (item: string) => {
        Text(`${this.mapCollect.get(item)?.id}`).onClick(() => {
          let value: Info|undefined = this.mapCollect.get(item);
          if (value) {
            value.id++;
          }
        })
      }, (item: string, index) => item + index.toString())

      // set c
      Button('set c').onClick(() => {
        this.mapCollect.set('c', new Info(30));
      })
      // delete c
      Button('delete c').onClick(() => {
        if (this.mapCollect.has('c')) {
          this.mapCollect.delete('c');
        }
      })
      // clear
      Button('clear').onClick(() => {
        this.mapCollect.clear();
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

**collections.Set**

The following APIs trigger UI re-rendering: add, clear, and delete.

```ts
import { collections } from '@kit.ArkTS';
import { UIUtils } from '@kit.ArkUI';
@Sendable
class Info {
  id: number = 0;

  constructor(id: number) {
    this.id = id;
  }
}


@Entry
@ComponentV2
struct Index {
  set: collections.Set<Info> = UIUtils.makeObserved(new collections.Set<Info>([new Info(10), new Info(20)]));

  build() {
    Column() {
      // ForEach does not support iterators. Use Array.from to create a shallow copy of the data.
      // However, the new array from the shallow copy is not observable. To ensure data observability when the ForEach component accesses items, call makeObserved again.
      ForEach((UIUtils.makeObserved(Array.from(this.set.values()))), (item: Info) => {
        Text(`${item.id}`).onClick(() => {
          item.id++;
        })
      }, (item: Info, index) => item.id + index.toString())

      // add
      Button('add').onClick(() => {
        this.set.add(new Info(30));
        console.info('size:' + this.set.size);
      })
      // delete
      Button('delete').onClick(() => {
        let iterator = this.set.keys();
        this.set.delete(iterator.next().value);
      })
      // clear
      Button('clear').onClick(() => {
        this.set.clear();
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

### makeObserved Input Parameter Is JSON.parse Return Value
**JSON.parse** returns an object that cannot be decorated with @Trace. Use **makeObserved** to make it observable.

```ts
import { JSON } from '@kit.ArkTS';
import { UIUtils } from '@kit.ArkUI';

class Info {
  id: number = 0;

  constructor(id: number) {
    this.id = id;
  }
}

let test: Record<string, number> = { 'a': 123 };
let testJsonStr: string = JSON.stringify(test);
let test2: Record<string, Info> = { 'a': new Info(20) };
let test2JsonStr: string = JSON.stringify(test2);

@Entry
@ComponentV2
struct Index {
  message: Record<string, number> = UIUtils.makeObserved<Record<string, number>>(JSON.parse(testJsonStr) as Record<string, number>);
  message2: Record<string, Info> = UIUtils.makeObserved<Record<string, Info>>(JSON.parse(test2JsonStr) as Record<string, Info>);

  build() {
    Column() {
      Text(`${this.message.a}`)
        .fontSize(50)
        .onClick(() => {
          this.message.a++;
        })
      Text(`${this.message2.a.id}`)
        .fontSize(50)
        .onClick(() => {
          this.message2.a.id++;
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Using makeObserved with V2 Decorators
**makeObserved** can be used with V2 decorators. [@Monitor](./arkts-new-monitor.md) and [@Computed](./arkts-new-computed.md) cannot be defined within a class because makeObserved returns a class instance decorated with @Observed or ObservedV2. Therefore, @Monitor or @Computed must be defined within custom components.

Example:
```ts
import { UIUtils } from '@kit.ArkUI';

class Info {
  id: number = 0;
  age: number = 20;

  constructor(id: number) {
    this.id = id;
  }
}

@Entry
@ComponentV2
struct Index {
  @Local message: Info = UIUtils.makeObserved(new Info(20));

  @Monitor('message.id')
  onStrChange(monitor: IMonitor) {
    console.info(`name change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }

  @Computed
  get ageId() {
    console.info('---------Computed----------');
    return this.message.id + ' ' + this.message.age;
  }

  build() {
    Column() {
      Text(`id: ${this.message.id}`)
        .fontSize(50)
        .onClick(() => {
          this.message.id++;
        })

      Text(`age: ${this.message.age}`)
        .fontSize(50)
        .onClick(() => {
          this.message.age++;
        })

      Text(`Computed age+id: ${this.ageId}`)
        .fontSize(50)

      Button('change Info').onClick(() => {
        this.message = UIUtils.makeObserved(new Info(200));
      })

      Child({message: this.message})
    }
    .height('100%')
    .width('100%')
  }
}

@ComponentV2
struct Child {
  @Param @Require message: Info;
  build() {
    Text(`Child id: ${this.message.id}`)
  }
}
```

### Using makeObserved in @Component
**makeObserved** cannot be used with V1 state variable decorators but can be used in custom components decorated with @Component.

```ts
import { UIUtils } from '@kit.ArkUI';
class Info {
  id: number = 0;

  constructor(id: number) {
    this.id = id;
  }
}


@Entry
@Component
struct Index {
  // Using makeObserved with @State throws a runtime exception.
  message: Info = UIUtils.makeObserved(new Info(20));

  build() {
    RelativeContainer() {
      Text(`${this.message.id}`)
        .onClick(() => {
          this.message.id++;
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## FAQs
### Assigning Values to the Original Object via getTarget Fails to Trigger UI Re-render
[getTarget](./arkts-new-getTarget.md) can retrieve the original object before proxy addition in state management.

The observable object encapsulated by **makeObserved** can have its original object retrieved via **getTarget**. Modifying the original object's values does not trigger UI re-rendering.

Example:
1. Click the first **Text** component to get its original object via **getTarget**. Modifying the original object's attributes does not trigger UI re-rendering but updates the data.
2. Click the second **Text** component. Modifying the **this.observedObj** attribute triggers a UI re-render, and the **Text** value becomes **21**.

```ts
import { UIUtils } from '@kit.ArkUI';
class Info {
  id: number = 0;
}

@Entry
@Component
struct Index {
  observedObj: Info = UIUtils.makeObserved(new Info());
  build() {
    Column() {
      Text(`${this.observedObj.id}`)
        .fontSize(50)
        .onClick(() => {
          // Use getTarget to get the original object and assign unobservable data to this.observedObj.
          let rawObj: Info= UIUtils.getTarget(this.observedObj);
          // UI does not re-render, but the data is updated.
          rawObj.id = 20;
        })

      Text(`${this.observedObj.id}`)
        .fontSize(50)
        .onClick(() => {
          // Triggers UI re-render. Text value becomes 21.
          this.observedObj.id++;
        })
    }
  }
}
```
