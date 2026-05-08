# @Provide

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 23开始，支持该装饰器。

\@Provide和\@Consume配套使用，用于状态管理V1中，实现跨组件层级的双向同步。@Provide修饰数据源，对其所有后代组件可用。

在ArkTS-Sta中使用时，开发指南参考：[\@Provide装饰器和\@Consume装饰器：与后代组件双向同步（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-provide-and-consume.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名        | 类型    | 必填 | 说明                               |
| ------------- | ------- | ---- | ---------------------------------- |
| alias         | string  | 否   | 用于设置别名，默认值为属性名。                     |
| allowOverride | boolean | 否   | 用于设置是否允许重载，默认值为false即不允许。 |

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text } from '@ohos.arkui.component';
import { Provide, Consume } from '@ohos.arkui.stateManagement';

@Entry
@Component
struct Index {
  @Provide str: string = 'aaa';
  build() {
    Column() {
      Text(`provide: ${this.str}`)
      Child()
    }
  }
}

@Component
struct Child {
  @Consume str: string;
  build() {
    Column() {
      Text(`consume: ${this.str}`)
    }
  }
}
```

