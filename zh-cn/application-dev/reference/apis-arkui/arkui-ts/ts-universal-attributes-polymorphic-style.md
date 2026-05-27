# 多态样式
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

设置组件不同状态下的样式。

>  **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 从API version 11开始支持另一种写法[attributeModifier](./ts-universal-attributes-attribute-modifier.md#attributemodifier)，可根据开发者需要动态设置属性。
>
> - 多态样式仅支持[通用属性](ts-component-general-attributes.md)。如果多态样式不生效，则该属性可能为组件的私有属性，例如：fontColor、[TextInput](./ts-basic-components-textinput.md)组件的[backgroundColor](./ts-universal-attributes-background.md#backgroundcolor18)等。此时，可以通过attributeModifier动态设置组件属性来解决此问题。
>
> - 当前多态样式实现依赖于组件自定义节点的刷新机制。因Builder不具备独立的自定义父节点，无法直接触发刷新，致使多态样式无法直接在Builder中生效。解决方法是将多态样式封装至自定义组件内部，再将此组件置于@Builder中，以此来间接实现多态样式。示例代码可参考[示例3（设置Builder多态样式）](#示例3设置builder多态样式)。
>  
> - 多态样式的焦点态只有在[焦点激活态](../../../ui/arkts-common-events-focus-event.md#基础概念)开启时生效。
>
> - 如果组件同时处于多种状态，并且分别在各自的状态里设置了一样的属性，那么最终样式生效的优先级为悬浮态&lt;按压态&lt;获焦态&lt;禁用态&lt;选中态。例如，如果组件同时处于悬浮态和按压态，在悬浮态和按压态都设置了背景色，那么此时组件最终显示按压态的背景色。

## stateStyles

ArkTS-Dyn: stateStyles(value: StateStyles): T

ArkTS-Sta: stateStyles(value: StateStyles | undefined): this

设置组件不同状态的样式。

> **说明：**
>
> 该接口不支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                | 必填 | 说明                     |
| ------ | ----------------------------------- | ---- | ------------------------ |
| value  | ArkTS-Dyn: [StateStyles](#statestyles-1)<br/> ArkTS-Sta: [StateStyles](#statestyles-1) \| undefined | 是   | 设置组件不同状态的样式。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: T<br/>ArkTS-Sta: this | 返回当前组件。 |


## CustomStyles<sup>23+</sup>

type CustomStyles = (instance: CommonMethod) => void

定义用于多态样式的回调类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                | 必填 | 说明                     |
| ------ | ----------------------------------- | ---- | ------------------------ |
| instance  | CommonMethod | 是   | 提供组件的实例。 |


## StateStyles

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| normal | ArkTS-Dyn: any <br/> ArkTS-Sta: [CustomStyles](#customstyles23) | 否 | 是 | 组件无状态时的样式。<br/>**卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该参数支持在ArkTS卡片中使用。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该参数支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| pressed | ArkTS-Dyn: any <br/> ArkTS-Sta: [CustomStyles](#customstyles23) | 否 | 是 | 组件按下状态的样式。<br/>**卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该参数支持在ArkTS卡片中使用。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该参数支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| disabled | ArkTS-Dyn: any <br/> ArkTS-Sta: [CustomStyles](#customstyles23) | 否 | 是 | 组件禁用状态的样式。<br/>**卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该参数支持在ArkTS卡片中使用。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该参数支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| focused | ArkTS-Dyn: any <br/> ArkTS-Sta: [CustomStyles](#customstyles23) | 否 | 是 | 组件获焦状态的样式。<br/>**卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该参数支持在ArkTS卡片中使用。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该参数支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| clicked | ArkTS-Dyn: any <br/> ArkTS-Sta: [CustomStyles](#customstyles23) | 否 | 是 | 组件点击状态的样式。<br/>**卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该参数支持在ArkTS卡片中使用。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该参数支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| selected<sup>10+</sup> | ArkTS-Dyn: object <br/> ArkTS-Sta: [CustomStyles](#customstyles23) | 否 | 是 | 组件选中状态的样式。<br/>**卡片能力（仅ArkTS-Dyn）：** 从API version 10开始，该参数支持在ArkTS卡片中使用。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该参数支持在原子化服务中使用。<br/>**模型约束：** 此接口仅可在Stage模型下使用。<br/>**ArkTS-Dyn起始版本：** 10<br/>**ArkTS-Sta起始版本：** 23 |
| hovered | ArkTS-Dyn: object <br/> ArkTS-Sta: [CustomStyles](#customstyles23) | 否 | 是 | 组件悬浮状态的样式。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 26开始，该参数支持在原子化服务中使用。<br/>**模型约束：** 此接口仅可在Stage模型下使用。<br/>**ArkTS-Dyn起始版本：** 26.0.0 <br/>**ArkTS-Sta起始版本：** 26.0.0 |

**selected选中状态说明**

- 当前多态样式的选中状态样式依赖组件选中属性值，可以使用[点击事件](ts-universal-events-click.md)修改属性值，或使用属性自带[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定功能。

- 当前支持selected的组件及其参数/属性值：

  | 组件                                                         | 支持的参数/属性 | 起始API版本 |
  | ------------------------------------------------------------ | --------------- | ----------- |
  | [Checkbox](ts-basic-components-checkbox.md) | select          | 10          |
  | [CheckboxGroup](ts-basic-components-checkboxgroup.md) | selectAll       | 10          |
  | [Radio](ts-basic-components-radio.md)  | checked         | 10          |
  | [Toggle](ts-basic-components-toggle.md) | isOn            | 10          |
  | [ListItem](ts-container-listitem.md) | selected         | 10          |
  | [GridItem](ts-container-griditem.md) | selected         | 10          |
  | [MenuItem](ts-basic-components-menuitem.md) | selected         | 10          |

**pressed和clicked状态说明**

- 当clicked和pressed同时在一个组件上使用时，只有后注册的状态才能生效。

## 示例

### 示例1（设置Text多态样式）

该示例展示了[stateStyles](#statestyles)设置状态为hovered、pressed和disabled时Text组件的样式变化。

从API版本26.0.0开始，[stateStyles](#statestyles)新增hovered属性。

```ts
// xxx.ets
@Entry
@Component
struct StyleExample {
  @State isEnable: boolean = true

  @Styles
  hoveredStyles(): void {
    .backgroundColor('#12db70')
    .borderRadius(10)
    .borderStyle(BorderStyle.Dashed)
    .borderWidth(2)
    .borderColor('#33000000')
    .width(120)
    .height(30)
    .opacity(1)
  }

  @Styles
  pressedStyles(): void {
    .backgroundColor('#ED6F21')
    .borderRadius(10)
    .borderStyle(BorderStyle.Dashed)
    .borderWidth(2)
    .borderColor('#33000000')
    .width(120)
    .height(30)
    .opacity(1)
  }

  @Styles
  disabledStyles(): void {
    .backgroundColor('#E5E5E5')
    .borderRadius(10)
    .borderStyle(BorderStyle.Solid)
    .borderWidth(2)
    .borderColor('#2a4c1919')
    .width(90)
    .height(25)
    .opacity(1)
  }

  @Styles
  normalStyles(): void {
    .backgroundColor('#0A59F7')
    .borderRadius(10)
    .borderStyle(BorderStyle.Solid)
    .borderWidth(2)
    .borderColor('#33000000')
    .width(100)
    .height(25)
    .opacity(1)
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center }) {
      Text("normal")
        .fontSize(14)
        .fontColor(Color.White)
        .opacity(0.5)
        // stateStyles设置组件无状态时的样式
        .stateStyles({
          normal: this.normalStyles,
        })
        .margin({ bottom: 20 })
        .textAlign(TextAlign.Center)
      Text('hovered')
        .backgroundColor('#0A59F7')
        .borderRadius(20)
        .borderStyle(BorderStyle.Dotted)
        .borderWidth(2)
        .borderColor(Color.Red)
        .width(100)
        .height(25)
        .opacity(1)
        .fontSize(14)
        .fontColor(Color.White)
        // stateStyles设置组件鼠标悬浮状态时的样式
        .stateStyles({
          hovered: this.hoveredStyles,
        })
        .margin({ bottom: 20 })
        .textAlign(TextAlign.Center)
      Text('pressed')
        .backgroundColor('#0A59F7')
        .borderRadius(20)
        .borderStyle(BorderStyle.Dotted)
        .borderWidth(2)
        .borderColor(Color.Red)
        .width(100)
        .height(25)
        .opacity(1)
        .fontSize(14)
        .fontColor(Color.White)
        // stateStyles设置组件按下状态时的样式
        .stateStyles({
          pressed: this.pressedStyles,
        })
        .margin({ bottom: 20 })
        .textAlign(TextAlign.Center)
      Text(this.isEnable == true ? 'effective' : 'disabled')
        .backgroundColor('#0A59F7')
        .borderRadius(20)
        .borderStyle(BorderStyle.Solid)
        .borderWidth(2)
        .borderColor(Color.Gray)
        .width(100)
        .height(25)
        .opacity(1)
        .fontSize(14)
        .fontColor(Color.White)
        .enabled(this.isEnable)
        // stateStyles设置组件禁用状态时的样式
        .stateStyles({
          disabled: this.disabledStyles,
        })
        .textAlign(TextAlign.Center)
      Text('control disabled')
        .onClick(() => {
          this.isEnable = !this.isEnable
          console.info(`${this.isEnable}`)
        })
    }
    .width(350).height(300)
  }
}
```

![zh-cn_image_0000001188742468](figures/zh-cn_image_0000001188742468.gif)

### 示例2（设置Radio多态样式）

该示例展示了状态为selected时Radio组件的样式变化。

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State value: boolean = false
  @State value2: boolean = false

  @Styles
  normalStyles(): void{
    .backgroundColor("#E5E5E1")
  }

  @Styles
  selectStyles(): void{
    .backgroundColor("#ED6F21")
    .borderWidth(2)
  }

  build() {
    Flex({ direction: FlexDirection.Row, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Column() {
        Text('Radio1')
          .fontSize(25)
        Radio({ value: 'Radio1', group: 'radioGroup1' })
          .checked(this.value)
          .height(50)
          .width(50)
          .borderWidth(0)
          .borderRadius(30)
          .onClick(() => {
            this.value = !this.value
          })
          .stateStyles({
            normal: this.normalStyles,
            selected: this.selectStyles,
          })
      }
      .margin(30)

      Column() {
        Text('Radio2')
          .fontSize(25)
        Radio({ value: 'Radio2', group: 'radioGroup2' })
          .checked($$this.value2)
          .height(50)
          .width(50)
          .borderWidth(0)
          .borderRadius(30)
          .stateStyles({
            normal: this.normalStyles,
            selected: this.selectStyles,
          })
      }
      .margin(30)
    }.padding({ top: 30 })
  }
}
```

![selected](figures/selected.gif)

### 示例3（设置Builder多态样式）

该示例展示了状态为pressed时Builder组件的样式变化。

```ts
import { ComponentContent } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Component
struct Child {
  build() {
    Row()
      .zIndex(10)
      .width(200)
      .height(200)
      .stateStyles({
        normal: {
          .backgroundColor(Color.Blue)
        },
        pressed: {
          .backgroundColor(Color.Black)
        }
      })
  }
}

@Builder
function buildText() {
  Child()
}

@Entry
@Component
struct Index {
  private contentNode: ComponentContent<Object> =
    new ComponentContent(this.getUIContext(), wrapBuilder(buildText));

  build() {
    Column() {
      Button().margin({ top: 200 }).onClick((event: ClickEvent) => {
        this.getUIContext()
          .getPromptAction()
          .openCustomDialog(this.contentNode)
          .then(() => {
            console.info('OpenCustomDialog complete.')
          })
          .catch((error: BusinessError) => {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`OpenCustomDialog args error code is ${code}, message is ${message}`);
          })
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

![Builder](figures/stateStyles_builder.gif)