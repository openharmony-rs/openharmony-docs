# \@Monitor装饰器：状态变量修改监听

为了增强状态管理框架对状态变量变化的监听能力，开发者可以使用\@Monitor装饰器对状态变量进行监听。

>**说明：**
>
>\@Monitor装饰器从API version 23开始支持。

## 概述

\@Monitor装饰器用于监听状态变量修改，使得状态变量具有深度监听的能力：

- \@Monitor装饰器支持在\@ComponentV2装饰的自定义组件中使用，未被状态变量装饰器[\@Local](./arkts-static-new-local.md)、[\@Param](./arkts-static-new-param.md)、[\@Provider、\@Consumer](./arkts-static-new-provider-and-consumer.md)、[\@Computed](./arkts-static-new-computed.md)装饰的变量无法被\@Monitor监听到变化。

- \@Monitor装饰器支持在类中与[\@ObservedV2、\@Trace](./arkts-static-new-observedV2-and-trace.md)配合使用，不允许在未被\@ObservedV2装饰的类中使用\@Monitor装饰器。未被\@Trace装饰的属性无法被\@Monitor监听到变化。
- 当观测的属性变化时，\@Monitor装饰器定义的回调方法将被调用。判断属性是否变化使用的是严格相等（===），当严格相等判断的结果是false（即不相等）的情况下，就会触发\@Monitor的回调。当在一次事件中多次改变同一个属性时，将会使用初始值和最终值进行比较以判断是否变化。
- 单个\@Monitor装饰器能够同时监听多个属性的变化，当这些属性在一次事件中共同变化时，只会触发一次\@Monitor的回调方法。
- \@Monitor装饰器具有深度监听的能力，能够监听嵌套类、多维数组、对象数组中指定项的变化。对于嵌套类、对象数组中成员属性变化的监听要求该类被\@ObservedV2装饰且该属性被\@Trace装饰。
- 在继承类场景中，可以在父子组件中对同一个属性分别定义\@Monitor进行监听，当属性变化时，父子组件中定义的\@Monitor回调均会被调用。
- 和\@Watch装饰器类似，开发者需要自己定义回调函数，区别在于\@Watch装饰器将函数名作为参数，而\@Monitor直接装饰回调函数。\@Monitor与[\@Watch](./arkts-static-watch.md)的对比可以查看[\@Monitor与\@Watch的对比](#monitor与watch对比)。

在静态上下文中使用时，需导入装饰器：

```ts
import { Monitor } from '@ohos.arkui.stateManagement';
```

## 装饰器说明

| \@Monitor属性装饰器 | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| 装饰器参数          | 字符串类型的对象属性名列表。可同时监听多个对象属性，例如@Monitor(['prop1', 'prop2'])。可监听深层的属性变化，如多维数组中的某一个元素，嵌套对象或对象数组中的某一个属性。详见[监听变化](#监听变化)。 |
| 装饰对象            | \@Monitor装饰成员方法。当监听的属性发生变化时，会触发该回调方法。该回调方法以[IMonitor类型](#imonitor类型)的变量作为参数，开发者可以从该参数中获取变化前后的相关信息。 |

## 接口说明

IMonitor类型和IMonitorValue\<T\>类型的接口说明参考API文档：[@Monitor](../../reference/apis-arkui/arkui-ts/ts-state-management-monitor-static.md)

## 监听变化

### 在\@ComponentV2装饰的自定义组件中使用\@Monitor

使用\@Monitor监听的状态变量发生变化时，会触发\@Monitor的回调方法。

- \@Monitor监听的变量需要被\@Local、\@Param、\@Provider、\@Consumer、\@Computed装饰，未被状态变量装饰器装饰的变量在变化时无法被监听。\@Monitor可以同时监听多个状态变量，这些变量名之间用","隔开。

   ```ts
   'use static'
   
   import { Button, Column, ComponentV2, Entry } from '@ohos.arkui.component';
   import { Local, IMonitor, Monitor } from '@ohos.arkui.stateManagement';
   @Entry
   @ComponentV2
   struct Index {
     @Local message: string = 'Hello World';
     @Local name: string = 'Tom';
     @Local age: number = 24;
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
   
   import { Button, Column, ComponentV2, Entry, Text } from '@ohos.arkui.component';
   import { Local, IMonitor, Monitor } from '@ohos.arkui.stateManagement';
   
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
   
   import { Button, Column, ComponentV2, Entry, Text } from '@ohos.arkui.component';
   import { Local, IMonitor, Monitor, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
   
   @ObservedV2
   class Info {
     @Trace name: string = 'Tom';
     @Trace region: string = 'North';
     @Trace job: string = 'Teacher';
     age: number = 25;
     // name被@Trace装饰，能够监听变化
     @Monitor(['name'])
     onNameChange(monitor: IMonitor) {
       console.info(`name change from ${monitor.value<string>()?.before} to ${monitor.value<string>()?.now}`);
     }
     // age未被@Trace装饰，不能监听变化
     @Monitor(['age'])
     onAgeChange(monitor: IMonitor) {
       console.info(`age change from ${monitor.value<number>()?.before} to ${monitor.value<number>()?.now}`);
     }
     // region与job均被@Trace装饰，能够监听变化
     @Monitor(['region', 'job'])
     onChange(monitor: IMonitor) {
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
   
   import { Button, Column, ComponentV2, Entry, Text } from '@ohos.arkui.component';
   import { Local, IMonitor, Monitor, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
   
   @ObservedV2
   class Inner {
     @Trace num: number = 0;
   }
   @ObservedV2
   class Outer {
     inner: Inner = new Inner();
     @Monitor(['inner.num'])
     onChange(monitor: IMonitor) {
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
   
   import { Button, Column, ComponentV2, Entry } from '@ohos.arkui.component';
   import { IMonitor, Monitor, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
   
   @ObservedV2
   class Base {
     @Trace name: string;
     // 基类监听name属性
     @Monitor(['name'])
     onBaseNameChange(monitor: IMonitor) {
       console.info('Base Class name change');
     }
     constructor(name: string) {
       this.name = name;
     }
   }
   @ObservedV2
   class Derived extends Base {
     // 继承类监听name属性
     @Monitor(['name'])
     onDerivedNameChange(monitor: IMonitor) {
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
   
   import { Button, Column, ComponentV2, Entry } from '@ohos.arkui.component';
   import { IMonitor, Monitor, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
   
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
     // dimensionTwo为二维简单类型数组，且被@Trace装饰，能够观测里面的元素变化
     @Monitor(['dimensionTwo.0.0', 'dimensionTwo.1.1'])
     onDimensionTwoChange(monitor: IMonitor) {
       monitor.dirty.forEach((path: string) => {
         console.info(`dimensionTwo path: ${path} change from ${monitor.value<number>(path)?.before} to ${monitor.value<number>(path)?.now}`);
       })
     }
     // dimensionThree为三维简单类型数组，且被@Trace装饰，能够观测里面的元素变化
     @Monitor(['dimensionThree.0.0.0', 'dimensionThree.1.1.0'])
     onDimensionThreeChange(monitor: IMonitor) {
       monitor.dirty.forEach((path: string) => {
         console.info(`dimensionThree path: ${path} change from ${monitor.value<number>(path)?.before} to ${monitor.value<number>(path)?.now}`);
       })
     }
     // Info类中属性name、age均被@Trace装饰，能够监听到变化
     @Monitor(['infoArr.0.name', 'infoArr.1.age'])
     onInfoArrPropertyChange(monitor: IMonitor) {
       monitor.dirty.forEach((path: string) => {
         console.info(`infoArr path:${path} change from ${monitor.value<Any>(path)?.before} to ${monitor.value<Any>(path)?.now}`);
       })
     }
     // infoArr被@Trace装饰，能够监听到infoArr整体赋值的变化
     @Monitor(['infoArr'])
     onInfoArrChange(monitor: IMonitor) {
       console.info('infoArr whole change');
     }
     // 能够监听到infoArr的长度变化
     @Monitor(['infoArr.length'])
     onInfoArrLengthChange(monitor: IMonitor) {
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
   
   import { Button, Column, ComponentV2, Entry } from '@ohos.arkui.component';
   import { IMonitor, Monitor, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
   
   @ObservedV2
   class Info {
     @Trace person: Person;
     @Monitor(['person.name'])
     onNameChange(monitor: IMonitor) {
       console.info(`name change from ${monitor.value<string>()?.before} to ${monitor.value<string>()?.now}`);
     }
     @Monitor(['person.age'])
     onAgeChange(monitor: IMonitor) {
       console.info(`age change from ${monitor.value<number>()?.before} to ${monitor.value<number>()?.now}`);
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
   
   import { Button, Column, ComponentV2, Entry } from '@ohos.arkui.component';
   import { IMonitor, Monitor, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
   
   @ObservedV2
   class Frequence {
     @Trace count: number = 0;
     @Monitor(['count'])
     onCountChange(monitor: IMonitor) {
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

## 限制条件

- \@Monitor的参数需要为监听属性名的字符串，enum枚举值和const常量，仅可以使用字符串字面量作为参数。不支持使用变量作为参数。 

   ```ts
   'use static'
   
   import { IMonitor, Monitor, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
   enum ENUM {
     T2 = 't2' // enum枚举值
   };
   const t3: string = 't3'; // const常量
   let t4: string = 't4'; // 变量
   @ObservedV2
   class Info {
     @Trace t1: number = 0;
     @Trace t2: number = 0;
     @Trace t3: number = 0;
     @Trace t4: number = 0;
     @Trace t5: number = 0;
     @Monitor(['t1']) // 字符串字面量, 成功编译
     onT1Change(monitor: IMonitor) {
       console.info(`t1 change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
     }
     @Monitor([ENUM.T2]) // enum枚举值，成功编译
     onT2Change(monitor: IMonitor) {
       console.info(`t2 change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
     }
     @Monitor([t3]) // const常量，成功编译
     onT3Change(monitor: IMonitor) {
       console.info(`t3 change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
     }
     @Monitor([t4]) // 错误用法，编译报错
     onT4Change(monitor: IMonitor) {
       console.info(`t4 change from ${monitor.value<Any>()?.before} to ${monitor.value<Any>()?.now}`);
     }
   }
   ```

- 建议开发者避免在\@Monitor中再次更改被监听的属性，这会导致无限循环。

   ```ts
   @ObservedV2
   class Info {
     @Trace count: number = 0;
     @Monitor(['count'])
     onCountChange(monitor: IMonitor) {
       this.count++; // 应避免这种写法，会导致无限循环
     }
   }
   ```
- 在被\@ObservedV2装饰的类中使用\@Monitor装饰器时，\@Monitor监听的变量必须带有\@Trace装饰器，否则会触发告警。

  ```ts
  'use static';
  import { IMonitor, Monitor, ObservedV2, Trace } from '@kit.ArkUI';

  @ObservedV2
  class Info {
    @Trace name: string = 'Tom';
    @Trace region: string = 'North';
    @Trace job: string = 'Teacher';
    age: number = 25;
    // job属性被@Trace装饰，编译成功
    @Monitor(['job'])
    onJobChange(monitor: IMonitor) {
      console.info(`change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
    // age属性未被@Trace装饰，编译成功，但会显示Plugin warning的告警
    @Monitor(['age'])
    onAgeChange(monitor: IMonitor) {
      console.info(`change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
  }
  ```

- 在被\@ComponentV2装饰的自定义组件中使用\@Monitor装饰器时，\@Monitor监听的变量必须被\@Local、\@Param、\@Provider、\@Consumer或\@Computed装饰器修饰，否则会触发告警。

  ```ts
  'use static'

  import { Column, ComponentV2, Entry, Local, Param, IMonitor, Monitor, ObservedV2, Trace } from '@kit.ArkUI';

  @ObservedV2
  class UserV2 {
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
      console.info(`change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
    // 编译成功，但会显示Plugin warning的告警
    @Monitor(['age']) 
    onAgeChange(monitor: IMonitor) {
      console.info(`change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
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

  import { Column, ComponentV2, Entry, Local, IMonitor, Monitor, ObservedV2, Trace } from '@kit.ArkUI';

  @ObservedV2 
  class UserV2 {
    @Trace name: string = 'Tom';
    age: number = 1;
  }

  @ObservedV2
  class Info {
    @Trace age: number = 25;
    @Trace user: UserV2 = new UserV2();

    // age1不存在，会导致编译报错
    @Monitor(['age1'])
    onAgeChange(monitor: IMonitor) {
      console.info(`change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    }
    
    // user.age1不存在，会导致编译报错
    @Monitor(['user.age1'])
    onUserAgeChange(monitor: IMonitor) {
      console.info(`change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
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
      console.info(`change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
    } 

    // user.age1不存在，会导致编译报错
    @Monitor(['user.age1'])  
    onUserAgeChange(monitor: IMonitor): void {
      console.info(`change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
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
| 使用场景           | 仅能在\@Component装饰的自定义组件中使用。 | 能在\@ComponentV2装饰的自定义组件中使用，也能在\@ObservedV2装饰的类中使用。 |

## 使用场景

### 监听深层属性变化

\@Monitor可以监听深层属性的变化，并能够根据更改前后的值做分类处理。

下面的示例中监听了属性value的变化，并根据变化的幅度改变Text组件显示的样式。

```ts
'use static'

import { Button, Color, Column, ComponentV2, Entry, Text } from '@ohos.arkui.component';
import { IMonitor, Monitor, ObservedV2, Trace } from '@ohos.arkui.stateManagement';

@ObservedV2
class Info {
  @Trace value: number = 50;
}
@ObservedV2
class UIStyle {
  info: Info = new Info();
  @Trace color: Color = Color.Black;
  @Trace fontSize: number = 45;
  @Monitor(['info.value'])
  onValueChange(monitor: IMonitor) {
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
