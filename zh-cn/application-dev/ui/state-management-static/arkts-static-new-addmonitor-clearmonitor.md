# addMonitor/clearMonitor接口：动态添加/取消监听

从API version 23开始，开发者可以使用addMonitor与clearMonitor方法，在应用程序运行过程中动态地为状态变量添加或删除监听函数。

在阅读本文档前，建议提前阅读：[@ObservedV2/@Trace](./arkts-static-new-observedV2-and-trace.md)、[@ComponentV2](./arkts-static-componentv2.md)、[@Local](./arkts-static-new-local.md)，[@Monitor](./arkts-static-new-monitor.md)。

## 概述

装饰器@Monitor如果声明在@ObservedV2和@ComponentV2中，会使得开发者构造出的所有的@ObservedV2和@ComponentV2的实例，都默认有同样的@Monitor的监听回调，且无法取消或删除对应的监听回调。

如果开发者希望动态地为@ObservedV2和@ComponentV2的实例添加或删除监听函数，则可以使用addMonitor和clearMonitor接口。

* 使用addMonitor/clearMonitor接口需要导入`UIUtils`。
  ```typescript
  import { UIUtils } from '@kit.ArkUI';
  ```
* clearMonitor仅可以删除addMonitor添加的监听函数，无法删除@Monitor的监听函数。

## 使用方法

* addMonitor可以在一次调用中为一个状态变量或多个状态变量（以数组形式）添加回调函数。

```typescript
'use static'

import { UIUtils, Local, Trace, ObservedV2, IMonitor, IMonitorDecoratedVariable } from '@ohos.arkui.stateManagement';
import { ComponentV2, Entry, Column, Button } from '@ohos.arkui.component';

@ObservedV2
class Test {
  @Trace value: string = '';
  @Trace arrayValue: Array<int> = [1, 2, 3, 4, 5];
  valueMonitor?: IMonitorDecoratedVariable;
  arrayMonitor?: IMonitorDecoratedVariable;

  constructor() {
    // 监听单个状态变量
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange);

    // 监听多个状态变量
    let callbackArray: Array<() => Any> = [];
    for (let index = 0; index < 5; index++) {
      callbackArray.push(() => this.arrayValue[index]);
    }
    this.arrayMonitor = UIUtils.addMonitor(callbackArray, this.onArrayChange);
  }

  onChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<string>(path)?.before} to ${m.value<string>(path)?.now}`);
    });
  }

  onArrayChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] array ${path} value has changed from ${m.value<int>(path)?.before} to ${m.value<int>(path)?.now}`);
    });
  }
}

@Entry
@ComponentV2
struct Page {
  @Local obj: Test = new Test();

  aboutToAppear(): void {
    console.info(`[DynamicMonitor] Test case begin.`);
  }

  build() {
    Column() {
      Button(`Current number: ${this.obj.value}`)
        .fontSize(20)
        .onClick(() => {
          // 修改已注册的监听值
          this.obj.value += 'a';
          for (let index = 0; index < 5; index++) {
            this.obj.arrayValue[index]++;
          }
        })
    }
  }
}
```

* addMonitor支持重复监听：即使状态变量和回调函数相同，每次调用都会返回一个唯一的句柄，代表独立的监听关系。

```typescript
'use static'

import { UIUtils, Local, Trace, ObservedV2, IMonitor, IMonitorDecoratedVariable } from '@ohos.arkui.stateManagement';
import { ComponentV2, Entry, Column, Button } from '@ohos.arkui.component';

@ObservedV2
class Test {
  @Trace value: int = 0;
  valueMonitor?: IMonitorDecoratedVariable;
  valueMonitorDuplicated?: IMonitorDecoratedVariable;

  constructor() {
    // 可以重复为同一对状态变量和回调函数多次添加监听关系
    // 但返回不同的唯一性句柄
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange);
    this.valueMonitorDuplicated = UIUtils.addMonitor(() => this.value, this.onChange);
  }

  onChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<int>(path)?.before} to ${m.value<int>(path)?.now}`);
    })
  }
}

@Entry
@ComponentV2
struct Page {
  @Local obj: Test = new Test();

  aboutToAppear(): void {
    console.info(`[DynamicMonitor] Test case begin.`);
  }

