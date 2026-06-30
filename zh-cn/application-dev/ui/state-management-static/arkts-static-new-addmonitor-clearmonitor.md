# addMonitor/clearMonitor接口：动态添加/取消监听

从API version 23开始，开发者可以使用[addMonitor](../../reference/apis-arkui/js-apis-stateManagement-static.md#addmonitor23)与[clearMonitor](../../reference/apis-arkui/js-apis-stateManagement-static.md#clearmonitor23)方法，在应用程序运行过程中动态地为状态变量添加或删除监听函数。

在阅读本文档前，建议提前阅读：[@ObservedV2/@Trace](./arkts-static-new-observedV2-and-trace.md)、[@ComponentV2](./arkts-static-componentv2.md)、[@Local](./arkts-static-new-local.md)，[@Monitor](./arkts-static-new-monitor.md)。

>**说明：**
>
>从API版本26.0.0开始，支持使用重载的addMonitor接口实现属性变化监听能力，其作用等效于通配符观察。

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

<!-- @[AddMonitorBasic](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorBasic.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, Local, ObservedV2, Trace, UIUtils } from '@kit.ArkUI';

@ObservedV2
export class Test {
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

  onChange(m: IMonitor): void {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<string>(path)?.before} to ${m.value<string>(path)?.now}`);
    });
  }

  onArrayChange(m: IMonitor): void {
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

<!-- @[AddMonitorDuplicated](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorDuplicated.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, Local, ObservedV2, Trace, UIUtils } from '@kit.ArkUI';

@ObservedV2
export class Test {
  @Trace value: int = 0;
  valueMonitor?: IMonitorDecoratedVariable;
  valueMonitorDuplicated?: IMonitorDecoratedVariable;

  constructor() {
    // 可以重复为同一对状态变量和回调函数多次添加监听关系
    // 但返回不同的唯一性句柄
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange);
    this.valueMonitorDuplicated = UIUtils.addMonitor(() => this.value, this.onChange);
  }

  onChange(m: IMonitor): void {
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

<!-- @[AddMonitorSyncMode](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorSyncMode.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, Local, ObservedV2, Trace, UIUtils } from '@kit.ArkUI';

@ObservedV2
export class Test {
  @Trace value: string = '';
  @Trace value2: string = '';
  valueMonitor?: IMonitorDecoratedVariable;
  value2Monitor?: IMonitorDecoratedVariable;

  constructor() {
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange);
    this.value2Monitor = UIUtils.addMonitor(() => this.value2, this.onSyncChange, { isSynchronous: true });
  }

  onChange(m: IMonitor): void {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value has changed from ${m.value<string>(path)?.before} to ${m.value<string>(path)?.now}`);
    });
  }

  onSyncChange(m: IMonitor): void {
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

<!-- @[AddMonitorOwner](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorOwner.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, Local, Text, UIUtils } from '@kit.ArkUI';

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

<!-- @[AddMonitorPath](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorPath.ets) -->

``` TypeScript
import { UIUtils, IMonitor, IMonitorDecoratedVariable, Local, Entry, ComponentV2,
         Row, Column, Text, Button, UIUtils } from '@kit.ArkUI';

export interface Pair<R, V> {
  key: R;
  value: V;
};

@Entry
@ComponentV2
struct Page {
  @Local singleValue: int = 0;
  // 需要用UIUtils.makeObserved封装字面量才具备观测能力。
  @Local pairValue: Pair<int, int> = UIUtils.makeObserved({ key: 42, value: 35 } as Pair<int, int>);
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
    const valueCallback = this.multipleValue.map((_: int, index: int): (() => Any) => (
      () => this.multipleValue[index]
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

* 通过向`addMonitor`传递[MonitorOptions.owner](../../reference/apis-arkui/js-apis-stateManagement-static.md#monitoroptions23)参数，可为`addMonitor`启用组件冻结功能。启用组件冻结后，被监听的状态变量修改后回调函数的触发会被推迟，直到包含该状态变量的组件从`inactive`状态变为`active`时才会触发。`MonitorOptions.owner`参数仅支持为`@ObservedV2`类中属性的监听器添加组件冻结能力。如果监听的属性是组件里的状态变量，如`@Local`等状态变量装饰器修饰的属性，则该状态变量默认继承组件的冻结能力，调用`addMonitor`时无需传递`MonitorOptions.owner`参数。

<!-- @[AddMonitorFreeze](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorFreeze.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, DatePicker, Divider, Entry, FontWeight, ForEach, IMonitor, IMonitorDecoratedVariable, Local, LocalStorageLink, ObservedV2, Param, Require, Row, Scroll, TabContent, Tabs, Text, TextAlign, Trace, UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct TabContentTest {
  @Local childMessage: Message = new Message();
  @Local data: number[] = [0, 1, 2];

  build() {
    Row() {
      Column() {
        // 当被监听的状态变量修改时，active页面的回调函数会正常触发
        // inactive页面的回调函数触发会推迟到页面变为active状态
        Button('change message').onClick(() => {
          this.childMessage.message++;
        })
        Tabs() {
          ForEach(this.data, (item: number) => {
            TabContent() {
              FreezeChild({ index: item, childMsg: this.childMessage})
            }.tabBar(`tab${item}`)
          }, (item: number) => item.toString())
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}

@ObservedV2
export class Message {
  @Trace message: number = 0;
}

@ComponentV2
struct FreezeChild {
  @Param childMsg: Message = new Message();
  @Param index: number = 0;
  messageMonitor?: IMonitorDecoratedVariable;

  aboutToAppear(): void {
    // 监听属性是@ObservedV2内部属性时，设置owner能让监听继承当前组件的冻结能力。
    this.messageMonitor = UIUtils.addMonitor(() => this.childMsg.message, this.messageChange, { path: ['message'] , owner: this });
  }

  messageChange(m: IMonitor) {
    m.dirty.forEach((path: string) => {
      console.info(`[addMonitorTest] ${path} changed from ${m.value<number>(path)?.before} to ${m.value<number>(path)?.now}, index: ${this.index}`);
    });
  }

  build() {
    Text(`设置owner ${this.childMsg.message}, index: ${this.index}`)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
  }
}
```

## 限制条件

* 对于可选参数`MonitorOptions.owner`，若其被[@Component](./arkts-static-create-component.md)而非@ComponentV2装饰，则在运行时抛出130000错误。

<!-- @[add_monitor_owner_error](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorOwnerError.ets) -->

``` TypeScript
import { Button, Column, Component, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, State, Text, UIUtils } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Component
struct Test {
  @State value: int = 0;
  valueMonitor?: IMonitorDecoratedVariable;

  aboutToAppear() {
    try {
      // 触发 130000 BusinessError
      this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange, { owner: this });
    } catch (err) {
      // 错误码需要捕获异常后输出
      if (err instanceof BusinessError) {
        console.error(`[DynamicMonitor] Error code: ${err.code}, message: ${err.message}`);
      }
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
struct AddMonitorOwnerErrorExample {
  build() {
    Column() {
      Test()
    }
  }
}
```

* addMonitor监听的变量类型与在回调函数中访问的类型必须匹配，否则会抛出异常，且无法通过`dirty`获取状态变量的新值与旧值，但仍能触发回调函数。


<!-- @[add_monitor_type_mismatch](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorTypeMismatch.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, Local, ObservedV2, Trace, UIUtils } from '@kit.ArkUI';

@ObservedV2
export class Test {
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

  onChange(m: IMonitor): void {
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
struct AddMonitorTypeMismatchExample {
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

<!-- @[add_monitor_container](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorContainer.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, Local, ObservedV2, Text, Trace, UIUtils } from '@kit.ArkUI';

@ObservedV2
export class Test {
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

  onChange(m: IMonitor): void {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<Array<int>>(path)?.before} to ${m.value<Array<int>>(path)?.now}`);
    })
  }

  onMapChange(m: IMonitor): void {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<Map<number, string>>(path)?.before} to ${m.value<Map<number, string>>(path)?.now}`);
    })
  }
}

