# ExtendableButton (可扩展的Button)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[Button](./ts-basic-components-button.md)的扩展组件的基类。开发者可以自定义扩展组件继承ExtendableButton，支持重写Button中的[属性](./ts-basic-components-button.md#属性)和[通用属性](./ts-component-general-attributes.md)，同时支持自定义属性。在阅读本文档前，建议提前阅读[Button](./ts-basic-components-button.md)。开发指南请参考[内置组件扩展](../../../ui/state-management-static/arkts-static-extendable-inner-component.md)。

**起始版本：** 26.0.0

>  **说明：**
>
>  本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { ExtendableButton } from '@kit.ArkUI';
```

## 子组件

可以包含单个子组件。

## 属性

自定义的Button扩展组件类支持重写Button的[属性](./ts-basic-components-button.md#属性)和[通用属性](./ts-component-general-attributes.md)，若不重写，则遵循对应属性的默认行为。此外，扩展组件类支持以下属性和自定义属性。

### setButtonOptions

setButtonOptions(label: ResourceStr, options?: ButtonOptions): this

设置按钮配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名  | 类型                                    | 必填 | 说明                 |
| ------- | --------------------------------------- | ---- | -------------------- |
| label   | [ResourceStr](ts-types.md#resourcestr)  | 是   | 按钮文本内容。<br/>**说明：** 当文本字符的长度超过按钮本身的宽度时，文本将会被截断。 |
| options | [ButtonOptions](./ts-basic-components-button.md#buttonoptions对象说明) | 否   | 配置按钮的显示样式。<br/> 未设置时，则按照ButtonOptions中各参数的默认值配置。 |

### setButtonOptions

setButtonOptions(options?: ButtonOptions): this

设置按钮配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名  | 类型                                    | 必填 | 说明                 |
| ------- | --------------------------------------- | ---- | -------------------- |
| options | [ButtonOptions](./ts-basic-components-button.md#buttonoptions对象说明) | 否   | 配置按钮的显示样式。<br/> 未设置时，则按照ButtonOptions中各参数的默认值配置。 |

## 事件

支持[通用事件](ts-component-general-events.md)。

## 示例

```ts
'use static'

import { ExtendableButton, ButtonOptions, Length, Entry, Component, Column, ResourceStr, ButtonType, ControlSize, State, ClickEvent } from '@kit.ArkUI';

class MyButton extends ExtendableButton {
  // 通用属性
  width(): this {
    super.width('100%');
    return this;
  }

  height(): this {
    super.height('100%');
    return this;
  }

  // 自定义属性
  newAttribute(): this {
    super.height('50%');
    super.width('30%');
    return this;
  }
}

@Entry
@Component
struct Index {
  @State str: string = 'add';

  build() {
    Column() {
      // 调用扩展组件
      MyButton(this.str, { controlSize: ControlSize.SMALL } as ButtonOptions)
        .type(ButtonType.Circle)
        .newAttribute() // 调用自定义属性
        .onClick((e: ClickEvent) => {
          this.str += '!';
        })
      MyButton(this.str)
        .type(ButtonType.Normal)
        .width() // 调用重写属性
        .onClick((e: ClickEvent) => {
          this.str += '~';
        })
    }
  }
}
```
