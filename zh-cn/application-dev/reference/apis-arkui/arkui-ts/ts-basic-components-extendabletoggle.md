# ExtendableToggle (可扩展的Toggle)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[Toggle](./ts-basic-components-toggle.md)的扩展组件的基类。开发者可以自定义扩展组件继承ExtendableToggle，支持重写Toggle中的[属性](./ts-basic-components-toggle.md#属性)和[通用属性](./ts-component-general-attributes.md)，同时支持自定义属性。在阅读本文档前，建议提前阅读[Toggle](./ts-basic-components-toggle.md)。开发指南请参考[内置组件扩展](../../../ui/state-management-static/arkts-static-extendable-inner-component.md)。

**起始版本：** 26.0.0

>  **说明：**
>
>  本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { ExtendableToggle } from '@kit.ArkUI';
```

## 子组件

仅当ToggleType设置为Button时，可包含子组件。

## 属性

自定义的Toggle扩展组件类支持重写Toggle的[属性](./ts-basic-components-toggle.md#属性)和[通用属性](./ts-component-general-attributes.md)，若不重写，则遵循对应属性的默认行为。此外，扩展组件类支持以下属性和自定义属性。

### setToggleOptions

setToggleOptions(options: ToggleOptions): this

设置Toggle配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名  | 类型                                    | 必填 | 说明                 |
| ------- | --------------------------------------- | ---- | -------------------- |
| options | [ToggleOptions](./ts-basic-components-toggle.md#toggleoptions18对象说明) | 是   | Toggle组件的配置选项，用于配置开关的样式类型和初始状态。 |

## 事件

支持Toggle的[事件](./ts-basic-components-toggle.md#事件)[通用事件](ts-component-general-events.md)。

## 示例

```ts
'use static'

import { ExtendableToggle, ToggleOptions, Length, Toggle, Entry, Component, ResourceColor, ToggleType } from '@kit.ArkUI';

class MyToggle extends ExtendableToggle {
  // 通用属性
  width(): this {
    super.width('100%');
    return this;
  }

  // 自定义属性
  newAttribute(): this {
    super.height('10%');
    super.width('20%');
    return this;
  }
}

@Entry
@Component
struct Index {
  build() {
    // 调用扩展组件
    MyToggle({ type: ToggleType.Switch, isOn: false } as ToggleOptions)
      .selectedColor('#007DFF')
      .newAttribute() // 调用自定义属性
      .onChange((isOn: boolean) => {
        console.info('Component status:' + isOn);
      })
  }
}
```