  build() {
    Column() {
      Button(`Current number: ${this.obj.value}`)
        .fontSize(20)
        .onClick(() => {
          this.obj.value++;
        })
      // 清除重复监听之后，修改状态变量只会触发一次回调函数
      // 即不影响先前绑定的监听关系
      Button(`Clear the duplicated monitor.`)
        .fontSize(20)
        .onClick(() => {
          UIUtils.clearMonitor(this.obj.valueMonitorDuplicated!);
        })
    }
  }
}
```

* addMonitor可以添加同步模式不同但状态变量与回调函数相同的监听关系，同步模式会在状态变量修改时立即触发回调函数，而异步模式的回调函数调用会推迟到下一次UI更新时调用。

```typescript
'use static'

import { UIUtils, Local, Trace, ObservedV2, IMonitor, IMonitorDecoratedVariable } from '@ohos.arkui.stateManagement';
import { ComponentV2, Entry, Column, Button } from '@ohos.arkui.component';

@ObservedV2
class Test {
  @Trace value: string = '';
  @Trace value2: string = '';
  valueMonitor?: IMonitorDecoratedVariable;
  value2Monitor?: IMonitorDecoratedVariable;

  constructor() {
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange);
    this.value2Monitor = UIUtils.addMonitor(() => this.value2, this.onChange, { isSynchronous: true });
  }

  onChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value has changed from ${m.value<string>(path)?.before} to ${m.value<string>(path)?.now}`);
    });
  }

  onSyncChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value has changed synchronously from ${m.value<string>(path)?.before} to ${m.value<string>(path)?.now}`);
    });
  }
}

@Entry
@ComponentV2
struct Page {
  @Local obj: Test = new Test();

  aboutToAppear(): void {
    console.info(`[DynamicMonitor] Test case begin.`);
  }

  build() {
    Column() {
      Button(`Current number: ${this.obj.value} | ${this.obj.value2}`)
        .fontSize(20)
        .onClick(() => {
          // 虽然value的修改先于value2的修改
          // 但value2绑定的监听关系是同步模式
          // 因此回调函数调用value2会先于value
          this.obj.value += 'a';
          this.obj.value2 += 'b';
        })
    }
  }
}
```

* 如果监听的是组件的状态变量，那么建议将组件作为`owner`传递给`addMonitor`。

```typescript
'use static'

import { UIUtils, Local, IMonitorDecoratedVariable, IMonitor } from '@ohos.arkui.stateManagement';
import { Entry, ComponentV2, Column, Button, Text } from '@ohos.arkui.component';

@Entry
@ComponentV2
struct Page {
  @Local value: int = 0;
  valueMonitor?: IMonitorDecoratedVariable;

