# @Computed：计算属性

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@Computed为方法装饰器，用于状态管理V2中，装饰getter方法。

在ArkTS-Dyn中使用时，开发指南参考：[@Computed装饰器：计算属性（ArkTS-Dyn）](../../../ui/state-management/arkts-new-computed.md)。

> **说明：**
>
> 从API version 12开始，支持该装饰器。

## @Computed

const Computed: MethodDecorator

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Entry
@ComponentV2
  struct Index {
  @Local firstName: string = 'Hua';
  @Local lastName: string = 'Li';

  // 声明Computed getter函数，避免重复计算
  @Computed
  get fullName() {
    return this.firstName + ' ' + this.lastName;
  }

  build() {
    Column() {
      Text(`${this.fullName}`)
    }
  }
}
```

