# 反色逃生
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @demon_coffee-->
<!--Tester: @demon_coffee-->
<!--Adviser: @HelloCrease-->

设置组件是否使能反色能力，开发者通过主动设置不使能反色算法，维持深浅色切换时的原有逻辑。

## allowForceDark

>  **说明：**
>
> 从API version 21开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

allowForceDark(value: boolean): T

设置组件是否使能反色能力。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型      | 必填 | 说明                       |
| ------ | -------- | -----|---------------------- |
| value  | boolean   |  是  | 是否使能反色能力。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

> **说明：**
>
> 当本节点主动设置不使能反色能力时，本节点及其所有子节点均不使能反色能力，不受父节点或祖先节点主动设置使能反色能力的影响。

**示例:**
```ts
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Column() {
        Text("Hello World")
          .fontSize(20)
          .fontColor(Color.Blue)
          .onClick(() => {
            console.info(`Text is clicked`);
          })
      }
      .allowForceDark(false) // Column组件及其子组件(Text组件)不生效反色能力，不受父组件(Column)使能反色能力的影响

      Row() {
        Button('TEST BUTTON')
          .backgroundColor(Color.Grey)
          .allowForceDark(true)
          .onClick(() => {
            console.info(`Button is clicked`);
          })
      }
      .allowForceDark(false) // Row组件及其子组件(Button组件)不生效反色能力，不受父组件(Column)使能反色能力的影响
    }
    .allowForceDark(true)
    .width('100%')
    .height('100%')
  }
}
```