# @Trace

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 20开始，支持该装饰器。

@Trace是属性装饰器，用于状态管理V2中。@ObservedV2与@Trace配套使用，装饰类以及类中的属性，使得被装饰的类和属性具有深度观测的能力。

在ArkTS-Sta中使用时，开发指南参考：[\@ObservedV2装饰器和\@Trace装饰器：类属性变化观测（ArkTS-Sta）](../../../ui/state-management-static/arkts-static-new-observedV2-and-trace.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { Entry, ComponentV2, Column, Text, ClickEvent } from '@ohos.arkui.component';
import { ObservedV2, Trace } from '@ohos.arkui.stateManagement';

@ObservedV2
class Son {
  @Trace age: number = 100;
}
class Father {
  son: Son = new Son();
}
@Entry
@ComponentV2
struct Index {
  father: Father = new Father();

  build() {
    Column() {
      Text(`${this.father.son.age}`)
        .onClick((e: ClickEvent) => {
          this.father.son.age++;
        })
    }
  }
}
```