  onChange(monitor: IMonitor) {
    console.info('[DynamicMonitor] Callback triggered.');

    monitor.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] Value ${path} has changed from ${monitor.value<int>(path)?.before} to ${monitor.value<int>(path)?.now}.`);
    });
  }

  aboutToAppear() {
    console.info('[DynamicMonitor] Test case begin.')

    // 对于监听组件的状态变量
    // 建议将组件作为owner传递给addMonitor
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange, { owner: this });
  }

  build() {
    Column() {
      Text(`Current value is ${this.value}`)
      Button('Increase the value')
        .onClick(() => {
          this.value++;
        })
    }
  }
}
```

* 开发者向`addMonitor`传递`MonitorOptions.path`时，函数内部会优先使用开发者传递的`path`，若传入路径数少于状态变量数则自动生成，若传入路径多于状态变量数，则多余部分忽略不计。

```typescript
'use static'

import { UIUtils, IMonitor, IMonitorDecoratedVariable, Local } from '@ohos.arkui.stateManagement';
import { Entry, ComponentV2, Row, Column, Text, Button } from '@ohos.arkui.component';

interface Pair<R, V> {
  key: R;
  value: V;
};

@Entry
@ComponentV2
struct Page {
  @Local singleValue: int = 0;
  @Local pairValue: Pair<int, int> = { key: 42, value: 35 };
  @Local multipleValue: int[] = [1, 2, 3];

  singleValueMonitor?: IMonitorDecoratedVariable;
  pairValueMonitor?: IMonitorDecoratedVariable;
  multipleValueMonitor?: IMonitorDecoratedVariable;

  aboutToAppear() {
    console.info('[DynamicMonitor] Test case begin.');

    // 传递path个数少于状态变量个数
    // 使用默认生成的字符串'MONITOR_n'作为路径
    // n是addMonitor注册的状态变量的序号
    // 因此生成的字符串在函数内部保证是全局唯一的
    this.singleValueMonitor = UIUtils.addMonitor(() => this.singleValue, this.onChange, { owner: this });

    // 传递 path 等于状态变量个数
    // 每一个 path 均应用于状态变量的路径
    const pairCallback: (() => Any)[] = [
      () => this.pairValue.key,
      () => this.pairValue.value
    ];
    this.pairValueMonitor = UIUtils.addMonitor(pairCallback, this.onChange, { owner: this, path: ['pair_key', 'pair_value'] });

    // 传递path多于状态变量个数
    // 多余的path忽略不计，也不会抛出错误
    const valueCallback = this.multipleValue.map((_: int, index: number): (() => Any) => (
      () => this.multipleValue[Double.toInt(index)]
    ));
    this.multipleValueMonitor = UIUtils.addMonitor(valueCallback, this.onChange, { owner: this, path: ['First', 'Second', 'Third', 'Fourth'] });
  }

  onChange(mon: IMonitor) {
    console.info('[DynamicMonitor] Callback triggered.');

    mon.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${mon.value<int>(path)?.before} to ${mon.value<int>(path)?.now}.`);
    })
  }

  build() {
    Column() {
      Text(`Single value: ${this.singleValue}`)
      Button('Increase the single value')
        .onClick(() => {
          this.singleValue++;
        })
      Text(`Pair value: [${this.pairValue.key}, ${this.pairValue.value}]`)
      Button('Increase the pair value')
        .onClick(() => {
          this.pairValue.key++;
          this.pairValue.value++;
        })
      Text(`Multiple value: ${this.multipleValue}`)
      Button('Increase the multiple value')
        .onClick(() => {
          for (let index = 0; index < this.multipleValue.length; index++) {
            this.multipleValue[index]++;
          }
        })
    }
  }
}
```

## 限制条件

* 对于可选参数`MonitorOptions.owner`，若其被@Component而非@ComponentV2装饰，则在运行时抛出130000错误。

```typescript
'use static'

import { UIUtils, IMonitorDecoratedVariable, IMonitor, State } from '@ohos.arkui.stateManagement';
import { Component, ComponentV2, Column, Text, Button, Entry, BusinessError } from '@ohos.arkui.component';

@Component
struct Test {
  @State value: int = 0;
  valueMonitor?: IMonitorDecoratedVariable;

  aboutToAppear() {
    try {
      // 触发 130000 BusinessError
      this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange, { owner: this });
    } catch (err: BusinessError) {
      // 错误码需要捕获异常后输出
      console.error(`[DynamicMonitor] Error code: ${err.code}, message: ${err.message}`);
    }
  }

  onChange(mon: IMonitor) {
      mon.dirty.forEach((path: string) => {
        console.info(`[DynamicMonitor] value ${path} has changed from ${mon.value<int>(path)?.before} to ${mon.value<int>(path)?.now}.`);
      })
  }

  build() {
    Column() {
      Text(`Current value is ${this.value}`)
      Button('Increase the value')
        .onClick(() => {
          this.value++;
        })
    }
  }
}

@Entry
@ComponentV2
struct Page {
  build() {
    Column() {
      Test()
    }
  }
}
```

* addMonitor监听的变量类型与在回调函数中访问的类型必须匹配，否则会抛出异常，且无法通过`dirty`获取状态变量的新值与旧值，但仍能触发回调函数。

```typescript
'use static'

import { UIUtils, Local, Trace, ObservedV2, IMonitor, IMonitorDecoratedVariable } from '@ohos.arkui.stateManagement';
import { ComponentV2, Entry, Column, Button } from '@ohos.arkui.component';

@ObservedV2
class Test {
  @Trace value: int = 0;
  @Trace valueError: number = 0;
  valueMonitor?: IMonitorDecoratedVariable;
  valueMonitorDuplicated?: IMonitorDecoratedVariable;

  constructor() {
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange);

