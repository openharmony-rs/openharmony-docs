# @Component：自定义组件

\@Component装饰器能装饰struct关键字声明的数据结构。struct被\@Component装饰后具备组件化的能力，需要实现build方法描述UI，一个struct只能被一个\@Component装饰。开发指南参考：[\@Component装饰器: 自定义组件](../../../ui/state-management-static/arkts-static-create-component.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Sta。
>
> - 本装饰器首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

ArkTS-Sta示例：

```ts
'use static'
import { Entry, Component, Column, Text } from '@kit.ArkUI';

@Entry
@Component
struct MyComponent {
  build() {
    Column() {
      Text('Hello World!')
    }
  }
}
```