# @Observed

> **说明：**
>
> 从API version 20开始，支持该装饰器。

@Observed是类装饰器，用于状态管理V1中，观察对象类属性变化。

在静态语言上下文中使用时，开发指南参考：[\@Observed装饰器和\@ObjectLink装饰器：嵌套类对象属性变化（ArkTS-ST）](../../../ui/state-management-static/arkts-static-observed-and-objectlink.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
import { Entry, Component, Column, Text } from '@ohos.arkui.component';
import { State, Observed } from '@ohos.arkui.stateManagement';

@Observed
class Info {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}

@Entry
@Component
struct Index {
  @State info: Info = new Info('Tom');
  build() {
    Column() {
      Text(`name: ${this.info.name}`)
    }
  }
}
```