@Entry
@ComponentV2
struct AddMonitorContainerExample {
  @Local obj: Test = new Test();

  aboutToAppear(): void {
    console.info('[DynamicMonitor] Test case begin.');
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

<!-- @[add_monitor_clear_monitor_with_monitor](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorClearMonitorWithMonitor.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, Local, Monitor, ObservedV2, Trace, UIUtils } from '@kit.ArkUI';

@ObservedV2
export class Test {
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
  onChange(m: IMonitor): void {
    m.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] value ${path} has changed from ${m.value<int>(path)?.before} to ${m.value<int>(path)?.now}`);
    })
  }
}

@Entry
@ComponentV2
struct AddMonitorClearMonitorWithMonitorExample {
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

<!-- @[AddMonitorObservedV2Local](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorObservedV2Local.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, Local, ObservedV2, Text, Trace, UIUtils } from '@kit.ArkUI';

// class使用@ObservedV2修饰
@ObservedV2
export class Test {
  // @ObserevdV2与@Trace搭配使用
  @Trace value: int = 0;
  valueMonitor?: IMonitorDecoratedVariable;

  constructor() {
    this.valueMonitor = UIUtils.addMonitor(() => this.value, this.onChange);
  }

  onChange(m: IMonitor): void {
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

<!-- @[AddMonitorArray](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorArray.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, Local, ObservedV2, Text, Trace, UIUtils } from '@kit.ArkUI';

@ObservedV2
export class Test {
  @Trace array: int[] = [1, 2, 3];
  arrayMonitor?: IMonitorDecoratedVariable;

  constructor() {
    // 对于每个数组元素映射到一个
    // 返回该元素的箭头函数
    let callbackArray = this.array.map(
      (_: int, index: int): (() => Any) => () => this.array[index]
    );

    // 监听数组长度
    callbackArray.push(() => this.array.length);

    this.arrayMonitor = UIUtils.addMonitor(callbackArray, this.onChange);
  }

  onChange(monitor: IMonitor): void {
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

<!-- @[AddMonitorSyncCallback](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorSyncCallback.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, Local, Text, UIUtils } from '@kit.ArkUI';

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
```text
message change from not initialized to initialized
```
* 点击`Button('change message')`，回调`onMessageChange`监听函数。 日志输出如下：
```text
message change from initialized to Index click to change message
```

> **说明**
>
> 在ArkTS-Dyn中，如果在`Index`组件的`aboutToAppear`中修改`message`，会额外触发`onMessageChange`回调；ArkTS-Sta中，由于对[@Monitor回调触发机制更改](./arkts-state-management-dynamic-static-compare.md#修改状态变量后monitor回调的触发机制不同)，导致`aboutToAppear`中修改`message`会覆盖`construtor`里的修改，只会触发一次`onMessageChange`回调。

<!-- @[AddMonitorConstructor](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorConstructor.ets) -->

``` TypeScript
import { ObservedV2, Trace, Local, IMonitor, IMonitorDecoratedVariable, UIUtils,
         ComponentV2, Column, Entry, Button } from '@kit.ArkUI';

@ObservedV2
export class Info {
  @Trace message: string = 'not initialized';
  messageMonitor?: IMonitorDecoratedVariable;

  constructor() {
    this.messageMonitor = UIUtils.addMonitor(() => this.message, this.onMessageChange);
    this.message = 'initialized';
  }
  onMessageChange(monitor: IMonitor): void {
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
    // 静态ArkTS中会覆盖constructor里对message的修改，只触发一次onMessageChange回调。
    // this.info.message = 'Index aboutToAppear';
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

<!-- @[AddMonitorDynamicCancel](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorDynamicCancel.ets) -->

``` TypeScript
import { Button, Column, ComponentV2, Entry, IMonitor, IMonitorDecoratedVariable, Local, ObservedV2, Param, Require, Text, Trace, UIUtils } from '@kit.ArkUI';

@ObservedV2
export class User {
  @Trace age: number = 10;
  ageMonitor?: IMonitorDecoratedVariable;

  onChange(mon: IMonitor): void {
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

### 使用addMonitor观察对象属性

从API版本26.0.0开始，addMonitor新增重载实现，用于实现对对象的属性观察能力，其作用等效于通配符能力。开启对对象属性的观察能力，需要使用新的[addMonitor](../../reference/apis-arkui/js-apis-stateManagement-static.md#addmonitor)方法，配置[MonitorValueInfo](../../reference/apis-arkui/js-apis-stateManagement-static.md#monitorvalueinfo)中`observeProp`项为true。同时可以配置每一个监听变量所对应的路径信息。使用新的addMonitor方法注册监听时，将不对路径合法性进行校验，仅作为每一个监听变量变化时返回的路径名。

正确使用新addMonitor方法的方式如下：

```ts
UIUtils.addMonitor({ valueCallback: () => this.obj, path: 'obj.*', observeProps: true }, this.onChange);
```

以下写法将保持与原有addMonitor行为一致，不会生效属性观察能力，即使路径上含有通配符：

```ts
UIUtils.addMonitor({ valueCallback: () => this.obj, path: 'obj.*'}, this.onChange);
```

通配符路径的使用规则可以参考@Monitor文档中对[监听包含通配符的路径](arkts-static-new-monitor.md#监听包含通配符的路径)的说明。

使用新addMonitor方法观察对象属性变化的用例如下。

<!-- @[AddMonitorObjectProperty](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/AddMonitorDecorator/entry/src/main/ets/pages/AddMonitorObjectProperty.ets) -->

``` TypeScript
import { Entry, Text, Column, ComponentV2, Button,
  ObservedV2, Trace, Local, Monitor, IMonitor, UIUtils, IMonitorDecoratedVariable } from '@kit.ArkUI';
import hilog from '@ohos.hilog';

@ObservedV2
export class ClassA {
  @Trace propA: int = 8;
  @Trace propB: int = 99;

  constructor(a: int, b: int) {
    this.propA = a;
    this.propB = b;
  }
}

@Entry
@ComponentV2
struct AddMonitorObject {
  @Local cls: ClassA = new ClassA(100, 100);
  monitorHandle: IMonitorDecoratedVariable | undefined = undefined;
  onClsChanged(m: IMonitor) {
    hilog.info(0xFF00, 'testTag', '%{public}s', `### onClsChanged, dirty: ${m.dirty.toString()}`);
  }

  aboutToAppear(): void {
    // 监听cls中的属性变化，设置路径为'cls.*'
    this.monitorHandle = UIUtils.addMonitor({ valueCallback: () => this.cls, observeProps: true, path: 'cls.*'}, this.onClsChanged);
  }

  build() {
    Column() {
      Button(`Change propA: ${this.cls.propA}`)
        .onClick(() => {
          this.cls.propA += 1; // onClsChanged回调触发
        })
      Button(`Change propB: ${this.cls.propB}`)
        .onClick(() => {
          this.cls.propB += 1; // onClsChanged回调触发
        })
      Button('Assign new object')
        .onClick(() => {
          this.cls = new ClassA(-200, -200); // onClsChanged回调触发
        })
      Button('clear').onClick(() => {
        UIUtils.clearMonitor(this.monitorHandle!); // 取消监听
      })
    }
  }
}
```
