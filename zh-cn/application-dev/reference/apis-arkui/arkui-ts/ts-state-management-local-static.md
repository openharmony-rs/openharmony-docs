# @Local

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 20开始，支持该装饰器。

@Local用于状态管理V2中，表示组件内部的状态，使得自定义组件内部的变量具有观测能力。

在ArkTS-Sta中使用时，开发指南参考：[@Local装饰器：组件内部状态（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-new-local.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { Local } from '@ohos.arkui.stateManagement';
import { Entry, ComponentV2, Column, Text } from '@ohos.arkui.component';

@Entry
@ComponentV2
struct LocalExample {
  @Local count: number = 0;
  build() {
    Column() {
      Text(`${this.count}`)
    }
  }
}
```

