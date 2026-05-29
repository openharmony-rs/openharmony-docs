# @ComponentV2：自定义组件V2

@ComponentV2主要配合状态管理V2使用。除非特别说明，@ComponentV2装饰的自定义组件将与[\@Component](../../../ui/state-management-static/arkts-static-create-component.md)装饰的自定义组件保持相同的行为。开发指南参考：[\@ComponentV2装饰器：自定义组件](../../../ui/state-management-static/arkts-static-componentv2.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Sta。
>
> - 本装饰器首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## @ComponentV2

@interface ComponentV2

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 名称   | 类型   | 只读 | 可选 | 说明                                                           |
| ------ | ------ | ---- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| reusePool | [ReusePoolOwnership](./ts-custom-component-decorator-component-static.md#reusepoolownership) | 否 | 是 | 全局复用池的持有模式。未提供reusePool参数时，全局复用功能不生效。<br/>**ArkTS-Sta起始版本：** 26.0.0|
| poolAccepts | string[] | 否 | 是 | 全局复用池接纳的组件名称列表。如果配置了reusePool，那么poolAccepts必须为非空数组，否则会编译报错。如果reusePool和poolAccepts同时未配置，则全局复用功能不生效。 <br/>**ArkTS-Sta起始版本：** 26.0.0|


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