    // 在这个监听关系的回调函数中
    // number（编译后为Double）与Int类型不匹配
    // 因此无法通过dirty获取监听变量的新值和旧值
    this.valueMonitorDuplicated = UIUtils.addMonitor(() => this.valueError, this.onChange);
  }

  onChange(m: IMonitor) {
    // 日志正常打印
    console.info('[DynamicMonitor] Callback triggered.');

    // 类型不匹配抛出ClassCastError异常
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<int>(path)?.before} to ${m.value<int>(path)?.now}`);
    })
  }
}

@Entry
@ComponentV2
struct Page {
  @Local obj: Test = new Test();

  aboutToAppear(): void {
    console.info(`[DynamicMonitor] Test case begin.`)
  }

  build() {
    Column() {
      Button(`Current number: ${this.obj.value}`)
        .fontSize(20)
        .onClick(() => {
          this.obj.value++;
          this.obj.valueError++;
        })
    }
  }
}
```

* addMonitor添加对容器的监听时，修改容器内的元素不会触发回调函数，必须修改对象本身才会触发监听。对于数组内元素的监听请参考[对数组内的元素及其长度的监听](#对数组内的元素及其长度的监听)的使用场景。

```typescript
'use static'
import { UIUtils, Local, Trace, ObservedV2, IMonitor, IMonitorDecoratedVariable } from '@ohos.arkui.stateManagement';
import { ComponentV2, Entry, Column, Button, Text } from '@ohos.arkui.component';

@ObservedV2
class Test {
  @Trace array: Array<int> = [1, 2, 3, 4, 5];
  @Trace map: Map<number, string> = new Map<number, string>([[1, 'first'], [2, 'second']]);

  arrayMonitor?: IMonitorDecoratedVariable;
  mapMonitor?: IMonitorDecoratedVariable;

  constructor() {
    // 只监听容器替换，而不监听容器内元素变更
    // 即被监听的对象的子对象变更不会触发事件
    // 只有被监听的对象本身变化才能触发事件
    this.arrayMonitor = UIUtils.addMonitor(() => this.array, this.onChange);
    this.mapMonitor = UIUtils.addMonitor(() => this.map, this.onMapChange);
  }

  onChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<Array<int>>(path)?.before} to ${m.value<Array<int>>(path)?.now}`);
    })
  }

  onMapChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<Map<number, string>>(path)?.before} to ${m.value<Map<number, string>>(path)?.now}`);
    })
  }
}

@Entry
@ComponentV2
struct Page {
  @Local obj: Test = new Test();

  aboutToAppear(): void {
    console.info(`[DynamicMonitor] Test case begin.`);
  }

  build() {
    Column() {
      Text(`Current array: ${this.obj.array}`)
      Text(`Current map: ${this.obj.map}`)
      Button(`Modify container`)
        .fontSize(20)
        .onClick(() => {
          // 容器内的值发生变更不会使
          // 监听容器本身的回调函数触发
          for (let index = 0; index < 5; index++) {
            this.obj.array[index]++;
          }

          // 修改容器对象本身会触发回调函数
          this.obj.map = new Map<number, string>();
        })
    }
  }
}
```

* clearMonitor 无法删除 [@Monitor](./arkts-static-new-monitor.md) 注册的监听关系，且只会影响传入句柄所指代的监听关系，对于相同状态变量与回调函数的监听关系互不影响。

```typescript
'use static'

import { UIUtils, Local, Trace, ObservedV2, IMonitor, IMonitorDecoratedVariable, Monitor } from '@ohos.arkui.stateManagement';
import { ComponentV2, Entry, Column, Button } from '@ohos.arkui.component';

@ObservedV2
class Test {
  @Trace value: int = 0;
  valueMonitor?: IMonitorDecoratedVariable;
  valueMonitorDuplicated?: IMonitorDecoratedVariable;

  constructor() {
    // 可以重复为同一个状态变量和回调函数多次添加监听关系
    // 但返回不同的唯一性句柄
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange);
    this.valueMonitorDuplicated = UIUtils.addMonitor(() => this.value, this.onChange);
  }

  @Monitor(['value'])
  onChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<int>(path)?.before} to ${m.value<int>(path)?.now}`);
    })
  }
}

@Entry
@ComponentV2
struct Page {
  @Local obj: Test = new Test();

  aboutToAppear(): void {
    console.info(`[DynamicMonitor] Test case begin.`)
  }

