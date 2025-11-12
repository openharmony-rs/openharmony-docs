# @Event

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 20开始，支持该装饰器。

@Event装饰回调方法，用于状态管理V2中，作为自定义组件的输出。

在ArkTS-Sta中使用时，开发指南参考：[@Event：规范组件输出（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-new-event.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { Entry, ComponentV2, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { Local, Param, Event } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
struct Index {
  @Local name: string = 'Tom';

  build() {
    Column() {
      Child({
        name: this.name,
        changeFactory: (type: number) => {
          if (type == 1) {
            this.name = 'Tom';
          } else if (type == 2) {
            this.name = 'Jerry';
          }
        }
      })
    }
  }
}

@ComponentV2
struct Child {
  @Param name: string = '';
  @Event changeFactory: (x: number) => void = (x: number) => {};

  build() {
    Column() {
      Text(`name: ${this.name}`)
      Button('change to Tom')
        .onClick((e: ClickEvent) => {
          this.changeFactory(1);
        })
      Button('change to Jerry')
        .onClick((e: ClickEvent) => {
          this.changeFactory(2);
        })
    }
  }
}
```

