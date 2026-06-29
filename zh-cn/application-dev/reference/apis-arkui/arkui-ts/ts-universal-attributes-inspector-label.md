# 节点调测标签
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

设置调测标签，帮助开发者分辨同类节点，提高开发和分析调试的效率。

**起始版本：** 26.0.0

## inspectorLabel

ArkTS-Dyn: inspectorLabel(label: string | undefined): T

ArkTS-Sta: inspectorLabel(label: string | undefined): this

设置组件的调测标签。未设置时，组件调测标签默认为空。如果同一个组件设置了多个调测标签，仅最后一次设置的生效。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名   | 类型      | 必填 | 说明                       |
| ------ | -------- | -----|---------------------- |
| label  | string \| undefined  |  是  | 组件的调测标签，请开发者保证标签的唯一性。如果传入undefined表示调测标签为空字符串。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: T<br/>ArkTS-Sta: this | 返回当前组件。 |

**示例：**
```ts
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Text('Hello World')
        .fontSize(20)
        .inspectorLabel('TEXT')
        .onClick(() => {
          console.info(`Text is clicked`);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```