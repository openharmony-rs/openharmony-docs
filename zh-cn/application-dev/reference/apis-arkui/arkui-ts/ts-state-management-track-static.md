# @Track

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 20开始，支持该装饰器。

@Track用于状态管理V1中，观测class对象的属性级更新。

在ArkTS-Sta中使用时，开发指南参考：[@Track装饰器：class对象属性级更新（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-track.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { State, Track } from '@ohos.arkui.stateManagement';

class Info {
  @Track id: number;

  constructor(id: number) {
    this.id = id;
  }
}

@Entry
@Component
struct Index {
  @State info: Info = new Info(1);

  build() {
    Column() {
      Text(`id: ${this.info.id}`)
      Button('change')
        .onClick((e: ClickEvent) => {
          this.info.id++;
        })
    }
  }
}
```