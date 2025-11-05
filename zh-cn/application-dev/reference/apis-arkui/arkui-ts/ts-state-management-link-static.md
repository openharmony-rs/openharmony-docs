# @Link

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 20开始，支持该装饰器。

@Link用于状态管理V1中，接收外部传入值，并与父组件中的数据源建立双向数据绑定。

在ArkTS-Sta中使用时，开发指南参考：[@Link装饰器：父子双向同步（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-link.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { State, Link } from '@ohos.arkui.stateManagement';

@Component
struct Child {
  @Link msg: string;

  build() {
    Column() {
      Text(this.msg)
      Button('change')
        .onClick((e: ClickEvent) => {
          this.msg += '~';
        })
    }
  }
}

@Entry
@Component
struct LinkExample {
  @State message: string = 'Hello';

  build() {
    Column() {
      Child({msg: this.message})
    }
  }
}
```

