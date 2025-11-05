# @Once

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 20开始，支持该装饰器。

@Once作为辅助装饰器，用于状态管理V2中，需要搭配@Param一起使用，适用于仅从外部初始化一次且不接受后续同步变化的场景。

在ArkTS-Sta中使用时，开发指南参考：[@Once：初始化同步一次（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-new-once.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { Entry, ComponentV2, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { Local, Param, Once } from '@ohos.arkui.stateManagement';

@ComponentV2
struct Child {
  @Param @Once onceParam: string = '';
  build() {
    Column() {
      Text(`onceParam: ${this.onceParam}`)
      Button('change onceParam')
        .onClick((e: ClickEvent) => {
          this.onceParam = 'child';
        })
    }
  }
}
@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello World';
  build() {
    Column() {
      Text(`Parent message: ${this.message}`)
      Button('change message')
        .onClick((e: ClickEvent) => {
          this.message = 'parent';
        })
      Child({ onceParam: this.message })
    }
  }
}
```

