# @Styles：组件重用样式

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @VictorS67-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

\@Styles装饰器用于将多条样式设置提炼为一个方法，在组件声明处直接调用，实现自定义样式的定义与复用。适用于多个组件需要共享相同样式、减少重复代码、提升样式一致性维护效率的场景。

在ArkTS-Dyn中使用时，开发指南参考：[\@Styles装饰器：定义组件重用样式](../../../ui/state-management/arkts-style.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Dyn。
>
> - 本装饰器首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## @Styles

const Styles: MethodDecorator

**卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Entry
@Component
struct FancyUse {
  @State heightValue: number = 50;

  // 使用@Styles装饰器定义可复用的样式方法
  @Styles
  fancy() {
    .height(this.heightValue)
    .backgroundColor(Color.Blue)
    .onClick(() => {
      this.heightValue = 100;
    })
  }

  build() {
    Column() {
      Button('change height')
        // 调用@Styles定义的fancy样式方法，应用复用样式
        .fancy()
    }
    .height('100%')
    .width('100%')
  }
}
```