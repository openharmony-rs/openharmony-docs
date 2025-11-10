# makeObserved接口：将非观察数据变为可观察数据

为了将普通不可观察数据变为可观察数据，开发者可以使用[makeObserved接口](../../reference/apis-arkui/js-apis-stateManagement-static.md#makeobserved)。

## 概述

makeObserved接口可以将[Array](#makeobserved与array配合使用)、[Map](#makeobserved与map配合使用)、[Set](#makeobserved与set配合使用)、[Date](#makeobserved与date配合使用)以及[interface字面量类型](#makeobserved与interface字面量配合使用)的变量转变为可观察数据。

由makeObserved转换的数据，即使不使用状态变量装饰器，也能观察其内部属性变化。

在静态语言上下文中使用时，需要导入UIUtils工具：

```ts
import { UIUtils } from '@ohos.arkui.stateManagement';
```

## 支持类型和观察变化

### 支持类型

makeObserved支持以下类型的变量：

- Array、Map、Set、Date
- interface字面量

### 观察变化

- makeObserved传入Array、Map、Set、Date类型的实例时，可以观察其API带来的变化。

  | 类型  | 可观测变化的API                                              |
  | ----- | ------------------------------------------------------------ |
  | Array | push、pop、shift、unshift、splice、copyWithin、fill、reverse、sort |
  | Map   | set、clear、delete                                           |
  | Set   | add、clear、delete                                           |
  | Date  | setFullYear、setMonth、setDate、setHours、setMinutes、setSeconds、setMilliseconds、setTime、setUTCFullYear、setUTCMonth、setUTCDate、setUTCHours、setUTCMinutes、setUTCSeconds、setUTCMilliseconds |

- makeObserved转换的数据具备可观察能力，即使不使用状态变量装饰器，也能观察其内部属性变化。

  ```ts
  'use static'
  
  import { Entry, Component, Column, Text, ClickEvent } from '@ohos.arkui.component';
  import { UIUtils } from '@ohos.arkui.stateManagement';
  interface Info {
    name: string;
    age: number;
  }
  @Entry
  @Component
  struct Index {
    info: Info = UIUtils.makeObserved({ name: 'Jack', age: 25} as Info) as Info;
    build() {
      Column() {
        Text(`info.name: ${this.info.name}`)
          .onClick((e: ClickEvent) => {
            this.info.name = 'Tom'; // 不依赖装饰器，仍能观察内部变化
          })
      }
    }
  }
  ```

- makeObserved支持观察嵌套场景。

  ```ts
  'use static'
  
  import { Entry, Component, Column, Text, ClickEvent } from '@ohos.arkui.component';
  import { UIUtils } from '@ohos.arkui.stateManagement';
  interface Info {
    name: string;
    age: number;
  }
  interface Person {
    info: Info;
  }
  @Entry
  @Component
  struct Index {
    person: Person = UIUtils.makeObserved({ info: { name: 'Jack', age: 25} as Info} as Person) as Person;
    build() {
      Column() {
        Text(`info.name: ${this.person.info.name}`)
          .onClick((e: ClickEvent) => {
            this.person.info.name = 'Tom'; // 支持观察嵌套场景
          })
      }
    }
  }
  ```

- 当makeObserved的返回值被状态变量装饰器装饰时，观察能力以makeObserved为准。

  ```ts
  'use static'
  
  import { Entry, Component, Column, Text, ClickEvent } from '@ohos.arkui.component';
  import { State, UIUtils } from '@ohos.arkui.stateManagement';
  interface Info {
    name: string;
    age: number;
  }
  interface Person {
    info: Info;
  }
  @Entry
  @Component
  struct Index {
    @State person: Person = UIUtils.makeObserved({ info: { name: 'Jack', age: 25} as Info} as Person) as Person;
    build() {
      Column() {
        Text(`info.name: ${this.person.info.name}`)
          .onClick((e: ClickEvent) => {
            // @State本身无法观察name变化，但makeObserved支持观察嵌套
            // 此时以makeObserved为准，因此name变化可观察
            this.person.info.name = 'Tom';
          })
      }
    }
  }
  ```

## 限制条件

- 仅支持非空对象作为makeObserved的参数。

  - 不支持undefined和null：返回自身，不做处理。
  - 不支持非对象类型：返回自身，不做处理。

  ```ts
  import { UIUtils } from '@ohos.arkui.stateManagement';
  let res1 = UIUtils.makeObserved(2); // 非对象类型入参，实际无作用，返回2
  let res2 = UIUtils.makeObserved(undefined); // 非对象类型入参，实际无作用，返回undefined
  let res3 = UIUtils.makeObserved(null); // 非对象类型入参，实际无作用，返回null
  ```

- makeObserved传入Array、Map、Set、Date以及interface字面量之外的其他对象类型变量将不做处理。

  ```ts
  import { UIUtils } from '@ohos.arkui.stateManagement';
  @ObservedV2
  class Info {
    @Trace id: number = 0;
  }
  let observedInfo: Info = UIUtils.makeObserved(new Info()); // 非支持类型，不做处理
  class Info2 {
    id: number = 0;
  }
  let observedInfo1: Info2 = UIUtils.makeObserved(new Info2()); // 非支持类型，不做处理
  ```

## 使用场景

### makeObserved与Array配合使用

```ts
'use static'

import { Entry, Component, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { UIUtils } from '@ohos.arkui.stateManagement';
@Entry
@Component
struct Index {
  arr: int[] = UIUtils.makeObserved([0, 1, 2]);
  build() {
    Column() {
      Text(`${this.arr}`)
      Button(`change arr[0]: ${this.arr[0]}`).onClick((e: ClickEvent) => {
        this.arr[0]++;
      })
      Button(`push item: ${this.arr.length}`).onClick((e: ClickEvent) => {
        this.arr.push(Double.toInt(this.arr.length));
      })
      Button(`pop item`).onClick((e: ClickEvent) => {
        this.arr.pop();
      })
      Button(`reverse`).onClick((e: ClickEvent) => {
        this.arr.reverse();
      })
    }
  }
}
```

### makeObserved与Map配合使用

```ts
'use static'

import { Entry, Component, Row, Column, ForEach, Text, Divider, Button, ClickEvent } from '@ohos.arkui.component';
import { UIUtils } from '@ohos.arkui.stateManagement';
@Entry
@Component
struct MapSample {
  message: Map<number, string> = UIUtils.makeObserved(new Map<number, string>([[0, 'a'], [1, 'b'], [3, 'c']]));

  build() {
    Row() {
      Column() {
        ForEach(Array.from(this.message.entries()), (item: [number, string]) => {
          Text(`${item[0]}`).fontSize(30)
          Text(`${item[1]}`).fontSize(30)
          Divider()
        })
        Button('set new one').onClick((e: ClickEvent) => {
          this.message.set(4, 'd');
        })
        Button('clear').onClick((e: ClickEvent) => {
          this.message.clear();
        })
        Button('replace the first one').onClick((e: ClickEvent) => {
          this.message.set(0, 'aa');
        })
        Button('delete the first one').onClick((e: ClickEvent) => {
          this.message.delete(0);
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### makeObserved与Set配合使用

```ts
'use static'

import { Entry, Component, Row, Column, ForEach, Text, Divider, Button, ClickEvent } from '@ohos.arkui.component';
import { UIUtils } from '@ohos.arkui.stateManagement';
@Entry
@Component
struct SetSample {
  message: Set<number> = UIUtils.makeObserved(new Set<number>([0, 1, 2, 3, 4]));

  build() {
    Row() {
      Column() {
        ForEach(Array.from(this.message.entries()), (item: [number, number]) => {
          Text(`${item[0]}`).fontSize(30)
          Divider()
        })
        Button('set new one').onClick((e: ClickEvent) => {
          this.message.add(5);
        })
        Button('clear').onClick((e: ClickEvent) => {
          this.message.clear();
        })
        Button('delete the first one').onClick((e: ClickEvent) => {
          this.message.delete(0);
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### makeObserved与Date配合使用

```ts
'use static'

import { Entry, Component, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { UIUtils } from '@ohos.arkui.stateManagement';
@Entry
@Component
struct DateExample {
  selectedDate: Date = UIUtils.makeObserved(new Date('2021-08-08'));

  build() {
    Column() {
      Text(`${this.selectedDate}`)
      Button('increase the year by 1')
        .margin(10)
        .onClick((e: ClickEvent) => {
          this.selectedDate.setFullYear(this.selectedDate.getFullYear() + 1);
        })
      Button('increase the month by 1')
        .margin(10)
        .onClick((e: ClickEvent) => {
          this.selectedDate.setMonth(this.selectedDate.getMonth() + 1);
        })
      Button('increase the day by 1')
        .margin(10)
        .onClick((e: ClickEvent) => {
          this.selectedDate.setDate(this.selectedDate.getDate() + 1);
        })
    }.width('100%')
  }
}
```

### makeObserved与interface字面量配合使用

```ts
'use static'

import { Entry, Component, Column, Text, ClickEvent } from '@ohos.arkui.component';
import { UIUtils } from '@ohos.arkui.stateManagement';
interface Info {
  name: string,
  age: number
}
@Entry
@Component
struct Index {
  info: Info = UIUtils.makeObserved({ name: 'Jack', age: 25} as Info) as Info;
  build() {
    Column() {
      Text(`info.name: ${this.info.name}`)
        .onClick((e: ClickEvent) => {
          this.info.name = 'Tom';
        })
    }
  }
}
```

