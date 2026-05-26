# ExtendableRow（可扩展的Row）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[Row](./ts-container-row.md)的扩展组件的基类。开发者可以自定义扩展组件继承ExtendableRow，支持重写Row中的[属性](./ts-container-row.md#属性)和[通用属性](./ts-component-general-attributes.md)，同时支持自定义属性。在阅读本文档前，建议提前阅读[Row](./ts-container-row.md)。

**起始版本：** 26.0.0

>  **说明：**
>
>  本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { ExtendableRow } from '@kit.ArkUI';
```

## 子组件

可以包含子组件。

## 属性

自定义的Row扩展组件类支持重写Row的[属性](./ts-container-row.md#属性)和[通用属性](./ts-component-general-attributes.md)，若不重写，则遵循对应属性的默认行为。此外，扩展组件类支持以下属性和自定义属性。

### setRowOptions

setRowOptions(options?: RowOptions | RowOptionsV2): this

设置横向布局元素配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名  | 类型                                    | 必填 | 说明                 |
| ------- | --------------------------------------- | ---- | -------------------- |
| options | [RowOptions](./ts-container-row.md#rowoptions18对象说明) \| [RowOptionsV2](./ts-container-row.md#rowoptionsv218对象说明) | 否   | 横向布局元素间距，支持设置number、string或Resource类型。 |

## 事件

支持[通用事件](ts-component-general-events.md)。

## 示例

```ts
'use static'

import { ExtendableRow, RowOptions, Length, Entry, Component, Text } from '@kit.ArkUI';

class MyRow extends ExtendableRow {
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
    MyRow({ space: 100 } as RowOptions) {
      Text('Hello World')
      Text('Hello ArkUI')
    }
    .height() // 调用重写属性
    .border({ width: 2, color: '#6699FF' })
  }
}
```

