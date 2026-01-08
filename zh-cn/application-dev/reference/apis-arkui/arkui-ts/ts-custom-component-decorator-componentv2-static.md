# @ComponentV2：自定义组件V2

@ComponentV2主要配合状态管理V2使用。除非特别说明，@ComponentV2装饰的自定义组件将与@Component装饰的自定义组件保持相同的行为。开发指南参考：[\@ComponentV2装饰器：自定义组件](../../../ui/state-management-static/arkts-static-componentv2.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Sta。
>
> - 本装饰器首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'
import { Entry, ComponentV2, Column, Text } from '@kit.ArkUI';

@Entry
@ComponentV2
struct MyComponent {
  build() {
    Column() {
      Text('Hello World!')
    }
  }
}
```
