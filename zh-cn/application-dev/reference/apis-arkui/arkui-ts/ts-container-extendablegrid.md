# ExtendableGrid（可扩展的Grid）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[Grid](./ts-container-grid.md)的扩展组件的基类。开发者可以自定义扩展组件继承ExtendableGrid，支持重写Grid中的[属性](./ts-container-grid.md#属性)和[通用属性](./ts-component-general-attributes.md)，同时支持自定义属性。在阅读本文档前，建议提前阅读[Grid](./ts-container-grid.md)。

**起始版本：** 26.0.0

>  **说明：**
>
>  本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { ExtendableGrid } from '@kit.ArkUI';
```

## 子组件

仅支持[GridItem](ts-container-griditem.md)子组件和自定义组件。自定义组件在Grid下使用时，建议使用GridItem作为自定义组件的顶层组件，不建议给自定义组件设置属性和事件方法。

## 属性

自定义的Grid扩展组件类支持重写Grid的[属性](./ts-container-grid.md#属性)和[通用属性](./ts-component-general-attributes.md)，若不重写，则遵循对应属性的默认行为。此外，扩展组件类支持以下属性和自定义属性。

### setGridOptions

setGridOptions(scroller?: Scroller, layoutOptions?: GridLayoutOptions): this

设置网格容器配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名   | 类型                                    | 必填 | 说明                                                     |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| scroller | [Scroller](ts-container-scroll.md#scroller) | 否   | 可滚动组件的控制器。用于与可滚动组件进行绑定。 |
| layoutOptions | [GridLayoutOptions](./ts-container-grid.md#gridlayoutoptions10对象说明) | 否 | Grid布局选项。<br/> 未设置时，则按照GridLayoutOptions中各参数的默认值配置。 |

## 事件

支持Grid的[事件](./ts-container-grid.md#事件)、[滚动组件通用事件](ts-container-scrollable-common.md#事件)[通用事件](ts-component-general-events.md)。

## 示例

```ts
'use static'

import { Entry, Component, Grid, Text, BorderOptions, Scroller, GridLayoutOptions, ForEach, GridItem, Color, ExtendableGrid, Length } from '@kit.ArkUI';

class MyGrid extends ExtendableGrid {
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
    super.columnsGap(10);
    super.rowsGap(10);
    super.height(100);
    return this;
  }
}

@Entry
@Component
struct Index {
  data: number[] = [0, 1, 2, 3, 4, 5];

  build() {
    MyGrid() {
      ForEach(this.data, (item: number) => {
        GridItem() {
          Text('N' + item)
            .height(80)
        }
        .backgroundColor(Color.Orange)
      })
    }
    .width() // 调用重写属性
    .border({ width: 1, color: Color.Black } as BorderOptions)
    .columnsTemplate('repeat(auto-fit, 70)')
    .newAttribute() // 调用自定义属性
  }
}
```