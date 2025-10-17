# 反色逃生
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @demon_coffee-->
<!--Tester: @demon_coffee-->
<!--Adviser: @HelloCrease-->

设置组件是否使用反色能力，开发者通过主动设置不使用反色算法，维持深浅色切换时的原有逻辑。

>  **说明：**
>
> 本模块首批接口从API version 21开始支持。后续版本的新增接口，采用上角标单独标记该接口的起始版本。

## allowForceDark

allowForceDark(value: boolean): T

设置组件是否使用反色能力。

**原子化服务API：** 从API version 21开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型      | 必填 | 说明                       |
| ------ | -------- | -----|---------------------- |
| value  | boolean   |  是  | 是否使用反色能力。true表示使用反色能力，false表示不使用反色能力。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

> **说明：**
>
> 当本节点主动设置不使用反色能力时，本节点及其所有子节点均不使用反色能力，不受父节点或祖先节点主动设置使用反色能力的影响。

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
      .allowForceDark(false) // Column组件及其子组件(Text组件)不生效反色能力，不受父组件(Column)使用反色能力的影响

      Row() {
        Button('TEST BUTTON')
          .backgroundColor(Color.Grey)
          .allowForceDark(true)
          .onClick(() => {
            console.info(`Button is clicked`);
          })
      }
      .allowForceDark(false) // Row组件及其子组件(Button组件)不生效反色能力，不受父组件(Column)使用反色能力的影响
    }
    .allowForceDark(true)
    .width('100%')
    .height('100%')
  }
}
```