# ArkUI子系统变更说明

## cl.arkui.1 LayoutPolicy.matchParent父组件为Row、Column、Flex组件时，单方向设置matchParent的子组件布局行为变更

**访问级别**

公共能力

**变更原因**

当前Row、Column、Flex组件布局过程中，单方向设置matchParent的子组件不会参与父组件的尺寸计算。变更后，Row、Column、Flex组件会自适应单方向matchParent子组件尺寸，布局效果更符合API语义。

**变更影响**

此变更涉及应用适配。

变更前：当Row、Column、Flex组件主轴尺寸自适应子组件，且子组件A仅交叉轴设置matchParent时，子组件A不参与Row、Column、Flex组件的主轴尺寸测量过程，此时Row、Column、Flex组件主轴方向不自适应子组件A的尺寸。交叉轴方向同理。

变更后：当Row、Column、Flex组件主轴尺寸自适应子组件，且子组件A仅交叉轴设置matchParent时，子组件A会参与Row、Column、Flex组件的主轴尺寸测量过程，此时Row、Column、Flex组件主轴方向会自适应子组件A的尺寸。交叉轴方向同理。

例如：运行以下示例，进入页面后观察父组件Column的大小。变更前Column组件只会被第一个子组件撑大，变更后，Column组件高度自适应第一个和第二个子组件，宽度自适应第一个和第三个子组件。

```ts
@Entry
@Component
struct Demo {
  build() {
    Column() {
      Column({space: "30px"}) {
        Column()
          .width("200px")
          .height("200px")
          .backgroundColor('rgb(0, 74, 175)')

        Column()
          .width(LayoutPolicy.matchParent)
          .height("200px")
          .backgroundColor('rgb(0, 74, 175)')

        Column()
          .width("400px")
          .height(LayoutPolicy.matchParent)
          .backgroundColor('rgb(0, 74, 175)')
      }
      .width(LayoutPolicy.wrapContent)
      .height(LayoutPolicy.wrapContent)
      .backgroundColor('rgb(39, 135, 217)')
      .padding("30px")
    }.width("100%")
  }
}
```

变更前后效果如下：

|变更前|变更后|
|--|--|
|![](figures/singleMatchParentBefore.png)|![](figures/singleMatchParentAfter.png)|

**起始 API Level**

15

**变更发生版本**

从 OpenHarmony SDK 7.0.0.21 开始。

**变更的接口/组件**

涉及组件：[Row](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-row.md)、[Column](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-column.md)、[Flex](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-flex.md)。

涉及接口：[LayoutPolicy.matchParent](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#layoutpolicy15)。

**适配指导**

默认行为变更，但开发者需审视此变更是否对自身相关业务代码逻辑产生影响，若有影响需根据自身业务代码进行适配。如果开发者要用原先的布局效果，可以根据未设置matchParent的子组件手动设置父组件尺寸。
