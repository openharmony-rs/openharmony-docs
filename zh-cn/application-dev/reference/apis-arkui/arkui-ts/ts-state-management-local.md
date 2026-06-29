# @Local：组件内部状态

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@Local用于状态管理V2中，表示组件内部的状态，使得自定义组件内部的变量具有观测能力。

在ArkTS-Dyn中使用时，开发指南参考：[@Local装饰器：组件内部状态（ArkTS-Dyn）](../../../ui/state-management/arkts-new-local.md)。

> **说明：**
>
> 从API version 12开始，支持该装饰器。

## @Local

const Local: PropertyDecorator

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Entry
@ComponentV2
struct LocalExample {
  @Local count: number = 0; // 定义一个Local变量
  build() {
    Column() {
      Text(`${this.count}`)
    }
  }
}
```

