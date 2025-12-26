# @Monitor

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 23开始，支持该装饰器。

@Monitor用于状态管理V2中，监听状态变量修改，使得状态变量具有深度监听的能力。

在ArkTS-Sta中使用时，开发指南参考：[@Monitor装饰器：状态变量修改监听（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-new-monitor.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型     | 必填 | 说明                                         |
| ------ | -------- | ---- | -------------------------------------------- |
| path   | string[] | 是   | 用于设置对象属性名，可同时监听多个对象属性。 |

**示例：**

```ts
'use static'

import { Entry, ComponentV2, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { Local, Monitor, IMonitor } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello World';
  @Local name: string = 'Tom';
  @Monitor(['message', 'name'])
  onStrChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`${path} changed from ${monitor.value<Any>(path)?.before} to ${monitor.value<Any>(path)?.now}`);
    });
  }
  build() {
    Column() {
      Text(`message: ${this.message}`)
      Text(`name: ${this.name}`)
      Button('change string')
        .onClick((e: ClickEvent) => {
          this.message += '!';
          this.name = 'Jack';
        })
    }
  }
}
```

## IMonitor

当监听的变量变化时，状态管理框架侧将回调开发者注册的函数，并传入变化信息。变化信息的类型即为IMonitor类型。

### 属性

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称                | 类型            | 只读  | 可选 | 说明             |
| ------------------- | --------------- | ---- | --- | ---------------- |
| dirty               | Array\<string\> | 否   | 否  | 变化路径的数组。 |

### value

value\<T\>(path?: string): IMonitorValue\<T\> | undefined

获取指定path的变化信息。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| path   | string | 否   | 可选，被监听变量的路径。未指定时默认使用变化路径数组dirty中的第一个路径。 |

**返回值：**

| 类型                                                  | 说明                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| [IMonitorValue\<T\>](#imonitorvaluet)  \| undefined | @Monitor监听变量的路径以及变化前后值信息。<br>T为监听变量的类型。<br>当监听的路径不存在时，返回undefined。<br>当未指定路径时，默认返回变化路径数组dirty中第一个路径对应的信息。 |

**示例：**

```ts
'use static'
import { ObservedV2, Trace, Monitor, IMonitor, Entry, ComponentV2, Local, Column, Text } from '@kit.ArkUI';

@ObservedV2
class Info {
  @Trace name: string = 'Tom';
  @Trace age: number = 25;
  @Trace height: number = 175;
  @Monitor(['name']) // 监听一个变量
  onNameChange(monitor: IMonitor) {
    // 未指定value的入参时，默认使用dirty中的第一个路径作为入参
    console.info(`path: ${monitor.value<string>()?.path} change from ${monitor.value<string>()?.before} to ${monitor.value<string>()?.now}`);
  }
  @Monitor(['age', 'height']) // 监听多个变量
  onRecordChange(monitor: IMonitor) {
    // 指定value的入参时，将返回入参路径path对应的变量变化值信息
    monitor.dirty.forEach((path: string) => {
      console.info(`path: ${path} change from ${monitor.value<number>(path)?.before} to ${monitor.value<number>(path)?.now}`);
    })
  }
}
@Entry
@ComponentV2
struct Index {
  @Local info: Info = new Info();
  build() {
    Column() {
      Text(`info.name: ${this.info.name}`)
        .onClick((e) => {
          this.info.name = 'Bob'; // 输出日志：path: name change from Tom to Bob
        })
      Text(`info.age: ${this.info.age}, info.name: ${this.info.height}`)
        .onClick((e) => {
          this.info.age++; // 输出日志：path: age change from 25 to 26
          this.info.height++; // 输出日志：path: height change from 175 to 176
        })
    }
  }
}
```

## IMonitorValue\<T\>

@Monitor监听变量变化的具体信息，通过IMonitor的value接口获取。T为变量类型。

### 属性

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| before | T | 否 | 否 | 变量变化前的值。|
| now | T | 否 | 否 | 变量当前的值。|
| path | string | 否 | 否 | 变量的路径。|

**示例：**

```ts
'use static'
import { ObservedV2, Trace, Monitor, IMonitor, Entry, ComponentV2, Local, Column, Text } from '@kit.ArkUI';

@ObservedV2
class Info {
  @Trace name: string = 'Tom';
  @Monitor(['name'])
  onNameChange(monitor: IMonitor) {
    // value的返回值为IMonitorValue类型，可以通过该返回值获取变量变化的信息
    console.info(`path: ${monitor.value<string>()?.path} change from ${monitor.value<string>()?.before} to ${monitor.value<string>()?.now}`);
  }
}
@Entry
@ComponentV2
struct Index {
  @Local info: Info = new Info();
  build() {
    Column() {
      Text(`info.name: ${this.info.name}`)
        .onClick((e) => {
          this.info.name = 'Bob'; // 输出日志：path: name change from Tom to Bob
        })
    }
  }
}

```

## MonitorValueCallback

type MonitorValueCallback = () => Any

监听状态变量的回调类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Any | 被监听状态变量。 |

**示例：**

```typescript
'use static'

import { UIUtils, IMonitorDecoratedVariable, IMonitor, MonitorValueCallback, Entry, ComponentV2, Local, Column, Text, Button } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Page {
  @Local array: number[] = [0, 1, 2];
  monitor?: IMonitorDecoratedVariable;

  aboutToAppear() {
    // 将数组的每个元素包装为 MonitorValueCallback
    const valueCallback: MonitorValueCallback[] = this.array.map((_: number, index: number): MonitorValueCallback => (
      () => this.array[Double.toInt(index)]
    ));
    this.monitor = UIUtils.addMonitor(valueCallback, this.onChange);
  }

  onChange(mon: IMonitor) {
    console.info('[DynamicMonitor] Callback triggered.');
  }

  build() {
    Column() {
      Text(`Array: ${this.array}`)
      Button('Increase value')
        .onClick(() => {
          this.array.forEach((value: number, index: number) => {
            this.array[Double.toInt(index)] = value + 1;
          })
        })
    }
  }
}
```

## MonitorCallback

type MonitorCallback = (iMonitor: IMonitor) => void

触发监听时被调用的回调函数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iMonitor | [IMonitor](#imonitor) | 是 | 保存触发监听前后的值以及路径。|

**示例：**

```typescript
'use static'

import { UIUtils, IMonitorDecoratedVariable, IMonitor, MonitorCallback, Entry, ComponentV2, Local, Column, Text, Button } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Page {
  @Local value: number = 0;
  monitor?: IMonitorDecoratedVariable;

  aboutToAppear() {
    // 注册监听关系时传入回调函数
    const callback: MonitorCallback = this.onChange;
    this.monitor = UIUtils.addMonitor(() => this.value, callback);
    // 也可以直接将this.onChange作为参数传递给addMonitor
    // this.monitor = UIUtils.addMonitor(() => this.value, this.onChange);
  }

  // 触发的回调函数
  onChange(mon: IMonitor) {
    console.info('[DynamicMonitor] Callback triggered.');
  }

  build() {
    Column() {
      Text(`Value: ${this.value}`)
      Button('Increase value')
        .onClick(() => {
          this.value++;
        })
    }
  }
}
```

## IMonitorDecoratedVariable

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### 属性

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| path | string[] | 是 | 否 | 获取所有被监听的状态变量的路径。|

**示例：**

```typescript
'use static'

import { UIUtils, IMonitorDecoratedVariable, IMonitor, Entry, ComponentV2, Local, Column, Text, Button } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Page {
  @Local array: number[] = [0, 1, 2];
  monitor?: IMonitorDecoratedVariable;

  aboutToAppear() {
    const valueCallback = this.array.map((_: number, index: number): (() => Any) => (
      () => this.array[Double.toInt(index)]
    ));
    this.monitor = UIUtils.addMonitor(valueCallback, this.onChange);
  }

  onChange(mon: IMonitor) {
    console.info('[DynamicMonitor] Callback triggered.');
  }

  build() {
    Column() {
      Text(`Array: ${this.array}`)
      Button('Increase value')
        .onClick(() => {
          this.array.forEach((value: number, index: number) => {
            this.array[Double.toInt(index)] = value + 1;
          });
        })
      Button('Show paths')
        .onClick(() => {
          // 输出所有被监听状态变量的路径
          console.info(`[DynamicMonitor] [${this.monitor?.path.join(", ")}]`);
        })
    }
  }
}
```

## IVariableOwner

定义一个提供变量相关功能的自定义组件API。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```typescript
'use static'

import { IMonitor, IMonitorDecoratedVariable, UIUtils, Local, Entry, ComponentV2, Column, Text, Button } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Page {
  @Local value: number = 0;
  monitor?: IMonitorDecoratedVariable;

  aboutToAppear() {
    // 注册监听关系
    // 传递类型为IVariableOwner的owner
    this.monitor = UIUtils.addMonitor(() => this.value, this.onChange, { owner: this });
  }

  onChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`[DynamicMonitor] Value has changed from ${monitor.value<number>(path)?.before} to ${monitor.value<number>(path)?.now}.`);
    });
  }

  build() {
    Column() {
      Text(`Current value: ${this.value}`)

      // 值修改时触发回调函数
      Button('Increase value')
        .onClick(() => {
          this.value++;
        })
    }
  }
}
```
