# ExtendableColumn（可扩展的Column）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[Column](./ts-container-column.md)的扩展组件的基类。开发者可以自定义扩展组件继承ExtendableColumn，支持重写Column中的[属性](./ts-container-column.md#属性)和[通用属性](./ts-component-general-attributes.md)，同时支持自定义属性。在阅读本文档前，建议提前阅读[Column](./ts-container-column.md)。

**起始版本：** 26.0.0

>  **说明：**
>
>  本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { ExtendableColumn } from '@kit.ArkUI';
```

## 子组件

可以包含子组件。

## 属性

自定义的Column扩展组件类支持重写Column的[属性](./ts-container-column.md#属性)和[通用属性](./ts-component-general-attributes.md)，若不重写，则遵循对应属性的默认行为。此外，扩展组件类支持以下属性和自定义属性。

### setColumnOptions

setColumnOptions(options?: ColumnOptions | ColumnOptionsV2): this

设置纵向布局元素垂直方向间距。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名  | 类型                             | 必填 | 说明                                |
| ------- | -------------------------------- | ---- | ----------------------------------- |
| options | [ColumnOptions](./ts-container-column.md#columnoptions18对象说明) \| [ColumnOptionsV2](./ts-container-column.md#columnoptionsv218对象说明) | 否   | 纵向布局元素垂直方向间距。默认为0。 |

## 事件

支持[通用事件](ts-component-general-events.md)。

## 示例

```ts
'use static'

import { Entry, Component, Text, Column, ExtendableColumn, ColumnOptions, Length, LayoutPolicy } from '@ohos.arkui.component';

class MyColumn extends ExtendableColumn {
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
    this.height();
    this.width();
    return this;
  }
}

@Entry
@Component
struct Index {
  build() {
    MyColumn({ space: 100 } as ColumnOptions) {
      Text('Hello World')
      Text('Hello ArkUI')
    }
    .newAttribute() // 调用自定义属性
  }
}
```

