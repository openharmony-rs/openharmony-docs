# \@Monitor装饰器：状态变量修改监听

为了增强状态管理框架对状态变量变化的监听能力，开发者可以使用\@Monitor装饰器对状态变量进行监听。

>**说明：**
>
>\@Monitor装饰器从API version 23开始支持。
>
>从API版本26.0.0开始，该装饰器新增支持通配符能力，用于模糊监听对象的内部变化。

## 概述

\@Monitor装饰器用于监听状态变量修改，使得状态变量具有深度监听的能力：

- \@Monitor装饰器支持在[\@ComponentV2](./arkts-static-componentv2.md)装饰的自定义组件中使用，未被状态变量装饰器[\@Local](./arkts-static-new-local.md)、[\@Param](./arkts-static-new-param.md)、[\@Provider、\@Consumer](./arkts-static-new-provider-and-consumer.md)、[\@Computed](./arkts-static-new-computed.md)装饰的变量无法被\@Monitor监听到变化。

- \@Monitor装饰器支持在类中与[\@ObservedV2、\@Trace](./arkts-static-new-observedV2-and-trace.md)配合使用，不允许在未被\@ObservedV2装饰的类中使用\@Monitor装饰器。未被\@Trace装饰的属性无法被\@Monitor监听到变化。
- 当观测的属性变化时，\@Monitor装饰器定义的回调方法将被调用。判断属性是否变化使用的是严格相等（===），当严格相等判断的结果是false（即不相等）的情况下，就会触发\@Monitor的回调。当在一次事件中多次改变同一个属性时，将会使用初始值和最终值进行比较以判断是否变化。
- 单个\@Monitor装饰器能够同时监听多个属性的变化，当这些属性在一次事件中共同变化时，只会触发一次\@Monitor的回调方法。
- \@Monitor装饰器具有深度监听的能力，能够监听嵌套类、多维数组、对象数组中指定项的变化。对于嵌套类、对象数组中成员属性变化的监听要求该类被\@ObservedV2装饰且该属性被\@Trace装饰。
- 在继承类场景中，可以在父子组件中对同一个属性分别定义\@Monitor进行监听，当属性变化时，父子组件中定义的\@Monitor回调均会被调用。
- 和\@Watch装饰器类似，开发者需要自己定义回调函数，区别在于\@Watch装饰器将函数名作为参数，而\@Monitor直接装饰回调函数。\@Monitor与[\@Watch](./arkts-static-watch.md)的对比可以查看[\@Monitor与\@Watch的对比](#monitor与watch对比)。

- 从API版本26.0.0开始，支持在监听路径中设置通配符“*”，用于模糊监听对象内部变化，包括@ObservedV2中任意@Trace属性变化，内置类型（Array、Map、Date、Set）的API调用引起的变化等。详情见[监听包含通配符的路径](#监听包含通配符的路径)。

在静态上下文中使用时，需导入装饰器：

```ts
import { Monitor } from '@kit.ArkUI';
```

## 装饰器说明

| \@Monitor属性装饰器 | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| 装饰器参数          | 字符串类型的对象属性名列表。可同时监听多个对象属性，例如@Monitor(['prop1', 'prop2'])。可监听深层的属性变化，如多维数组中的某一个元素，嵌套对象或对象数组中的某一个属性。详见[监听变化](#监听变化)。从API版本26.0.0开始，支持在路径中包含通配符“*”用于模糊监听对象内部的变化。详情见[监听包含通配符的路径](#监听包含通配符的路径)。 |
| 装饰对象            | \@Monitor装饰成员方法。当监听的属性发生变化时，会触发该回调方法。该回调方法以[IMonitor类型](../../reference/apis-arkui/arkui-ts/ts-state-management-monitor-static.md#imonitor)的变量作为参数，开发者可以从该参数中获取变化前后的相关信息。 |

## 接口说明

IMonitor类型和IMonitorValue\<T\>类型的接口说明参考API文档：[@Monitor](../../reference/apis-arkui/arkui-ts/ts-state-management-monitor-static.md)

## 监听变化

### 在\@ComponentV2装饰的自定义组件中使用\@Monitor

使用\@Monitor监听的状态变量发生变化时，会触发\@Monitor的回调方法。

- \@Monitor监听的变量需要被\@Local、\@Param、\@Provider、\@Consumer、\@Computed装饰，未被状态变量装饰器装饰的变量在变化时无法被监听。\@Monitor可以同时监听多个状态变量，这些变量名之间用","隔开。

   ```ts
   'use static'
   
   import { Button, Column, ComponentV2, Entry, IMonitor, Local, Monitor } from '@kit.ArkUI';
   @Entry
   @ComponentV2
   struct Index {
     @Local message: string = 'Hello World';
     @Local name: string = 'Tom';
     // 监听message、name的变化
     @Monitor(['message', 'name'])
     onStrChange(monitor: IMonitor) {
       monitor.dirty.forEach((path: string) => {
         console.info(`${path} changed from ${monitor.value<Any>(path)?.before} to ${monitor.value<Any>(path)?.now}`);
       });
     }
     build() {
       Column() {
         Button('change string')
           .onClick((e) => {
             // 修改message、name的值
             this.message += '!';
             this.name = 'Jack';
         })
       }
     }
   }
   ```

- \@Monitor监听的状态变量为类对象时，仅能监听对象整体的变化。监听类属性的变化需要类属性被\@Trace装饰。

   ```ts
   'use static'
   
   import { Button, Column, ComponentV2, Entry, IMonitor, Local, Monitor, Text } from '@kit.ArkUI';
   
   export class Info {
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
     @Monitor(['info'])
     infoChange(monitor: IMonitor) {
       console.info('info change');
     }
     @Monitor(['info.name'])
     infoPropertyChange(monitor: IMonitor) {
       console.info('info name change');
     }
     build() {
       Column() {
         Text(`name: ${this.info.name}, age: ${this.info.age}`)
         Button('change info')
           .onClick((e) => {
             this.info = new Info('Lucy', 18); // 能够监听到
           })
         Button('change info.name')
           .onClick((e) => {
             this.info.name = 'Jack'; // 监听不到
           })
       }
     }
   }
   ```

### 在\@ObservedV2装饰的类中使用\@Monitor

使用\@Monitor监听的属性发生变化时，会触发\@Monitor的回调方法。

- \@Monitor监听的对象属性需要被\@Trace装饰，未被\@Trace装饰的属性的变化无法被监听。\@Monitor可以同时监听多个属性，这些属性之间用","隔开。

   ```ts
   'use static'
   
   import { Button, Column, ComponentV2, Entry, IMonitor, Local, Monitor, ObservedV2, Text, Trace } from '@kit.ArkUI';
   
   @ObservedV2
   export class Info {
     @Trace name: string = 'Tom';
     @Trace region: string = 'North';
     @Trace job: string = 'Teacher';
     age: number = 25;
     // name被@Trace装饰，能够监听变化
     @Monitor(['name'])
     onNameChange(monitor: IMonitor): void {
       console.info(`name change from ${monitor.value<string>()?.before} to ${monitor.value<string>()?.now}`);
     }
     // age未被@Trace装饰，不能监听变化
     @Monitor(['age'])
     onAgeChange(monitor: IMonitor): void {
       console.info(`age change from ${monitor.value<number>()?.before} to ${monitor.value<number>()?.now}`);
     }
     // region与job均被@Trace装饰，能够监听变化
     @Monitor(['region', 'job'])
     onChange(monitor: IMonitor): void {
       monitor.dirty.forEach((path: string) => {
         console.info(`${path} change from ${monitor.value<string>(path)?.before} to ${monitor.value<string>(path)?.now}`);
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
           .onClick((e) => {
             this.info.name = 'Jack'; // 能够触发onNameChange方法
           })
         Button('change age')
           .onClick((e) => {
             this.info.age = 26; // 不能够触发onAgeChange方法
           })
         Button('change region')
           .onClick((e) => {
             this.info.region = 'South'; // 能够触发onChange方法
           })
         Button('change job')
           .onClick((e) => {
             this.info.job = 'Driver'; // 能够触发onChange方法
           })
       }
     }
   }
   ```

- \@Monitor可以监听深层属性的变化，该深层属性需要被@Trace装饰。

   ```ts
   'use static'
   
   import { Button, Column, ComponentV2, Entry, IMonitor, Local, Monitor, ObservedV2, Text, Trace } from '@kit.ArkUI';
   
   @ObservedV2
   export class Inner {
     @Trace num: number = 0;
   }
   @ObservedV2
   export class Outer {
     @Trace inner: Inner = new Inner();
     @Monitor(['inner.num'])
     onChange(monitor: IMonitor): void {
       console.info(`inner.num change from ${monitor.value<number>()?.before} to ${monitor.value<number>()?.now}`);
     }
   }
   @Entry
   @ComponentV2
   struct Index {
     outer: Outer = new Outer();
     build() {
       Column() {
         Button('change name')
           .onClick((e) => {
             this.outer.inner.num = 100; // 能够触发onChange方法
           })
       }
     }
   }
   ```

- 在继承类场景下，可以在继承链中对同一个属性进行多次监听。

   ```ts
   'use static'
   
   import { Button, Column, ComponentV2, Entry, IMonitor, Monitor, ObservedV2, Trace } from '@kit.ArkUI';
   
   @ObservedV2
   export class Base {
     @Trace name: string;
     // 基类监听name属性
     @Monitor(['name'])
     onBaseNameChange(monitor: IMonitor): void {
       console.info('Base Class name change');
     }
     constructor(name: string) {
       this.name = name;
     }
   }
   @ObservedV2
   export class Derived extends Base {
     @Trace age: int = 0;
     // 继承类监听name属性
     @Monitor(['name'])
     onDerivedNameChange(monitor: IMonitor): void {
       console.info('Derived Class name change');
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
           .onClick((e) => {
             this.derived.name = 'BBB'; // 能够先后触发onBaseNameChange、onDerivedNameChange方法
           })
       }
     }
   }
   ```

### 通用监听能力

- \@Monitor支持对数组中的项进行监听，包括多维数组，对象数组。\@Monitor无法监听内置类型（Array、Map、Date、Set）的API调用引起的变化。当\@Monitor监听数组整体时，只能观测到数组整体的赋值。可以通过监听数组的长度变化来判断数组是否有插入、删除等变化。当前仅支持使用"."的方式表达深层属性、数组项的监听。

   ```ts
   'use static'
   
   import { Button, Column, ComponentV2, Entry, IMonitor, Monitor, ObservedV2, Trace } from '@kit.ArkUI';
   
   @ObservedV2
   export class Info {
     @Trace name: string;
     @Trace age: number;
     
     constructor(name: string, age: number) {
       this.name = name;
       this.age = age;
     }
   }
   @ObservedV2
   export class ArrMonitor {
     @Trace dimensionTwo: number[][] = [[1,1,1],[2,2,2],[3,3,3]];
     @Trace dimensionThree: number[][][] = [[[1],[2],[3]],[[4],[5],[6]],[[7],[8],[9]]];
     @Trace infoArr: Info[] = [new Info('Jack', 24), new Info('Lucy', 18)];
     // dimensionTwo为二维简单类型数组，且被@Trace装饰，能够观测里面的元素变化
     @Monitor(['dimensionTwo.0.0', 'dimensionTwo.1.1'])
     onDimensionTwoChange(monitor: IMonitor): void {
       monitor.dirty.forEach((path: string) => {
         console.info(`dimensionTwo path: ${path} change from ${monitor.value<number>(path)?.before} to ${monitor.value<number>(path)?.now}`);
       })
     }
     // dimensionThree为三维简单类型数组，且被@Trace装饰，能够观测里面的元素变化
     @Monitor(['dimensionThree.0.0.0', 'dimensionThree.1.1.0'])
     onDimensionThreeChange(monitor: IMonitor): void {
       monitor.dirty.forEach((path: string) => {
         console.info(`dimensionThree path: ${path} change from ${monitor.value<number>(path)?.before} to ${monitor.value<number>(path)?.now}`);
       })
     }
     // Info类中属性name、age均被@Trace装饰，能够监听到变化
     @Monitor(['infoArr.0.name', 'infoArr.1.age'])
     onInfoArrPropertyChange(monitor: IMonitor): void {
       monitor.dirty.forEach((path: string) => {
         console.info(`infoArr path:${path} change from ${monitor.value<Any>(path)?.before} to ${monitor.value<Any>(path)?.now}`);
       })
     }
     // infoArr被@Trace装饰，能够监听到infoArr整体赋值的变化
     @Monitor(['infoArr'])
     onInfoArrChange(monitor: IMonitor): void {
       console.info('infoArr whole change');
     }
     // 能够监听到infoArr的长度变化
     @Monitor(['infoArr.length'])
     onInfoArrLengthChange(monitor: IMonitor): void {
       console.info('infoArr length change');
     }
   }
   @Entry
   @ComponentV2
   struct Index {
     arrMonitor: ArrMonitor = new ArrMonitor();
     build() {
       Column() {
         Button('Change dimensionTwo')
           .onClick((e) => {
             // 能够触发onDimensionTwoChange方法  
             this.arrMonitor.dimensionTwo[0][0]++; 
             this.arrMonitor.dimensionTwo[1][1]++; 
           })
         Button('Change dimensionThree')
           .onClick((e) => {
             // 能够触发onDimensionThreeChange方法
             this.arrMonitor.dimensionThree[0][0][0]++;
             this.arrMonitor.dimensionThree[1][1][0]++; 
           })
         Button('Change info property')
           .onClick((e) => {
             // 能够触发onInfoArrPropertyChange方法
             this.arrMonitor.infoArr[0].name = 'Tom'; 
             this.arrMonitor.infoArr[1].age = 19; 
           })
         Button('Change whole infoArr')
           .onClick((e) => {
             // 能够触发onInfoArrChange、onInfoArrPropertyChange、onInfoArrLengthChange方法
             this.arrMonitor.infoArr = [new Info('Cindy', 8)]; 
           })
         Button('Push new info to infoArr')
           .onClick((e) => {
             // 能够触发onInfoArrPropertyChange、onInfoArrLengthChange方法
             this.arrMonitor.infoArr.push(new Info('David', 50)); 
           })
       }
     }
   }
   ```

- 对象整体改变，但监听的属性不变时，不触发\@Monitor回调。

   下面的示例按照Step1-Step2-Step3的顺序点击，表现为代码注释中的行为。

   如果只点击Step2或Step3，改变name、age的值，此时会触发onNameChange和onAgeChange方法。

   ```ts
   'use static'
   
   import { Button, Column, ComponentV2, Entry, IMonitor, Monitor, ObservedV2, Trace } from '@kit.ArkUI';
   
   @ObservedV2
   export class Info {
     @Trace person: Person;
     @Monitor(['person.name'])
     onNameChange(monitor: IMonitor): void {
       console.info(`name change from ${monitor.value<string>()?.before} to ${monitor.value<string>()?.now}`);
     }
     @Monitor(['person.age'])
     onAgeChange(monitor: IMonitor): void {
       console.info(`age change from ${monitor.value<number>()?.before} to ${monitor.value<number>()?.now}`);
     }
     constructor(name: string, age: number) {
       this.person = new Person(name, age);
     }
   }
   @ObservedV2
   export class Person {
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
           .onClick((e) => {
             this.info.person = new Person('Jack', 25);  // 能够触发onNameChange方法，不触发onAgeChange方法
           })
         Button('Step2: Only change age')
           .onClick((e) => {
             this.info.person = new Person('Jack', 18);  // 能够触发onAgeChange方法，不触发onNameChange方法
           })
         Button('Step3: Change name and age')
           .onClick((e) => {
             this.info.person = new Person('Lucy', 19);  // 能够触发onNameChange、onAgeChange方法
           })
       }
     }
   }
   ```

- 在一次事件中多次改变被\@Monitor监听的属性，以最后一次修改为准。

   ```ts
   'use static'
   
   import { Button, Column, ComponentV2, Entry, IMonitor, Monitor, ObservedV2, Trace } from '@kit.ArkUI';
   
   @ObservedV2
   export class Frequence {
     @Trace count: number = 0;
     @Monitor(['count'])
     onCountChange(monitor: IMonitor): void {
       console.info(`count change from ${monitor.value<number>()?.before} to ${monitor.value<number>()?.now}`);
     }
   }
   @Entry
   @ComponentV2
   struct Index {
     frequence: Frequence = new Frequence();
     build() {
       Column() {
         Button('change count to 1000')
           .onClick((e) => {
             for (let i = 1; i <= 1000; i++) {
               this.frequence.count = i;
             }
           })
         Button('change count to 0 then to 1000')
           .onClick((e) => {
             for (let i = 999; i >= 0; i--) {
               this.frequence.count = i;
             }
             this.frequence.count = 1000; // 最终不触发onCountChange方法
           })
       }
     }
   }
   ```

在点击按钮"change count to 1000"后，会触发一次onCountChange方法，并输出日志"count change from 0 to 1000"。在点击按钮"change count to 0 then to 1000"后，由于事件前后属性count的值并没有改变，都为1000，所以不触发onCountChange方法。

## 监听包含通配符的路径

从API版本26.0.0开始，@Monitor支持通配符能力。通配符可以作为路径中的后缀，监听该路径最后确定值中的变化。该变化包括如@Trace属性的变化、内置类型（Array、Map、Set、Date）的API调用引起的变化等。

通配符路径的语法规则为：

- 通配符只能出现在路径末尾。
- 通配符不能出现在路径开头，也不能出现在路径中间。
- 一个路径中最多仅可以出现一个通配符。

合法的通配符路径示例为：

| 路径       | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| obj.*      | obj为@ObservedV2装饰的对象。监听该路径的@Monitor将在以下情况触发：<br>1、对obj整体赋值。<br>2、obj任意@Trace属性变化。 |
| arr.*      | arr为可观察数组。监听该路径的@Monitor将在以下情况触发：<br/>1、对arr整体赋值。<br>2、arr任意元素变化或数组长度变化。<br>3、调用数组的API（如push、pop、sort、fill、copyWithin等）。 |
| obj.objA.* | objA为@ObservedV2装饰的嵌套对象。监听该路径的@Monitor将在以下情况触发：<br>1、对obj整体赋值且objA变化。<br>2、对objA整体赋值。<br>3、objA任意@Trace属性变化。 |
| arr.1.*    | arr为嵌套可观察数组。监听该路径的@Monitor将在以下情况触发：<br/>1、对arr整体赋值且下标为1的数组发生变化。<br>2、arr下标为1的数组任意元素变化或数组长度变化。<br>3、调用arr下标为1的数组的API。 |

当修改嵌套对象中任意对象时，监听包含该对象的通配符路径遵循最终确定值原则，即通配符前的最后一个确定值变化时，才会触发监听回调。例如，监听上表的路径`obj.objA.*`时，`objA`为通配符前的最后一个确定值，对`obj`整体赋值，若`objA`赋值前后引用同一个对象，则不会触发回调。

此外，使用通配符时，IMonitor的dirty数组能正常包含通配符路径，但其对应的IMonitorValue的before值与now值都将为undefined。

### 使用通配符监听对象属性变化

当使用通配符监听对象时，对象的任意@Trace装饰的属性变化，或者对象本身被整体赋新值时，触发@Monitor回调。

``` TypeScript
'use static'

import { Entry, Text, Column, ComponentV2, Button,
  ObservedV2, Trace, Local, Monitor, IMonitor } from '@kit.ArkUI';
import hilog from '@ohos.hilog';

@ObservedV2
export class ClassA {
  @Trace public propA: int = 8;
  @Trace public propB: int = 99;

  constructor(a: int, b: int) {
    this.propA = a;
    this.propB = b;
  }
}

@Entry
@ComponentV2
struct MonitorWildcardObject {
  @Local cls: ClassA = new ClassA(100, 100);

  // 使用通配符
  @Monitor(['cls.*'])
  onClsChanged(m: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s', `onClsChanged, dirty: ${m.dirty.toString()}`);
  }

  build() {
    Column() {
      Button(`Change propA: ${this.cls.propA}`)
        .onClick(() => {
          this.cls.propA += 1; // 触发onClsChanged
        })
      Button(`Change propB: ${this.cls.propB}`)
        .onClick(() => {
          this.cls.propB += 1; // 触发onClsChanged
        })
      Button('Assign new object')
        .onClick(() => {
          this.cls = new ClassA(-200, -200); // 触发onClsChanged
        })
    }
  }
}
```

### 使用通配符监听嵌套对象属性变化

观察嵌套对象属性变化的示例如下。

``` TypeScript
'use static'

import { Entry, Text, Column, ComponentV2, Button,
  ObservedV2, Trace, Local, Monitor, IMonitor } from '@kit.ArkUI';
import hilog from '@ohos.hilog';

@ObservedV2
export class Person {
  @Trace public firstName: string = 'first';
  @Trace public lastName: string = 'last';
}

@ObservedV2
export class Class1 {
  @Trace public person: Person = new Person();
}

@ObservedV2
export class Class0 {
  @Trace public class1: Class1 = new Class1();
}

@Entry
@ComponentV2
struct MonitorWildcardNestedObject {
  @Local class0: Class0 = new Class0();

  // 使能通配符，监听嵌套对象
  @Monitor(['class0.class1.person.*'])
  onPersonChange(info: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s', 'onPersonChange, dirty: ' + info.dirty.toString());
  }

  build() {
    Column() {
      Button('1. Class0 = new Class')
        .onClick(() => {
          // @Monitor回调触发
          // 原因：class0, class1, person变更为新对象
          this.class0 = new Class0();
        })
      Button('2. Class0 = new Class, keep Class1')
        .onClick(() => {
          // 当class0为Class0类型时，@Monitor回调不触发
          // 原因：即使class0变化了，路径'class0.class1.person.*'中通配符前最后一个确定值person也没有改变
          if (this.class0 instanceof Class0) {
            let newClass0 = new Class0();
            newClass0.class1.person = (this.class0 as Class0).class1.person;
            this.class0 = newClass0;
          }
        })
      Button('3. Class0.class1 = new Class1')
        .onClick(() => {
          // 当class0为Class0类型时，@Monitor回调触发
          // 原因：class1、person变更为新对象
          if (this.class0 instanceof Class0) {
            (this.class0 as Class0).class1 = new Class1();
          }
        })
      Button('4. Class0.class1.person = new Person')
        .onClick(() => {
          // 当class0为Class0类型时，@Monitor回调触发
          // 原因：person变更为新对象
          if (this.class0 instanceof Class0) {
            (this.class0 as Class0).class1.person = new Person();
          }
        })
      Button('5. Class0....person.last update')
        .onClick(() => {
          // 当class0为Class0类型时，@Monitor回调触发
          // 原因：person的属性发生变化
          if (this.class0 instanceof Class0) {
            (this.class0 as Class0).class1.person.lastName += '+';
          }
        })
    }
  }
}
```

### 使用通配符监听数组对象的变化

使用配置项的@Monitor可以监听到数组的API调用。任意数组的方法被调用时，@Monitor回调都会被执行，即使数组为空或并未实际修改数组的内容。API包括`push`、`pop`、`shift`、`splice`、`unshift`、`copyWithin`、`fill`、`reverse`、`sort`。

``` TypeScript
'use static'

import { Entry, Text, Column, ComponentV2, Button,
  ObservedV2, Trace, Local, Monitor, IMonitor } from '@kit.ArkUI';
import hilog from '@ohos.hilog';

@ObservedV2
export class Person {
  @Trace public firstName: string = 'first';
  @Trace public lastName: string = 'last';

  constructor(first: string = 'no first', last: string = 'no last') {
    this.firstName = first;
    this.lastName = last;
  }
}

@Entry
@ComponentV2
struct MonitorWildcardArray {
  @Local topArray: Person[][] = this.makeNewTopArray();

  // 使能通配符
  @Monitor(['topArray.1.*'])
  topArrayMonitor1Star(monitor: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s', `TopArray[1]: ${monitor.dirty.toString()}`);
  }

  // 使能通配符
  @Monitor(['topArray.*'])
  topArrayMonitorStar(monitor: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s', `TopArray: ${monitor.dirty.toString()}`);
  }

  makeNewTopArray(): Person[][] {
    // 初始化数组
    return (new Array<Array<Person>>(
      new Array<Person>(new Person('Adrian'), new Person('Andrew'), new Person('Aaliyah'), new Person('Amir'), new Person('Angel')),
      new Array<Person>(new Person('Carter'), new Person('Charlie'), new Person('Cooper'), new Person('Cole'), new Person('Callie')),
      new Array<Person>(new Person('Daniel'), new Person('Dasy'), new Person('Dawson'), new Person('Dana'), new Person('Dalton')))
    );
  }

  build() {
    Column() {
      // topArrayMonitor1Star与topArrayMonitorStar回调均触发
      Button('topArray = new TopArray')
        .onClick(() => {
          this.topArray = this.makeNewTopArray();
        })

      // 当topArray[1][0]存在时，topArrayMonitor1Star回调触发，topArrayMonitorStar回调不触发
      Button('topArray[1][0] = new Person')
        .onClick(() => {
          if (this.topArray.length > 1 && this.topArray[1].length > 0) {
            this.topArray[1][0] = new Person();
          }
        })

      // 当topArray[0][1]存在时，topArrayMonitor1Star与topArrayMonitorStar回调均不触发
      Button('topArray[0][1] = new Person')
        .onClick(() => {
          if (this.topArray.length > 0 && this.topArray[0].length > 1) {
            this.topArray[0][1] = new Person();
          }
        })

      // 当topArray[1]存在时，topArrayMonitor1Star回调触发，topArrayMonitorStar回调不触发
      Button('topArray[1].push')
        .onClick(() => {
          if (this.topArray.length > 1 && this.topArray[1] instanceof Array) {
            this.topArray[1].push(new Person());
          }
        })

      // 当topArray的length大于2时，topArrayMonitor1Star与topArrayMonitorStar回调均触发
      Button('topArray.shift (length>2)')
        .onClick(() => {
          if (this.topArray.length > 2) {
            this.topArray.shift();
          }
        })

      // 当topArray[0]存在时，topArrayMonitor1Star回调不触发，topArrayMonitorStar回调触发
      Button('topArray[0] = new ArrayOfPerson')
        .onClick(() => {
          if (this.topArray.length > 0) {
            this.topArray[0] = new Array<Person>(new Person(), new Person());
          }
        })

      // 当topArray[1][0]存在时，topArrayMonitor1Star与topArrayMonitorStar回调均不触发
      Button('topArray[1][0].last update')
        .onClick(() => {
          if (this.topArray.length > 1 && this.topArray[1].length > 0 && this.topArray[1][0] instanceof Person) {
            this.topArray[1][0].lastName += '~';
          }
        })

      // topArrayMonitor1Star回调不触发，topArrayMonitorStar回调触发
      Button('topArray = new TopArray, keep [1]')
        .onClick(() => {
          let newTop = this.makeNewTopArray();
          newTop[1] = this.topArray[1]; // topArray.1未改变，路径'topArray.1.*'中通配符前最后一个确定值未改变
          this.topArray = newTop;
        })

      // topArrayMonitor1Star回调不触发，topArrayMonitorStar回调触发
      Button('topArray.push')
        .onClick(() => {
          this.topArray.push(new Array<Person>(new Person(), new Person()));
        })
    }
  }
}
```

### 使用通配符监听Date对象的变化

使用通配符可以监听Date对象的API调用。

```ts
@Monitor(['dateInstance.*'])
onDateChange(m: IMonitor) {
}
```

@Monitor会在以下情况回调：

- `dateInstance`被赋新值。
- 调用Date的任意API，包括`setFullYear`、`setMonth`、`setDate`、`setHours`、`setMinutes`、`setSeconds`、`setMilliseconds`、`setTime`、`setUTCFullYear`、`setUTCMonth`、`setUTCDate`、`setUTCHours`、`setUTCMinutes`、`setUTCSeconds`、`setUTCMilliseconds`。即使这些API未实际对Date的值产生更改，@Monitor回调也会触发。

使用通配符监听Date对象的示例如下。

``` TypeScript
'use static'

import { Entry, Text, Column, ComponentV2, Button,
  ObservedV2, Trace, Local, Monitor, IMonitor } from '@kit.ArkUI';
import hilog from '@ohos.hilog';

@Entry
@ComponentV2
struct MonitorWildcardDate {
  @Local date: Date = new Date();

  // 使能通配符
  @Monitor(['date.*'])
  onDateChanged(m: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s', `onDateChanged, dirty: ${m.dirty.toString()}`);
  }

  build() {
    Column() {
      // API调用触发onDateChanged
      Button(`date.setMilliseconds(1000)`)
        .onClick(() => {
          this.date.setMilliseconds(1000);
        })
      // API调用触发onDateChanged
      Button(`date.setTime(1000000)`)
        .onClick(() => {
          this.date.setTime(1000000);
        })
      // API调用触发onDateChanged
      Button(`Assign new Date`)
        .onClick(() => {
          this.date = new Date();
        })
      // 整体赋相同值，不触发onDateChanged
      Button(`Re-assign the same Date`)
        .onClick(() => {
          let sameDate = this.date;
          this.date = sameDate;
        })
    }
  }
}
```

### 使用通配符监听Map对象的变化

使用通配符可以监听Map对象的API调用。

```ts
@Monitor(['mapInstance.*'])
onMapChange(m: IMonitor) {
}
```

@Monitor会在以下情况回调：

- `mapInstance`被赋新值。
- 调用Map的API，例如`set`、`delete`、`clear`时触发。与Array、Date不同的是，只有当变化真的发生时，回调才会触发。这意味着，当对空Map调用`clear`，对不存在的Map键值调用`delete`，以及不实际改变值的`set`调用都不会触发@Monitor回调。

与Array不同，@Monitor无法对Map的某一个key做监听。

使用通配符监听Map对象的示例如下。

``` TypeScript
'use static'

import { Entry, Text, Column, ComponentV2, Button, BorderStyle, Color,
  ObservedV2, Trace, Local, Monitor, IMonitor } from '@kit.ArkUI';
import hilog from '@ohos.hilog';

@Entry
@ComponentV2
struct MonitorWildcardMap {
  @Local map: Map<string, string> = new Map<string, string>();
  cnt: int = 0;

  @Monitor(['map.size'])
  onMapSizeChanged(m: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s', `onMapSizeChanged, size dirty: ${m.dirty.toString()}`);
  }

  // 使能通配符
  @Monitor(['map.*'])
  onMapChanged(m: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s', `onMapChanged, dirty: ${m.dirty.toString()}`);
  }

  build() {
    Column() {
      Text(`map.size: ${this.map.size}`)
      Text(`map.get('one'): ${this.map.get('one')}`)
      // 在首次点击时，onMapSizeChanged、onMapChanged回调都触发
      Button(`Init, map.set('one', 'A'), map.set('two', 'B')`)
        .onClick(() => {
          this.map.set('one', 'A');
          this.map.set('two', 'B');
        })
      // onMapSizeChanged、onMapChanged回调都触发
      Button(`Add new, map.set('three' + this.cnt, 'C')`)
        .onClick(() => {
          this.cnt++;
          this.map.set('three' + this.cnt, 'C');
        })
      // 当'one'不存在时，onMapSizeChanged、onMapChanged回调都不触发
      // 当'one'存在时，onMapSizeChanged、onMapChanged回调都触发
      Button(`Delete from map: map.delete('one')`)
        .onClick(() => {
          this.map.delete('one');
        })
      // 当map不为空时，onMapSizeChanged、onMapChanged回调都触发
      // 当map为空时，onMapSizeChanged、onMapChanged回调都不触发
      Button(`Clear map`)
        .onClick(() => {
          this.map.clear();
        })
      // 在首次点击且假设存在（'one' -> 'A'）时，仅onMapChanged回调触发
      // 若已经设置过（'one' -> 'TWO'），则onMapSizeChanged、onMapChanged回调都不触发
      Button(`Update one to 'TWO' - map.set('one', 'TWO')`)
        .onClick(() => {
          this.map.set('one', 'TWO');
        })
      // 当Map不存在'one'时，onMapSizeChanged、onMapChanged回调都触发
      // 当Map存在'one'时，onMapSizeChanged、onMapChanged回调都不会触发
      Button(`Update one to the same - map.set('one', sameval)`)
        .onClick(() => {
          const sameval = this.map.get('one') ?? 'one';
          this.map.set('one', sameval);
        })
      // 当Map不存在'one'时，onMapSizeChanged、onMapChanged回调都触发
      // 当Map存在'one'时，仅onMapChanged回调触发
      Button(`Update one to new value - map.set('one', newval)`)
        .onClick(() => {
          let newval = 'x' + (++this.cnt);
          this.map.set('one', newval);
        })
      // 当map为空时，仅onMapChanged回调触发
      // 当map不为空时，onMapChanged、onMapSizeChanged回调都触发
      Button(`new map`)
        .onClick(() => {
          this.map = new Map<string, string>();
        })
    }
    .border({ style: BorderStyle.Solid, width: 2, color: Color.Green })
  }
}
```

### 使用通配符监听Set对象的变化

使用通配符可以监听Set对象的API调用。

```ts
@Monitor(['setInstance.*'])
onSetChange(m: IMonitor) {
}
```

@Monitor会在以下情况回调：

- `setInstance`被赋新值。
- 调用Set的API，例如`add`、`delete`、`clear`时触发。与Array、Date不同的是，只有当变化真的发生时，回调才会触发。这意味着，当对空Set调用`clear`，对不存在的Set元素调用`delete`，以及不实际新增元素的`add`调用都不会触发@Monitor回调。

与Array不同，@Monitor无法对Set的某一个key做监听。

使用通配符监听Set对象的示例如下。

``` TypeScript
'use static'

import { Entry, Text, Column, ComponentV2, Button,
  ObservedV2, Trace, Local, Monitor, IMonitor } from '@kit.ArkUI';
import hilog from '@ohos.hilog';

@Entry
@ComponentV2
struct MonitorWildcardSet {
  @Local set: Set<string> = new Set<string>();
  cnt: int = 0;

  // 使能通配符
  @Monitor(['set.*'])
  onSetChanged(m: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s', `onSetChanged, dirty: ${m.dirty.toString()}`);
  }

  @Monitor(['set.size'])
  onSetSizeChanged(m: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s', `onSetSizeChanged, size dirty: ${m.dirty.toString()}`);
  }

  aboutToAppear(): void {
    this.set.add('one');
    this.set.add('two');
  }

  build() {
    Column() {
      // onSetChanged、onSetSizeChanged回调都触发
      Button(`Add three<Num> to the set`)
        .onClick(() => {
          this.cnt++;
          this.set.add('three' + this.cnt);
        })
      // 当元素不存在时，onSetChanged、onSetSizeChanged回调都不触发
      // 当元素存在时，onSetChanged、onSetSizeChanged回调都触发
      Button(`Delete 'three<Num>' from the set - set.delete(...)`)
        .onClick(() => {
          this.set.delete('three' + this.cnt);
        })
      // 当set不为空时，onSetChanged、onSetSizeChanged回调都触发
      // 当set为空时，onSetChanged、onSetSizeChanged回调都不触发
      Button(`Clear the set - set.clear()`)
        .onClick(() => {
          this.set.clear();
        })
      // 当set不为空时，onSetChanged、onSetSizeChanged回调都触发
      // 当set为空时，仅onSetChanged回调触发
      Button(`Assign new set`)
        .onClick(() => {
          this.set = new Set<string>();
        })
      // 当set不包含'one'时，onSetChanged、onSetSizeChanged回调都触发
      // 当set包含'one'时，onSetChanged、onSetSizeChanged回调都不触发
      Button(`Add 'one' to the set`)
        .onClick(() => {
          this.set.add('one');
        })
    }
  }
}
```

## 限制条件

- \@Monitor的参数需要为监听属性名的字符串，enum枚举值和const常量，仅可以使用字符串字面量作为参数。不支持使用变量作为参数。 

   ```ts
   'use static'
   
   import { IMonitor, Monitor, ObservedV2, Trace } from '@kit.ArkUI';
   enum ENUM {
     T2 = 't2' // enum枚举值
   };
   const t3: string = 't3'; // const常量
   let t4: string = 't4'; // 变量
   @ObservedV2
   export class Info {
     @Trace t1: number = 0;
     @Trace t2: number = 0;
     @Trace t3: number = 0;
     @Trace t4: number = 0;
     @Trace t5: number = 0;
     @Monitor(['t1']) // 字符串字面量, 成功编译
     onT1Change(monitor: IMonitor): void {
       console.info(`t1 change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
     }
     @Monitor([ENUM.T2]) // enum枚举值，成功编译
     onT2Change(monitor: IMonitor): void {
       console.info(`t2 change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
     }
     @Monitor([t3]) // const常量，成功编译
     onT3Change(monitor: IMonitor): void {
       console.info(`t3 change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
     }
     @Monitor([t4]) // 错误用法，编译报错
     onT4Change(monitor: IMonitor): void {
       console.info(`t4 change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
     }
   }
   ```

- 建议开发者避免在\@Monitor中再次更改被监听的属性，这会导致无限循环。

   ```ts
   @ObservedV2
   export class Info {
     @Trace count: number = 0;
     @Monitor(['count'])
     onCountChange(monitor: IMonitor): void {
       this.count++; // 应避免这种写法，会导致无限循环
     }
   }
   ```
- 在被\@ObservedV2装饰的类中使用\@Monitor装饰器时，\@Monitor监听的变量必须带有\@Trace装饰器，否则会触发告警。

  ```ts
  'use static';
  import { IMonitor, Monitor, ObservedV2, Trace } from '@kit.ArkUI';

  @ObservedV2
  export class Info {
    @Trace name: string = 'Tom';
    @Trace region: string = 'North';
    @Trace job: string = 'Teacher';
    age: number = 25;
    // job属性被@Trace装饰，编译成功
    @Monitor(['job'])
    onJobChange(monitor: IMonitor): void {
      console.info(`change from ${monitor.value<string>()?.before} to ${monitor.value<string>()?.now}`);
    }
    // age属性未被@Trace装饰，编译成功，但会显示Plugin warning的告警
    @Monitor(['age'])
    onAgeChange(monitor: IMonitor): void {
      console.info(`change from ${monitor.value<number>()?.before} to ${monitor.value<number>()?.now}`);
    }
  }
  ```

- 在被\@ComponentV2装饰的自定义组件中使用\@Monitor装饰器时，\@Monitor监听的变量必须被\@Local、\@Param、\@Provider、\@Consumer或\@Computed装饰器修饰，否则会触发告警。

  ```ts
  'use static'
  
  import { Column, ComponentV2, Entry, IMonitor, Local, Monitor, ObservedV2, Param, Trace } from '@kit.ArkUI';
  
  @ObservedV2
  export class UserV2 {
    @Trace name: string = 'Tom';
    age: number = 1;
  }
  
  @Entry
  @ComponentV2
  struct Index {
    @Local message: string = 'Hello World';
    @Param name: string = 'Tom';
    @Local user: UserV2 = new UserV2();
    age: number = 24;
  
    // 编译成功
    @Monitor(['user'])
    onUserChange(monitor: IMonitor) {
      console.info(`change from ${monitor.value<UserV2>()?.before} to ${monitor.value<UserV2>()?.now}`);
    }
    // 编译成功，但会显示Plugin warning的告警
    @Monitor(['age']) 
    onAgeChange(monitor: IMonitor) {
      console.info(`change from ${monitor.value<number>()?.before} to ${monitor.value<number>()?.now}`);
    }
    
    build() {
      Column() {
      }
    }
  }
  ```
  
- 在被\@ObservedV2装饰的类中，或在被\@ComponentV2装饰的自定义组件中使用\@Monitor装饰器时，\@Monitor监听的变量必须是已存在的变量，否则会导致编译报错。

  ```ts
  'use static'
  
  import { Column, ComponentV2, Entry, IMonitor, Local, Monitor, ObservedV2, Trace } from '@kit.ArkUI';
  
  @ObservedV2 
  export class UserV2 {
    @Trace name: string = 'Tom';
    age: number = 1;
  }
  
  @ObservedV2
  export class Info {
    @Trace age: number = 25;
    @Trace user: UserV2 = new UserV2();
  
    // age1不存在，会导致编译报错
    @Monitor(['age1'])
    onAgeChange(monitor: IMonitor): void {
      console.info(`change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
    }
  
    // user.age1不存在，会导致编译报错
    @Monitor(['user.age1'])
    onUserAgeChange(monitor: IMonitor): void {
      console.info(`change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
    }
  }
  
  @Entry
  @ComponentV2
  struct Index {
    @Local message: string = 'Hello world';
    @Local user: UserV2 = new UserV2();
  
    // user1不存在，会导致编译报错
    @Monitor(['user1'])  
    onUserChange(monitor: IMonitor): void {
      console.info(`change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
    } 
  
    // user.age1不存在，会导致编译报错
    @Monitor(['user.age1'])  
    onUserAgeChange(monitor: IMonitor): void {
      console.info(`change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
    }
  
    build() {
      Column() {
      }
    }
  }
  ```

## \@Monitor与\@Watch对比

\@Monitor与\@Watch的用法、功能对比如下：

| 比较项             | \@Watch                                 | \@Monitor                                                    |
| ------------------ | --------------------------------------- | ------------------------------------------------------------ |
| 参数               | 回调方法名。                              | 监听状态变量名、属性名。                                       |
| 监听目标数         | 只能监听单个状态变量。                    | 能同时监听多个状态变量。                                       |
| 监听能力           | 跟随状态变量观察能力（一层）。           | 跟随状态变量观察能力（深层）。                                 |
| 能否获取变化前的值 | 不能获取变化前的值。                      | 能获取变化前的值。                                             |
| 监听条件           | 监听对象为状态变量。                      | 监听对象为状态变量或为\@Trace装饰的类成员属性。                |
| 使用场景           | 仅能在[\@Component](./arkts-static-create-component.md#component)装饰的自定义组件中使用。 | 能在[\@ComponentV2](./arkts-static-componentv2.md)装饰的自定义组件中使用，也能在\@ObservedV2装饰的类中使用。 |

## 使用场景

### 监听深层属性变化

\@Monitor可以监听深层属性的变化，并能够根据更改前后的值做分类处理。

下面的示例中监听了属性value的变化，并根据变化的幅度改变Text组件显示的样式。

```ts
'use static'

import { Button, Color, Column, ComponentV2, Entry, IMonitor, Monitor, ObservedV2, Text, Trace } from '@kit.ArkUI';

@ObservedV2
export class Info {
  @Trace value: number = 50;
}
@ObservedV2
export class UIStyle {
  info: Info = new Info();
  @Trace color: Color = Color.Black;
  @Trace fontSize: number = 45;
  @Monitor(['info.value'])
  onValueChange(monitor: IMonitor): void {
    let lastValue: number = monitor.value<number>()?.before as number;
    let curValue: number = monitor.value<number>()?.now as number;
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
        .onClick((e) => {
          this.textStyle.info.value = Math.floor(Math.random() * 100) + 1;
        })
    }
  }
}
```
