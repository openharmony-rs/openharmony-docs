# 状态管理动静态差异

由于动态语言不支持多线程，因此在动态语言上演进出静态语言，以原生支持多线程。

部分基于动态语言实现的功能无法通过静态语言实现，导致部分功能受限或行为发生更改。下面介绍状态管理功能在ArkTS-Dyn和ArkTS-Sta上的差异。

## V1和V2混用无需enableV2Compatibility

在ArkTS-Dyn（API version 19之后）中，状态管理V1和V2混用时，需要调用[`UIUtils.enableV2Compatibility`](../state-management/arkts-v1-v2-mixusage.md#enablev2compatibility)和[`UIUtils.makeV1Observed`](../state-management/arkts-v1-v2-mixusage.md#makev1observed)接口来实现V1和V2的状态变量传递。

而在ArkTS-Sta中，由于采用相同的状态管理实现逻辑，`@Component`和`@ComponentV2`天然支持V1/V2状态变量的传递，因此无需调用`UIUtils.enableV2Compatibility`和`UIUtils.makeV1Observed`接口，可以直接混用状态管理V1与V2。


具体混用规则可参考[状态管理V1V2混用指导](./arkts-static-v1-v2-mixusage.md)。

## 静态无需mutableBuilder

在ArkTS-Dyn中，当需要动态切换全局@Builder时，需要使用mutableBuilder来实现，因为[wrapBuilder](../state-management/arkts-wrapBuilder.md)不支持二次赋值。

而在ArkTS-Sta中，由于采用静态语言特性，可以直接使用状态变量配合条件渲染来实现全局@Builder的动态切换，无需使用mutableBuilder。

例如：

<!-- @[static_no_mutable_builder](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaCompare/entry/src/main/ets/pages/StaticNoMutableBuilder.ets) -->

``` TypeScript
import { Entry, Builder, ComponentV2, Local, Text, Button, Column } from '@kit.ArkUI';

@Builder
function textBuilder(p: { text: string }) {
  Text(p.text)
}

@Builder
function buttonBuilder(p: { text: string }) {
  Button(p.text)
}

@Entry
@ComponentV2
struct Index {
  @Local useText: boolean = true;
  @Local message: string = 'init';

  build() {
    Column() {
      // 直接通过条件判断切换@Builder
      if (this.useText) {
        textBuilder({ text: this.message })
      } else {
        buttonBuilder({ text: this.message })
      }
      Button('Switch Builder')
        .onClick(() => {
          this.useText = !this.useText;
        })
    }
  }
}
```

## 双向绑定语法差异

ArkTS在不同语言版本和状态管理版本中提供了不同的双向绑定方式。

### 三种方式对比

| 特性 | 动态：`$$` 运算符 | 动态：`!!` 运算符 | 静态：`$$()` 函数 |
|------|------------------|------------------|-----------------|
| 语言版本 | ArkTS-Dyn | ArkTS-Dyn | ArkTS-Sta (静态) |
| 状态管理版本 | V1 | V2 | V1 |
| 系统组件双向绑定 | 支持 `$$this.text` | 支持 `this.text!!` | 支持 `$$(this.text)` |
| 自定义组件双向绑定 | 不支持 | 支持 `this.value!!` 语法糖 | 不支持，需使用@Param+@Event |
| 语法形式 | 前缀运算符 | 后缀运算符 | 函数调用 |
| 是否需要导入 | 否 | 否 | 是，需导入 `$$` |
| 起始API版本 | API 10 | API 12 | API 23 |

### 关键差异说明
- 自定义组件双向绑定

  ArkTS-Dyn：支持 `!!` 语法糖（API 12+）

   ```typescript
   // ArkTS-Dyn - 使用!!语法糖
   @ComponentV2
   struct Child {
     @Param value: number = 0;
     @Event $value: (val: number) => void = () => {};
   }

   // 父组件中直接使用!!语法糖
   Child({ value: this.value!! })
   ```

   ArkTS-Sta：不支持 `!!` 语法糖，必须显式使用 @Param + @Event

   ```typescript
   // ArkTS-Sta - 必须显式传递@Param和@Event
   import { ComponentV2, Param, Event } from '@kit.ArkUI';

   @ComponentV2
   struct Child {
     @Param value: number = 0;
     @Event $value: (val: number) => void = () => {};
   }

   // 父组件中必须显式传递参数
   Child({
     value: this.value,
     $value: (val: number) => { this.value = val; }
   })
   ```

- 系统组件双向绑定

   ArkTS-Dyn：

   - `$$` 运算符（API 10）
   - `!!` 运算符（API 12，推荐）

   ```typescript
   // ArkTS-Dyn - $$运算符
   TextInput({ text: $$this.text })
   
   // ArkTS-Dyn - !!运算符（API 12+，推荐使用）
   TextInput({ text: this.text!! })
   ```

   ArkTS-Sta：使用 `$$()` 函数

   ```typescript
   // ArkTS-Sta - $$()函数
   import { $$, TextInput } from '@ohos.arkui.component';
   
   TextInput({ text: $$(this.stateVar) })
   ```

### 使用建议

- ArkTS-Dyn状态管理V2：
   - 系统组件推荐使用 `!!` 运算符（API 12+）。
   - 自定义组件使用 `!!` 运算符实现双向绑定。

- ArkTS-Sta (静态)：
  - 系统组件使用 `$$()` 函数。
  - 自定义组件使用 `@Param` + `@Event` 显式传递，不支持语法糖。

## 修改状态变量后，@Monitor回调的触发机制不同

在状态变量被修改后，状态管理框架需要异步触发依赖状态变量的回调函数，比如触发[@Monitor](./arkts-static-new-monitor.md)回调，或者触发[@Computed](./arkts-static-new-computed.md)重新计算。ArkTS-Dyn中，该触发机制使用Promise任务异步，新建的Promise会被存入任务队列并延时执行。

ArkTS-Sta中，状态管理框架使用Vsync（渲染同步信号）异步触发依赖更新，在每一帧渲染UI组件之前执行依赖状态变量的回调函数。所以状态管理回调的触发机制不再依赖Promise任务，而是申请额外的Vsync渲染。Vsync由后端触发执行，相比Promise方案性能更好，但是可能会导致监听回调函数被执行的次数变少。受影响的[addMonitor](./arkts-static-new-addmonitor-clearmonitor.md)示例如下。

ArkTS-Dyn示例：

<!-- @[monitor_trigger_dyn](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynCompare/entry/src/main/ets/pages/MonitorTriggerDyn.ets) -->

``` TypeScript
import { UIUtils } from '@kit.ArkUI';

@ObservedV2
class Info {
  @Trace message: string = 'not initialized';

  constructor() {
    UIUtils.addMonitor(this, 'message', this.onMessageChange);
    // 会触发onMessageChange回调，打印`message change from not initialized to initialized`
    this.message = 'initialized';
  }
  onMessageChange(monitor: IMonitor) {
    console.info(`message change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
}

