# @LocalStoragePropRef

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 23开始，支持该装饰器。

@LocalStoragePropRef用于状态管理V1中，与LocalStorage中给定属性建立单向同步关系。

在ArkTS-Sta中使用时，开发指南参考：[LocalStorage：页面级UI状态存储（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-localstorage.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型   | 必填 | 说明                         |
| -------- | ------ | ---- | ---------------------------- |
| property | string | 是   | 用于标识LocalStorage的属性。 |

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text, Button, ClickEvent } from '@ohos.arkui.component';
import { LocalStoragePropRef } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct Parent {
  @LocalStoragePropRef('PropRefA') propRefA: number = 1;

  build() {
    Column() {
      Button(`${this.propRefA}`)
        .onClick((e: ClickEvent) => {
          this.propRefA += 1;
        })
    }
  }
}
```

