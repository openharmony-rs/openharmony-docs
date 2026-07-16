# \@Builder装饰器：自定义构建函数

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

\@Builder装饰的函数也称为“自定义构建函数”，用于封装可复用的UI构建逻辑，可在自定义组件中多次调用。开发指南见[@Builder装饰器：自定义构建函数](../../../ui/state-management/arkts-builder.md)。

> **说明：**
>
> - 该装饰器从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## @Builder

const Builder: MethodDecorator

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**示例：**

```ts
@Entry
@Component
struct BuilderDemo {
  // @Builder装饰此函数，使其成为自定义构建函数，用于配置并构建Text组件
  @Builder
  showTextBuilder() {
    Text('Hello World')
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }

  @Builder
  showTextValueBuilder(param: string) {
    Text(param)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }

  build() {
    Column() {
      // 无参数
      this.showTextBuilder()
      // 有参数
      this.showTextValueBuilder('Hello @Builder')
    }
  }
}
```