@Entry
@ComponentV2
struct Page {
  info: Info = new Info();

  aboutToAppear(): void {
    // 会再次触发onMessageChange回调，打印`message change from initialized to Index aboutToAppear`
    this.info.message = 'Index aboutToAppear';
  }

  build() {
    Column() {
      Text('Hello world')
    }
  }
}
```

ArkTS-Sta示例：


<!-- @[monitor_trigger_sta](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaCompare/entry/src/main/ets/pages/MonitorTriggerSta.ets) -->

``` TypeScript
import { ObservedV2, Trace, Local, IMonitor, IMonitorDecoratedVariable, UIUtils,
         ComponentV2, Column, Entry, Button, Text } from '@kit.ArkUI';

@ObservedV2
class Info {
  @Trace message: string = 'not initialized';
  messageMonitor?: IMonitorDecoratedVariable;

  constructor() {
    this.messageMonitor = UIUtils.addMonitor(() => this.message, this.onMessageChange);
    // 不会触发onMessageChange回调，因为this.message修改时申请的Vsync在下方aboutToAppear执行后才被执行
    // 导致该修改被下方aboutToAppear里的修改覆盖。
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
    // 触发onMessageChange回调，打印`message change from not initialized to Index aboutToAppear`
    this.info.message = 'Index aboutToAppear';
  }

