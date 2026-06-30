# @SyncMonitor

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @zhangboren-->
<!--TSE: @TerryTsao-->

@SyncMonitor用于状态管理V2中，同步监听状态变量修改，使得状态变量具有深度监听的能力。开发指南见：[\@SyncMonitor装饰器：状态变量修改同步监听](../../../ui/state-management-static/arkts-static-new-syncmonitor.md)。

> **说明：**
>
> 本模块仅适用于ArkTS-Sta。
>
> 该装饰器从API版本26.0.0开始支持。

## @SyncMonitor

@interface SyncMonitor

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型     | 必填 | 说明                                                                                     |
| ------ | -------- | ---- | ---------------------------------------------------------------------------------------- |
| path   | string[] | 是   | 字符串类型的对象属性名称。可同时监听多个对象属性，例如：@SyncMonitor(['prop1', 'prop2'])。 |

**示例：**

```ts
'use static'

import { Entry, ComponentV2, Local, SyncMonitor, IMonitor, Column, Button } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello World';
  @Local name: string = 'Tom';
  // 使用@SyncMonitor同时监听message和name的变化
  @SyncMonitor(['message', 'name'])
  onStrChange(monitor: IMonitor) {
    monitor.dirty.forEach((path: string) => {
      console.info(`${path} changed from ${monitor.value<string>(path)?.before} to ${monitor.value<string>(path)?.now}`);
    });
  }
  build() {
    Column() {
      Button('change string')
        .onClick(() => {
          this.message += '!'; // 修改message，同步触发onStrChange回调
          this.name = 'Jack'; // 修改name，同步触发onStrChange回调
        })
    }
  }
}
```