  build() {
    Column() {
      Button(`Current number: ${this.obj.value}`)
        .fontSize(20)
        .onClick(() => {
          this.obj.value++;
        })
      // 清除重复监听之后，修改状态变量只会触发两次回调函数
      // 即不影响先前绑定的与@Monitor添加的监听关系
      Button(`Clear the duplicated monitor.`)
        .fontSize(20)
        .onClick(() => {
          UIUtils.clearMonitor(this.obj.valueMonitorDuplicated!);
        })
    }
  }
}
```

## 使用场景

### 监听@ObservedV2/@Trace与@ComponentV2/@Local搭配修饰的变量

若要使用addMonitor对状态变量进行监听，需要使用@Local/@Trace来修饰被监听的变量，且被监听的变量所在的struct/class需要有@ComponentV2/@ObservedV2修饰。

```typescript
'use static'
import { UIUtils, Local, Trace, ObservedV2, IMonitor, IMonitorDecoratedVariable } from '@ohos.arkui.stateManagement';
import { ComponentV2, Entry, Column, Button, Text } from '@ohos.arkui.component';

// class使用@ObservedV2修饰
@ObservedV2
class Test {
  // @ObserevdV2与@Trace搭配使用
  @Trace value: int = 0;
  valueMonitor?: IMonitorDecoratedVariable;

  constructor() {
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange);
  }

  onChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<int>(path)?.before} to ${m.value<int>(path)?.now}`);
    })
  }
}

// struct使用@ComponentV2修饰
@ComponentV2
struct Child {
  // @ComponentV2与@Local搭配使用
  @Local value: double = 0.0;
  valueMonitor?: IMonitorDecoratedVariable;

  aboutToAppear() {
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange);
  }

  onChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<double>(path)?.before} to ${m.value<double>(path)?.now}`);
    })
  }

  build() {
    Column() {
      Text(`Current ComponentV2 value is ${this.value}`)
      Button(`Add value in ComponentV2`)
        .onClick(() => {
          this.value += 0.1;
        })
    }
  }
}

@Entry
@ComponentV2
struct Page {
  @Local obj: Test = new Test();

  aboutToAppear(): void {
    console.info(`[DynamicMonitor] Test case begin.`)
  }

  build() {
    Column() {
      Text(`Current ObservedV2 value is ${this.obj.value}`)
      Button(`Add value in ObservedV2`)
        .fontSize(20)
        .onClick(() => {
          this.obj.value++;
        })
      Child()
    }
  }
}
```

### 对数组内的元素及其长度的监听

对数组内的元素和数组的长度监听与对普通状态变量的监听方法是一样的。

```typescript
'use static'

import { UIUtils, IMonitorDecoratedVariable, IMonitor, ObservedV2, Local, Trace } from '@ohos.arkui.stateManagement';
import { Entry, ComponentV2, Column, Button, Text } from '@ohos.arkui.component';

@ObservedV2
class Test {
  @Trace array: int[] = [1, 2, 3];
  arrayMonitor?: IMonitorDecoratedVariable;

  constructor() {
    // 对于每个数组元素映射到一个
    // 返回该元素的箭头函数
    let callbackArray = this.array.map(
      (_: int, index: number): (() => Any) => () => this.array[Double.toInt(index)]
    );

    // 监听数组长度
    callbackArray.push(() => this.array.length);

    this.arrayMonitor = UIUtils.addMonitor(callbackArray, this.onChange);
  }

