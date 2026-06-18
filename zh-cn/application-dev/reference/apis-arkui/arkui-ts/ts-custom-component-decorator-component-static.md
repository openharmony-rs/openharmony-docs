# @Component：自定义组件

\@Component装饰器能装饰struct关键字声明的数据结构。struct被\@Component装饰后具备组件化的能力，需要实现build方法描述UI，一个struct只能被一个\@Component装饰。开发指南参考：[\@Component装饰器: 自定义组件](../../../ui/state-management-static/arkts-static-create-component.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Sta。
>
> - 本装饰器首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## @Component

@interface Component

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：**

| 名称   | 类型   | 只读 | 可选 | 说明                                                           |
| ------ | ------ | ---- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| reusePool | [ReusePoolOwnership](#reusepoolownership) | 否 | 是 | 全局复用池的持有模式。未提供reusePool参数时，全局复用功能不生效。<br/>**ArkTS-Sta起始版本：** 26.0.0|
| poolAccepts | string[] | 否 | 是 | 全局复用池接纳的组件名称列表。如果配置了reusePool，那么poolAccepts必须为非空数组，否则会编译报错。如果reusePool和poolAccepts同时未配置，则全局复用功能不生效。 <br/>**ArkTS-Sta起始版本：** 26.0.0|

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

## ReusePoolOwnership

定义全局复用的持有模式。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 26.0.0

| 名称        | 值   | 说明                                       |
| ----------- | ---- | ------------------------------------------------------------ |
| SHARED       | 'shared'      | 拥有@Component/@ComponentV2类的所有实例共享单个复用池实例。 |
| PER_INSTANCE | 'perInstance' | 拥有@Component/@ComponentV2的每个实例都有自己的复用池实例。复用池的生命周期与其拥有组件实例的生命周期相同。当拥有组件被销毁时，其复用池和其中的所有回收组件也被销毁。 |
| OFF          | 'off'         | 全局复用池功能不生效。该枚举值为@Component和@ComponentV2的reusePool参数的默认值。|