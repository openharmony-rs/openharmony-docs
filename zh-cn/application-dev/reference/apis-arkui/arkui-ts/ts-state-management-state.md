# @State：组件内状态

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@State用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，将自定义组件内的普通变量转变为状态变量，当状态变量变化时，触发组件内UI重新渲染。适用于需要在组件内管理可变状态的场景。

在ArkTS-Dyn中使用时，开发指南参考：[@State装饰器：组件内状态（ArkTS-Dyn）](../../../ui/state-management/arkts-state.md)。

> **说明：**
>
> 从API version 7开始，支持该装饰器。

## @State

const State: PropertyDecorator

**卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Entry
@Component
struct StateExample {
  @State count: number = 0; // 状态变量

  build() {
    Column() {
      Text(`${this.count}`)
    }
  }
}
```
