# @LocalBuilder装饰器：维持组件关系

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

`@LocalBuilder`拥有和局部[`@Builder`](./ts-universal-builder-dynamic.md#@Builder)相同的功能，且比局部`@Builder`能够更好地确定组件的父子关系和状态管理的父子关系。适用于需要在自定义构建函数中保持组件父子关系和状态管理同步的场景。开发指南见[`@LocalBuilder` 装饰器：维持组件关系](../../../ui/state-management/arkts-localBuilder.md)。

> **说明：**
>
> - 本装饰器首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## @LocalBuilder

const LocalBuilder: MethodDecorator

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
class ReferenceType {
  paramString: string = '';
}

@Entry
@Component
struct Parent {
  @State variableValue: string = 'Hello World';

  // 使用@LocalBuilder装饰器定义构建函数，维持组件的父子关系和状态管理的父子关系
  // 通过引用类型参数传递，可以监听到状态变量的变化
  @LocalBuilder
  citeLocalBuilder(params: ReferenceType) {
    Row() {
      Text(`UseStateVarByReference: ${params.paramString}`)
    }
  }

  build() {
    Column() {
      // 调用@LocalBuilder定义的构建函数，传入包含状态变量的引用类型参数
      this.citeLocalBuilder({ paramString: this.variableValue })
      Button('Click me')
        .onClick(() => {
          // 点击后修改状态变量的值，UI会自动刷新
          this.variableValue = 'Hi World';
        })
    }
  }
}
```
