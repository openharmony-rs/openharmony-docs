# @Param

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 20开始，支持该装饰器。

@Param用于状态管理V2中，接收外部输入，实现父子组件之前的单向数据同步。

在ArkTS-Sta中使用时，开发指南参考：[@Param：组件外部输入（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-new-param.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { Entry, ComponentV2, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { Local, Param } from '@ohos.arkui.stateManagement';

@ComponentV2
struct Child {
  @Param message: string = '';
  build() {
    Column() {
      Text(`Child message: ${this.message}`)
    }
  }
}
@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello';
  build() {
    Column() {
      Text(`Parent message: ${this.message}`)
      Button('change message')
        .onClick((e: ClickEvent) => {
          this.message = 'Hello World';
        })
      Child({ message: this.message })
    }
  }
}
```