  onChange(monitor: IMonitor) {
    console.info('[DynamicMonitor] Callback triggered.');

    monitor.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] Value ${path} has changed from ${monitor.value<int>(path)?.before} to ${monitor.value<int>(path)?.now}.`);
    });
  }
}

@Entry
@ComponentV2
struct Page {
  @Local obj: Test = new Test();

  aboutToAppear() {
    console.info('[DynamicMonitor] Test case begin.')
  }

  build() {
    Column() {
      Text(`Current array is: ${this.obj.array}`)
      Button('Add new value into array')
        .onClick(() => {
          this.obj.array.push(42);
        })
      Button('Increase registered value')
        .onClick(() => {
          for (let index: int = 0; index < 3; index++) {
            this.obj.array[index]++;
          }
        })
    }
  }
}
```

### 配置同步监听模式的回调函数

相比于异步模式，同步模式在每一次被监听的变量改变时都会立即触发一次回调函数。

```typescript
'use static'

import { Local, IMonitor, IMonitorDecoratedVariable, UIUtils } from '@ohos.arkui.stateManagement';
import { ComponentV2, Column, Text, Entry, Button } from '@ohos.arkui.component';

@Entry
@ComponentV2
struct Page {
  @Local value: int = 0;
  valueMonitor?: IMonitorDecoratedVariable;

  aboutToAppear() {
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange, { isSynchronous: true });
  }

  onChange(mon: IMonitor) {
    mon.dirty.forEach((path: string) => {
      console.info(`onChange: value ${path} has changed from ${mon.value<int>(path)?.before} to ${mon.value<int>(path)?.now}.`);
    })
  }

  build() {
    Column() {
      Text(`Current value is ${this.value}`)
      Button('Increase value')
        .onClick(() => {
          this.value++;
          this.value++;
        })
    }
  }
}
```

### 监听构造函数中同步修改的状态变量的变化

和@Monitor异步构造不同，addMonitor是同步构造的，所以在开发者调用完`UIUtils.addMonitor(() => this.message, this.onMessageChange)`后就完成了对`message`添加监听函数`this.onMessageChange`。在下面的例子中：

* 拉起页面，构造`Info`的实例，回调`onMessageChange`监听函数。日志输出如下：
```
message change from not initialized to initialized
message change from initialized to Index aboutToAppear
```
* 点击`Button('change message')`，回调`onMessageChange`监听函数。 日志输出如下：
```
message change from Index aboutToAppear to Index click to change message
```

```typescript
'use static'

import { ObservedV2, Trace, Local, IMonitor, IMonitorDecoratedVariable, UIUtils } from '@ohos.arkui.stateManagement';
import { ComponentV2, Column, Entry, Button } from '@ohos.arkui.component';

@ObservedV2
class Info {
  @Trace message: string = 'not initialized';
  messageMonitor?: IMonitorDecoratedVariable;

  constructor() {
    this.messageMonitor = UIUtils.addMonitor(() => this.message, this.onMessageChange);
    this.message = 'initialized';
  }
  onMessageChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`message change from ${monitor.value<string>(path)?.before} to ${monitor.value<string>(path)?.now}`);
    });
  }
}

@Entry
@ComponentV2
struct Page {
  @Local info: Info = new Info();

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

### 动态取消@ObservedV2/@ComponentV2实例的监听

和@Monitor不同，addMonitor/clearMonitor可以对不同的@ObservedV2/@ComponentV2实例动态添加监听函数。

```typescript
'use static'

import { ObservedV2, Trace, Local, Param, Require, IMonitor, IMonitorDecoratedVariable, UIUtils } from '@ohos.arkui.stateManagement';
import { ComponentV2, Column, Entry, Button, Text } from '@ohos.arkui.component';

@ObservedV2
class User {
  @Trace age: number = 10;
  ageMonitor?: IMonitorDecoratedVariable;

  onChange(mon: IMonitor) {
    mon.dirty.forEach((path: string) => {
      console.info(`onChange: User property ${path} change from ${mon.value<number>(path)?.before} to ${mon.value<number>(path)?.now}`);
    });
  }

  constructor(needMonitor: boolean) {
    if (needMonitor) {
      this.ageMonitor = UIUtils.addMonitor(() => this.age, this.onChange);
    }
  }
}

@Entry
@ComponentV2
struct Page {
  @Local user1: User = new User(true);
  @Local user2: User = new User(false);
  @Local count: number = 10;

  build() {
    Column() {
      Text(`user1 age ${this.user1.age}`).fontSize(20).onClick(() => {
        // 有Monitor回调
        this.user1.age++;
      })
      Text(`user2 age ${this.user2.age}`).fontSize(20).onClick(() => {
        // 无Monitor回调
        this.user2.age++;
      })
      Button(`remove user1 monitor`).onClick(() => {
        UIUtils.clearMonitor(this.user1.ageMonitor!);
      })

      Button(`change count`).onClick(() => {
        this.count++;
      })

      Child({ needMonitor: true, count: this.count })
      Child({ needMonitor: false, count: this.count })
    }
  }
}

@ComponentV2
struct Child {
  @Require @Param needMonitor: boolean = false;
  @Require @Param count: number = 0;
  countMonitor?: IMonitorDecoratedVariable;

  onChange(mon: IMonitor) {
    mon.dirty.forEach((path: string) => {
      console.info(`Child needMonitor ${this.needMonitor} onChange: property ${path} change from ${mon.value<number>(path)?.before} to ${mon.value<number>(path)?.now}`);
    });
  }

  aboutToAppear(): void {
    if (this.needMonitor) {
      this.countMonitor = UIUtils.addMonitor(() => this.count, this.onChange);
    }
  }

  build() {
    Column() {
      Text(`${this.count}`).fontSize(20)
    }
  }
}
```