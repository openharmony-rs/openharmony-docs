# ExtendableRelativeContainer（可扩展的RelativeContainer）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[RelativeContainer](./ts-container-relativecontainer.md)的扩展组件的基类。开发者可以自定义扩展组件继承ExtendableRelativeContainer，支持重写RelativeContainer中的[属性](./ts-container-relativecontainer.md#属性)和[通用属性](./ts-component-general-attributes.md)，同时支持自定义属性。在阅读本文档前，建议提前阅读[RelativeContainer](./ts-container-relativecontainer.md)。

**起始版本：** 26.0.0

>  **说明：**
>
>  本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { ExtendableRelativeContainer } from '@kit.ArkUI';
```

## 子组件

可以包含子组件。

## 属性

自定义的RelativeContainer扩展组件类支持重写RelativeContainer的[属性](./ts-container-relativecontainer.md#属性)和[通用属性](./ts-component-general-attributes.md)，若不重写，则遵循对应属性的默认行为。此外，扩展组件类支持以下属性和自定义属性。

### setRelativeContainerOptions

setRelativeContainerOptions(): this

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

## 事件

支持[通用事件](ts-component-general-events.md)。

## 示例

```ts
'use static'

import { ExtendableRelativeContainer, Length, Entry, Component, Text } from '@kit.ArkUI';

class MyRelativeContainer extends ExtendableRelativeContainer {
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
    super.width('50%');
    return this;
  }
}

@Entry
@Component
struct Index {
  build() {
    // 调用扩展组件
    MyRelativeContainer() {
      Text('RelativeContainer')
    }
    .border({ width: 2, color: '#6699FF' })
    .newAttribute() // 调用自定义属性
  }
}
```

