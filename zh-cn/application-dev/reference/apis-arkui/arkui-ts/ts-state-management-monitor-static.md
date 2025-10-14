# @Monitor

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 20开始，支持该装饰器。

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

