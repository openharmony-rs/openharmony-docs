# @StorageLink

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 23开始，支持该装饰器。

@StorageLink用于状态管理V1中，与AppStorage中对应的属性建立双向数据同步。

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
import { StorageLink } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct StorageLinkComponent {
  @StorageLink('LinkA') linkA: number = 1;

  build() {
    Column() {
      Text('@StorageLink接口初始化，@StorageLink取值')
      Button(`${this.linkA}`)
        .onClick((e: ClickEvent) => {
          this.linkA += 1;
      })
    }
  }
}
```

