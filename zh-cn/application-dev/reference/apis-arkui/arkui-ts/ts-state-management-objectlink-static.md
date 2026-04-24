# @ObjectLink

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 23开始，支持该装饰器。

@ObjectLink用于状态管理V1中，接收@Observed装饰的类的实例，并与父组件中的数据源建立双向数据绑定。

在ArkTS-Sta中使用时，开发指南参考：[\@Observed装饰器和\@ObjectLink装饰器：嵌套类对象属性变化（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-observed-and-objectlink.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text } from '@ohos.arkui.component';
import { State, Observed, ObjectLink } from '@ohos.arkui.stateManagement';

@Observed
class Info {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}

@Component
struct Child {
  @ObjectLink info: Info;
  build() {
    Column() {
      Text(`name: ${this.info.name}`)
    }
  }
}

@Entry
@Component
struct Index {
  @State info: Info = new Info('Tom');
  build() {
    Column() {
      Child({info: this.info})
    }
  }
}
```

