# \@Param装饰器：组件外部输入

\@Param表示组件外部输入，接收从父组件传入的变量，若数据源为状态变量，还能与之单向同步。

## 概述

\@Param装饰器，用于[\@ComponentV2](./arkts-static-componentv2.md#componentv2)装饰的自定义组件中，定义组件从外部传入的状态。\@Param装饰的变量为状态变量，具有观察变化的能力，当它变化时，会触发绑定的UI组件刷新。\@Param装饰的变量为只读变量，因此无法在组件内部直接修改。

\@Param装饰器具有以下能力：

- \@Param装饰的变量支持本地初始化，但不允许在组件内部直接修改。
- \@Param装饰的变量能够从父组件传入初始化，如果传入的数据源是状态变量，数据源的修改会同步给\@Param。

- \@Param装饰的变量变化时，会刷新使用该变量的组件。
- \@Param支持观察Object、class、string、number、boolean、enum、interface等基本类型以及[Array](#装饰Array类型变量)、[Date](#装饰date类型变量)、[Map](#装饰map类型变量)、[Set](#装饰set类型变量)等内置类型。
- \@Param支持null、undefined以及[联合类型](#联合类型)。

在静态语言上下文中使用时，需要导入装饰器：

```ts
import { Param } from '@ohos.arkui.stateManagement';
```

## 装饰器说明

| \@Param变量装饰器  | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| 装饰器参数         | 无                                                           |
| 允许装饰的变量类型 | Object、class、string、number、boolean、enum、interface等基本类型以及Array、Date、Map、Set等内嵌类型。支持null、undefined以及联合类型。 |
| 初始化规则         | **定义本地默认值时：**<br/>- 支持从父组件传入变量（含undefined类型），此时优先使用传入值进行初始化。<br/>- 若父组件未传值，则使用本地默认值进行初始化。<br/>**未定义本地默认值时：**<br/>必须从父组件传入变量进行初始化。 |
| 同步规则           | **在子组件使用时：**<br>- 与父组件中传入的状态变量数据源（即\@Local或\@Param装饰的变量）进行同步。<br/>- 当父组件传入的变量改变时（含undefined类型）会更新\@Param。<br/>**在父组件使用时：**<br/>- 可以初始化子组件的\@Param变量。<br/>- \@Param变量的变化会同步给子组件的\@Param变量。 |

## 观察变化

使用\@Param装饰的变量具有被观测变化的能力。当装饰的变量发生变化时，会触发该变量绑定的UI组件刷新。

- 当装饰boolean、string、number类型时，可观察数据源同步变化。

  ```ts
  'use static'
  
  import { Entry, ComponentV2, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
  import { Local, Param, Require } from '@ohos.arkui.stateManagement';
  @Entry
  @ComponentV2
  struct Index {
    @Local count: number = 0;
    @Local message: string = 'Hello';
    @Local flag: boolean = false;
    build() {
      Column() {
        Text(`${this.count}`)
        Text(`${this.message}`)
        Text(`${this.flag}`)
        Button('change Local')
          .onClick((e: ClickEvent) => {
            // 数据源变量修改，会同步给\@Param
            this.count++;
            this.message += ' World';
            this.flag = !this.flag;
        })
        Child({
          count: this.count,
          message: this.message,
          flag: this.flag
        })
      }
    }
  }
  @ComponentV2
  struct Child {
    @Require @Param count: number;
    @Require @Param message: string;
    @Require @Param flag: boolean;
    build() {
      Column() {
        Text(`Param ${this.count}`)
        Text(`Param ${this.message}`)
        Text(`Param ${this.flag}`)
      }
    }
  }
  ```

- 当装饰的变量类型为类对象时，仅可以观察到对类对象整体赋值的变化，无法直接观察到对类成员属性赋值的变化，对类成员属性的观察依赖[\@ObservedV2和\@Trace](./arkts-static-new-observedV2-and-trace.md)装饰器。

  ```ts
  'use static'
  
  import { Entry, ComponentV2, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
  import { Local, Param, ObservedV2, Trace, Require } from '@ohos.arkui.stateManagement';
  class RawObject {
    name: string;
    constructor(name: string) {
      this.name = name;
    }
  }
  @ObservedV2
  class ObservedObject {
    @Trace name: string;
    constructor(name: string) {
      this.name = name;
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    @Local rawObject: RawObject = new RawObject('rawObject');
    @Local observedObject: ObservedObject = new ObservedObject('observedObject');
    build() {
      Column() {
        Text(`${this.rawObject.name}`)
        Text(`${this.observedObject.name}`)
        Button('change object')
          .onClick((e: ClickEvent) => {
            // 对类对象整体的修改均能观察到
            this.rawObject = new RawObject('new rawObject');
            this.observedObject = new ObservedObject('new observedObject');
        })
        Button('change name')
          .onClick((e: ClickEvent) => {
            // @Local与@Param均不具备观察类对象属性的能力，因此对rawObject.name的修改无法观察到
            this.rawObject.name = 'new rawObject name';
            // 由于ObservedObject的name属性被@Trace装饰，因此对observedObject.name的修改能被观察到
            this.observedObject.name = 'new observedObject name';
        })
        Child({
          rawObject: this.rawObject,
          observedObject: this.observedObject
        })
      }
    }
  }
  @ComponentV2
  struct Child {
    @Require @Param rawObject: RawObject;
    @Require @Param observedObject: ObservedObject;
    build() {
      Column() {
        Text(`${this.rawObject.name}`)
        Text(`${this.observedObject.name}`)
      }
    }  
  }
  ```

- 装饰的变量为简单类型数组时，可观察数组整体或数组项变化。

  ```ts
  'use static'
  
  import { Entry, ComponentV2, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
  import { Local, Param, Require } from '@ohos.arkui.stateManagement';
  @Entry
  @ComponentV2
  struct Index {
    @Local numArr: number[] = [1, 2, 3, 4, 5];
    @Local dimensionTwo: number[][] = [[1, 2, 3], [4, 5, 6]];
    build() {
      Column() {
        Text(`${this.numArr[0]}`)
        Text(`${this.numArr[1]}`)
        Text(`${this.numArr[2]}`)
        Text(`${this.dimensionTwo[0][0]}`)
        Text(`${this.dimensionTwo[1][1]}`)
        Button('change array item')
          .onClick((e: ClickEvent) => {
            this.numArr[0]++;
            this.numArr[1] += 2;
            this.dimensionTwo[0][0] = 0;
            this.dimensionTwo[1][1] = 0;
          })
        Button('change whole array')
          .onClick((e: ClickEvent) => {
            this.numArr = [5, 4, 3, 2, 1];
            this.dimensionTwo = [[7, 8, 9], [0, 1, 2]];
          })
        Child({
          numArr: this.numArr,
          dimensionTwo: this.dimensionTwo
        })
      }
    }
  }
  @ComponentV2
  struct Child {
    @Require @Param numArr: number[];
    @Require @Param dimensionTwo: number[][];
    
    build() {
      Column() {
        Text(`${this.numArr[0]}`)
        Text(`${this.numArr[1]}`)
        Text(`${this.numArr[2]}`)
        Text(`${this.dimensionTwo[0][0]}`)
        Text(`${this.dimensionTwo[1][1]}`)
      }
    }
  }
  ```

- 当装饰内置类型时，可以观察到变量整体赋值及API调用带来的变化。

  | 类型  | 可观察变化的API                                              |
  | ----- | ------------------------------------------------------------ |
  | Array | push, pop, shift, unshift, splice, copyWithin, fill, reverse, sort |
  | Date  | setFullYear, setMonth, setDate, setHours, setMinutes, setSeconds, setMilliseconds, setTime, setUTCFullYear, setUTCMonth, setUTCDate, setUTCHours, setUTCMinutes, setUTCSeconds, setUTCMilliseconds |
  | Map   | set, clear, delete                                           |
  | Set   | add, clear, delete                                           |


- 当装饰interface字面量类型时，仅可以观察到字面量整体的变化，无法观察到属性的变化，可以使用[makeObserved接口](./arkts-static-new-makeObserved.md)实现对字面量属性的观察。

  ```ts
  'use static'
  
  import { Entry, ComponentV2, Column, Text, ClickEvent, Button } from '@ohos.arkui.component';
  import { Local, Param, Require } from '@ohos.arkui.stateManagement';
  interface Info {
    name: string;
    age: number;
  }
  @Entry
  @ComponentV2
  struct Index {
    // 装饰字面量
    @Local info: Info = { name: 'Jack', age: 25 } as Info;
    build() {
      Column() {
        Text(`Local info.name: ${this.info.name}`)
        Text(`Local info.age: ${this.info.age}`)
        Button('Local change info')
          .onClick((e: ClickEvent) => {
            this.info = { name: 'Tom', age: 18 } as Info; // 变化可观察
          })
        Button('Local change info.name')
          .onClick((e: ClickEvent) => {
            this.info.name = 'Lucy'; // 变化无法观察
          })
        Child({info: this.info})
      }
    }
  }
  @ComponentV2
  struct Child {
    @Require @Param info: Info;
    build() {
      Column() {
        Text(`Param info.name: ${this.info.name}`)
        Text(`Param info.age: ${this.info.age}`)
        Button('Param change info.name')
          .onClick((e: ClickEvent) => {
            this.info.name = 'Mary'; // 变化无法观察
          })
      }
    }
  }
  ```

## 限制条件

- \@Param装饰器只能在\@ComponentV2装饰器的自定义组件中使用。

  ```ts
  @ComponentV2
  struct MyComponent {
    @Param message: string = 'Hello World'; // 正确用法
    build() {
    }
  }
  @Component
  struct TestComponent {
    @Param message: string = 'Hello World'; // 错误用法，编译时报错
    build() {
    }
  }
  ```

- \@Param装饰的变量表示组件外部输入，需要初始化。支持使用本地初始值或外部传入值进行初始化。必须存在本地初始值或外部传入值，当二者同时存在时，优先使用外部传入值。

  ```ts
  'use static'
  
  import { Entry, ComponentV2, Column, Text, ClickEvent } from '@ohos.arkui.component';
  import { Local, Param, Require } from '@ohos.arkui.stateManagement';
  @ComponentV2
  struct ChildComponent {
    @Param param1: string = 'Initialize local';
    @Param param2: string = 'Initialize local and put in';
    @Require @Param param3: string;
    @Param param4: string; // 错误用法，外部未传入初始化且本地也无初始值，编译报错
    build() {
      Column() {
        Text(`${this.param1}`) // 本地初始化，显示Initialize local
        Text(`${this.param2}`) // 外部传入初始化，显示Put in
        Text(`${this.param3}`) // 外部传入初始化，显示Put in
      }
    }
  }
  @Entry
  @ComponentV2
  struct MyComponent {
    @Local message: string = 'Put in';
    build() {
      Column() {
        ChildComponent({
          param2: this.message,
          param3: this.message
        })
      }
    }
  }
  ```

- 使用`@Param`装饰的变量在子组件中无法被直接修改。但是，如果装饰的变量是对象类型，在子组件中可以修改对象的属性。

  ```ts
  'use static'
  
  import { Entry, ComponentV2, Column, Text, ClickEvent, Button } from '@ohos.arkui.component';
  import { Local, Param, ObservedV2, Trace, Require } from '@ohos.arkui.stateManagement';
  @ObservedV2
  class Info {
    @Trace name: string;
    constructor(name: string) {
      this.name = name;
    }
  }
  @Entry
  @ComponentV2
  struct Index {
    @Local info: Info = new Info('Tom');
    build() {
      Column() {
        Text(`Parent info.name ${this.info.name}`)
        Button('Parent change info')
          .onClick((e: ClickEvent) => {
            // 父组件更改@Local变量，会同步子组件对应@Param变量
            this.info = new Info('Lucy');
        })
        Child({ info: this.info })
      }
    }
  }
  @ComponentV2
  struct Child {
    @Require @Param info: Info;
    build() {
      Column() {
        Text(`info.name: ${this.info.name}`)
        Button('change info')
          .onClick((e: ClickEvent) => {
            // 错误用法，不允许在子组件中更改@Param变量，编译时会报错
            this.info = new Info('Jack');
          })
        Button('Child change info.name')
          .onClick((e: ClickEvent) => {
            // 允许在子组件中更改对象中属性，该修改会同步到父组件数据源上，当属性被@Trace装饰时，可观测到对应UI刷新
            this.info.name = 'Jack';
          })
      }
    }
  }
  ```

## 使用场景

### 从父组件到子组件变量传递与同步

\@Param能够接受父组件\@Local或\@Param传递的数据并与之变化同步。

```ts
'use static'

import { Entry, ComponentV2, Column, ForEach, Button, Text, ClickEvent } from '@ohos.arkui.component';
import { Local, Param, ObservedV2, Trace, Require } from '@ohos.arkui.stateManagement';
@ObservedV2
class Region {
  @Trace x: number;
  @Trace y: number;
  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}
@ObservedV2
class Info {
  @Trace name: string;
  @Trace age: number;
  @Trace region: Region;
  constructor(name: string, age: number, x: number, y: number) {
    this.name = name;
    this.age = age;
    this.region = new Region(x, y);
  }
}
@Entry
@ComponentV2
struct Index {
  @Local infoList: Info[] = [new Info('Alice', 8, 0, 0), new Info('Barry', 10, 1, 20), new Info('Cindy', 18, 24, 40)];
  build() {
    Column() {
      ForEach(this.infoList, (info: Info, index: int) => {
        MiddleComponent({ info: info })
      })
      Button('change')
        .onClick((e: ClickEvent) => {
          this.infoList[0] = new Info('Atom', 40, 27, 90);
          this.infoList[1].name = 'Bob';
          this.infoList[2].region = new Region(7, 9);
        })
    }
  }
}
@ComponentV2
struct MiddleComponent {
  @Require @Param info: Info;
  build() {
    Column() {
      Text(`name: ${this.info.name}`)
      Text(`age: ${this.info.age}`)
      SubComponent({ region: this.info.region })
    }
  }
}
@ComponentV2
struct SubComponent {
  @Require @Param region: Region;
  build() {
    Column() {
      Text(`region: ${this.region.x}-${this.region.y}`)
    }
  }
}
```

### 装饰Array类型变量

当装饰Array类型时，可以观察到Array整体及其元素的变化。通过API操作更改数组内容也能被观察到。

```ts
'use static'

import { Entry, ComponentV2, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { Local, Param, Require } from '@ohos.arkui.stateManagement';
@Entry
@ComponentV2
struct Index {
  @Local arr: int[] = [0, 1, 2];
  build() {
    Column() {
      Text(`Local ${this.arr}`)
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
      Button(`reset`).onClick((e: ClickEvent) => {
        this.arr = [0, 1, 2];
      })
      Child({ arr: this.arr })
    }
  }
}
@ComponentV2
struct Child {
  @Require @Param arr: int[];
  build() {
    Column() {
	  Text(`Param ${this.arr}`)
    }
  }
}
```

### 装饰Date类型变量

当装饰Date类型时，可以观察到数据源对Date整体的赋值及其API操作的变化。

```ts
'use static'

import { Entry, ComponentV2, Column, Button, Text, ClickEvent } from '@ohos.arkui.component';
import { Local, Param } from '@ohos.arkui.stateManagement';
@ComponentV2
struct DateComponent {
  @Param selectedDate: Date = new Date('2024-01-01');

  build() {
    Column() {
      Text(`${this.selectedDate}`)
    }
  }
}

@Entry
@ComponentV2
struct ParentComponent {
  @Local parentSelectedDate: Date = new Date('2021-08-08');

  build() {
    Column() {
      Button('parent update the new date')
        .margin(10)
        .onClick((e: ClickEvent) => {
          this.parentSelectedDate = new Date('2023-07-07');
        })
      Button('increase the year by 1')
        .margin(10)
        .onClick((e: ClickEvent) => {
          this.parentSelectedDate.setFullYear(this.parentSelectedDate.getFullYear() + 1);
        })
      Button('increase the month by 1')
        .margin(10)
        .onClick((e: ClickEvent) => {
          this.parentSelectedDate.setMonth(this.parentSelectedDate.getMonth() + 1);
        })
      Button('parent increase the day by 1')
        .margin(10)
        .onClick((e: ClickEvent) => {
          this.parentSelectedDate.setDate(this.parentSelectedDate.getDate() + 1);
        })
      DateComponent({ selectedDate: this.parentSelectedDate })
    }
  }
}
```

### 装饰Map类型变量

当装饰Map类型时，可以观察到数据源对Map整体的赋值及其API操作带来的变化。

```ts
'use static'

import { Entry, ComponentV2, Row, Column, ForEach, Text, Divider, Button, ClickEvent } from '@ohos.arkui.component';
import { Local, Param } from '@ohos.arkui.stateManagement';
@ComponentV2
struct Child {
  @Param value: Map<number, string> = new Map<number, string>()

  build() {
    Column() {
      ForEach(Array.from(this.value.entries()), (item: [number, string]) => {
        Text(`${item[0]}`).fontSize(30)
        Text(`${item[1]}`).fontSize(30)
        Divider()
      })
    }
  }
}
@Entry
@ComponentV2
struct MapSample {
  @Local message: Map<number, string> = new Map<number, string>([[0, 'a'], [1, 'b'], [3, 'c']])

  build() {
    Row() {
      Column() {
        Child({ value: this.message })
        Button('init map').onClick((e: ClickEvent) => {
          this.message = new Map<number, string>([[0, 'a'], [1, 'b'], [3, 'c']])
        })
        Button('set new one').onClick((e: ClickEvent) => {
          this.message.set(4, 'd')
        })
        Button('clear').onClick((e: ClickEvent) => {
          this.message.clear()
        })
        Button('replace the first one').onClick((e: ClickEvent) => {
          this.message.set(0, 'aa')
        })
        Button('delete the first one').onClick((e: ClickEvent) => {
          this.message.delete(0)
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 装饰Set类型变量

当装饰Set类型时，可以观察到数据源对Set整体的赋值及其API操作带来的变化。

```ts
'use static'

import { Entry, ComponentV2, Row, Column, ForEach, Text, Divider, Button, ClickEvent } from '@ohos.arkui.component';
import { Local, Param } from '@ohos.arkui.stateManagement';
@ComponentV2
struct Child {
  @Param message: Set<number> = new Set<number>()

  build() {
    Column() {
      ForEach(Array.from(this.message.entries()), (item: [number, number]) => {
        Text(`${item[0]}`).fontSize(30)
        Divider()
      })
    }
    .width('100%')
  }
}
@Entry
@ComponentV2
struct SetSample {
  @Local message: Set<number> = new Set<number>([0, 1, 2, 3, 4])

  build() {
    Row() {
      Column() {
        Child({ message: this.message })
        Button('init set').onClick((e: ClickEvent) => {
          this.message = new Set<number>([0, 1, 2, 3, 4])
        })
        Button('set new one').onClick((e: ClickEvent) => {
          this.message.add(5)
        })
        Button('clear').onClick((e: ClickEvent) => {
          this.message.clear()
        })
        Button('delete the first one').onClick((e: ClickEvent) => {
          this.message.delete(0)
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### 联合类型

\@Param支持null、undefined以及联合类型。以下示例中，count类型为number | null，点击改变count的类型时，UI会自动刷新。

```ts
'use static'

import { Entry, ComponentV2, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { Local, Param } from '@ohos.arkui.stateManagement';
@Entry
@ComponentV2
struct Index {
  @Local count: number | null = 0;

  build() {
    Column() {
      MyComponent({ count: this.count })
      Button('change')
        .onClick((e: ClickEvent) => {
          this.count = null;
        })
    }
  }
}

@ComponentV2
struct MyComponent {
  @Param count: number | null = 0;

  build() {
    Column() {
      Text(`count(${this.count})`)
    }
  }
}
```