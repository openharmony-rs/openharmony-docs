# @Computed

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 23开始，支持该装饰器。

@Computed为方法装饰器，用于状态管理V2中，装饰getter方法。

在ArkTS-Sta中使用时，开发指南参考：[@Computed装饰器：计算属性（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-new-computed.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { Entry, ComponentV2, Column, Text } from '@ohos.arkui.component';
import { Local, Computed } from '@ohos.arkui.stateManagement';

@Entry
@ComponentV2
  struct Index {
  @Local firstName: string = 'Hua';
  @Local lastName: string = 'Li';

  @Computed
  get fullName(): string {
    return this.firstName + ' ' + this.lastName;
  }

  build() {
    Column() {
      Text(`${this.fullName}`)
    }
  }
}
```

