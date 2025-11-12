# @StoragePropRef

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 20开始，支持该装饰器。

@StoragePropRef用于状态管理V1中，与AppStorage中对应的属性建立单向数据同步。

在ArkTS-Sta中使用时，开发指南参考：[AppStorage：应用全局的UI状态存储（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-appstorage.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型   | 必填 | 说明                       |
| -------- | ------ | ---- | -------------------------- |
| property | string | 是   | 用于标识AppStorage的属性。 |

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text, ClickEvent, Button } from '@ohos.arkui.component';
import { StoragePropRef } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct StoragePropRefComponent {
  @StoragePropRef('PropRefA') propRefA: number = 1;

  build() {
    Column() {
      Text('@StoragePropRef接口初始化，@StoragePropRef取值')
      Button(`${this.propRefA}`)
        .onClick((e: ClickEvent) => {
          this.propRefA += 1;
      })
    }
  }
}
```