  build() {
    Column() {
      Text('Hello world')
    }
  }
}
```

## globalConnect接口变更

PersistenceV2的globalConnect接口在ArkTS-Dyn和ArkTS-Sta上存在API层面的差异。以下以持久化Array类型为例进行说明。

### API差异对比

| 差异点 | ArkTS-Dyn | ArkTS-Sta |
|--------|-----------|-----------|
| globalConnect调用 | `PersistenceV2.globalConnect({...})` | `PersistenceV2.globalConnect<Array<Person>>({...})` |
| type参数 | `type: Array<Person>` | `type: Class.from<Array<Person>>()` |
| 嵌套类型标记 | class中使用[\@Type](../state-management/arkts-new-type.md)装饰器标记嵌套类型属性 | 不使用\@Type，统一通过[StorageDefaultSubCreators](../../reference/apis-arkui/js-apis-stateManagement-static.md#storagedefaultsubcreators)批量注册 |
| 子元素构造器 | [defaultSubCreator](../../reference/apis-arkui/js-apis-stateManagement.md#connectoptionscollectionst-s23)：传入单个工厂函数<br>`defaultSubCreator: () => new Person()` | [defaultSubCreators](../../reference/apis-arkui/js-apis-stateManagement-static.md#connectoptions)：传入StorageDefaultSubCreators构造器集合<br>`defaultSubCreators: creators` |

### 差异说明

- globalConnect调用：ArkTS-Dyn中无需显式泛型；ArkTS-Sta需要显式指定泛型类型参数，以便编译器进行类型推断和检查。
- type参数：ArkTS-Dyn中可以直接将类型作为参数传入；ArkTS-Sta中由于静态语言无法直接传递类型，需通过 `Class.from<>()` 获取类型元信息。
- 嵌套类型标记：ArkTS-Dyn中，对于class中嵌套的自定义类属性，需要在class中使用\@Type装饰器标记类型；ArkTS-Sta中不使用\@Type装饰器，而是统一通过StorageDefaultSubCreators一次性注册所有嵌套类型的构造器。
- 子元素构造器：ArkTS-Dyn中通过defaultSubCreator传入单个工厂函数；ArkTS-Sta中通过StorageDefaultSubCreators批量注册所有嵌套类型后，通过defaultSubCreators参数传入构造器集合。

### 示例对比

以持久化 `Array<Person>` 类型数据为例，其中 `Person` 包含嵌套类型 `Info`，`Info` 中包含嵌套类型 `Inner`。

ArkTS-Dyn示例：

<!-- @[global_connect_dyn](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/DynCompare/entry/src/main/ets/pages/GlobalConnectDyn.ets) -->

``` TypeScript
import { PersistenceV2, UIUtils, Type } from '@kit.ArkUI';

@ObservedV2
class Inner {
  @Trace age: number = 24; // 迁移时需将number改为int等静态类型
}

@ObservedV2
class Info {
  @Trace userInfo: number = 1;
  @Trace arr: Array<Inner> = new Array<Inner>();
}

@ObservedV2
class Person {
  @Trace userName: string = 'John';
  userId: number = 1;
  @Type(Info) // 迁移时需移除@Type装饰器，嵌套类型改由defaultSubCreators统一注册
  @Trace info: Info = new Info();
}

@Entry
@ComponentV2
struct Index {
  // globalConnect调用迁移时需：
  // - 添加显式泛型类型参数<Array<Person>>
  // - type参数改为Class.from<Array<Person>>()
  // - defaultSubCreator改为defaultSubCreators，传入StorageDefaultSubCreators
  @Local stateVar: Array<Person> = PersistenceV2.globalConnect({
    type: Array<Person>,
    key: 'PersonArray',
    // 动态中defaultCreator需要使用makeObserved包装，确保从磁盘恢复的数据具备观察能力以实现自动持久化
    // 静态中可无需makeObserved包装，去除即可
    defaultCreator: () => UIUtils.makeObserved(new Array<Person>()),
    // 迁移时需替换为defaultSubCreators + StorageDefaultSubCreators
    defaultSubCreator: () => new Person()
  })!;

  build() {
    Column() {
      Text(`length: ${this.stateVar.length}`)
      Button('push')
        .onClick(() => {
          this.stateVar.push(new Person());
        })
      List() {
        ForEach(this.stateVar, (item: Person, index: number) => {
          ListItem() {
            Column() {
              Text(`item: ${item.userName}`)
                .onClick(() => {
                  item.userName += '~';
                  item.info.userInfo++;
                  let inner = new Inner();
                  inner.age = item.info.userInfo;
                  item.info.arr.push(inner);
                })
              Text(`userInfo: ${item.info.userInfo}`)
            }
          }
        }, (item: Person, index: number) => {
          return item.userName + index.toString();
        })
      }
    }
  }
}
```

ArkTS-Sta示例：

<!-- @[global_connect_sta](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaCompare/entry/src/main/ets/pages/GlobalConnectSta.ets) -->

``` TypeScript
// 迁移步骤1：移除Type的导入，新增StorageDefaultSubCreators的导入
import { PersistenceV2, ObservedV2, Trace, Entry, ComponentV2, Local,
  Column, Text, Button, ForEach, List, ListItem, StorageDefaultSubCreators } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

