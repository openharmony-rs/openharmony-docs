# @State

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 20开始，支持该装饰器。

@State用于状态管理V1中，将自定义组件内的普通变量转变为状态变量，管理组件内UI刷新。

在ArkTS-Sta中使用时，开发指南参考：[@State装饰器：组件内状态（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-state.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { State } from '@ohos.arkui.stateManagement';
import { Entry, Component, Column, Text } from '@ohos.arkui.component';

@Entry
@Component
struct StateExample {
  @State count: number = 0;
  build() {
    Column() {
      Text(`${this.count}`)
    }
  }
}
```