# @PropRef

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 20开始，支持该装饰器。
>

@PropRef用于状态管理V1中，接收外部传入值，并与父组件建立单向同步关系。

在ArkTS-Sta中使用时，开发指南参考：[@PropRef装饰器：父子单向同步（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-propref.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { State, PropRef } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct Index {
  @State count: number = 0;
  build() {
    Column() {
      Text(`State ${this.count}`)
      Button('change State')
        .onClick((e: ClickEvent) => {
          this.count++;
      })
      Child({ count: this.count })
    }
  }
}

@Component
struct Child {
  @PropRef count: number;
  build() {
    Column() {
      Text(`PropRef ${this.count}`)
      Button('change PropRef')
        .onClick((e: ClickEvent) => {
          this.count++;
        })
    }
  }
}
```