@ObservedV2
export class Inner {
  @Trace age: int = 24; // 迁移步骤2：数值类型从number改为int等静态类型
}

@ObservedV2
export class Info {
  @Trace userInfo: int = 1;
  @Trace arr: Array<Inner> = new Array<Inner>();
}

@ObservedV2
export class Person {
  @Trace userName: string = 'John';
  userId: int = 1;
  @Trace info: Info = new Info(); // 迁移步骤3：移除@Type装饰器，嵌套类型通过defaultSubCreators统一注册
}

// 迁移步骤4：使用StorageDefaultSubCreators批量注册所有嵌套类型的构造器，替代动态中的@Type + defaultSubCreator
const creators = new StorageDefaultSubCreators([
  [Class.from<Person>(), () => new Person()],
  [Class.from<Inner>(), () => new Inner()],
  [Class.from<Info>(), () => new Info()]
]);

@Entry
@ComponentV2
struct Index {
  // 迁移步骤5：globalConnect调用变更
  // - 添加显式泛型类型参数<Array<Person>>
  // - type参数使用Class.from<Array<Person>>()替代Array<Person>
  // - defaultCreator无需再调用makeObserved包装，去除即可
  // - 使用defaultSubCreators替代defaultSubCreator，传入上述批量注册的构造器集合
  @Local stateVar: Array<Person> = PersistenceV2.globalConnect<Array<Person>>({
    type: Class.from<Array<Person>>(),
    key: 'PersonArray',
    defaultCreator: () => {
      return new Array<Person>();
    },
    areaMode: contextConstant.AreaMode.EL1,
    enableAutoSave: true,
    defaultSubCreators: creators
  })!;

  build() {
    Column(undefined) {
      Text(`length: ${this.stateVar.length}`)
      Button('push')
        .onClick(() => {
          this.stateVar.push(new Person());
        })
      List() {
        ForEach(this.stateVar, (item: Person, index: int) => {
          ListItem() {
            if (item instanceof Person) {
              Column() {
                Text(`item: ${item.userName}`)
                  .onClick(() => {
                    item.userName += '~';
                    item.info.userInfo++;
                    let inner = new Inner();
                    inner.age = item.info.userInfo;
                    item.info.arr.push(inner);
                  })
                Text(`userInfo: ${item.info.userInfo}`)
              }
            }
          }
        }, (item: Person, index: int) => {
          return item.userName + index.toString();
        })
      }
    }
  }
}
```

### 迁移步骤说明

从ArkTS-Dyn的globalConnect迁移到ArkTS-Sta，需要完成以下步骤：

1. 移除[\@Type](../state-management/arkts-new-type.md)装饰器：静态ArkTS中不再使用\@Type标记嵌套类型属性，嵌套类型统一通过构造器注册机制处理。

2. 使用[StorageDefaultSubCreators](../../reference/apis-arkui/js-apis-stateManagement-static.md#storagedefaultsubcreators)批量注册嵌套类型：将动态中\@Type装饰器 + [defaultSubCreator](../../reference/apis-arkui/js-apis-stateManagement.md#connectoptionscollectionst-s23)的方式，替换为通过StorageDefaultSubCreators一次性注册所有嵌套类型（包括Person、Info、Inner）的构造器，每个构造器使用 `Class.from<>()` 指定类型。

3. 调整globalConnect调用方式：添加显式泛型参数 `<Array<Person>>`；`type` 参数从直接传入类型改为使用 `Class.from<>()` 包裹。

4. 关于[UIUtils.makeObserved](../../reference/apis-arkui/js-apis-stateManagement.md#makeobserved)调用：动态中defaultCreator和defaultSubCreator需要通过makeObserved包装返回值，以确保从磁盘恢复的数据具备观察能力以实现自动持久化；静态中可无需makeObserved包装，去除即可。

5. 替换defaultSubCreator为[defaultSubCreators](../../reference/apis-arkui/js-apis-stateManagement-static.md#connectoptions)：将上述通过StorageDefaultSubCreators创建的构造器集合，通过defaultSubCreators参数传入globalConnect。

