# ExtendableGridItem（可扩展的GridItem）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[GridItem](./ts-container-griditem.md)的扩展组件的基类。开发者可以自定义扩展组件继承ExtendableGridItem，支持重写GridItem中的[属性](./ts-container-griditem.md#属性)和[通用属性](./ts-component-general-attributes.md)，同时支持自定义属性。在阅读本文档前，建议提前阅读[GridItem](./ts-container-griditem.md)。

**起始版本：** 26.0.0

>  **说明：**
>
>  本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { ExtendableGridItem } from '@kit.ArkUI';
```

## 子组件

可以包含单个子组件。

## 属性

自定义的GridItem扩展组件类支持重写GridItem的[属性](./ts-container-griditem.md#属性)和[通用属性](./ts-component-general-attributes.md)，若不重写，则遵循对应属性的默认行为。此外，扩展组件类支持以下属性和自定义属性。

### setGridItemOptions

setGridItemOptions(value?: GridItemOptions): this

设置GridItem配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型                                    | 必填 | 说明                 |
| ------- | --------------------------------------- | ---- | -------------------- |
| value | [GridItemOptions](./ts-container-griditem.md#griditemoptions11对象说明) | 否   | GridItem配置参数。<br/> 未设置时，则按照GridItemOptions中各参数的默认值配置。 |

## 事件

支持GridItem的[事件](./ts-container-griditem.md#事件)。

## 示例

```ts
'use static'

import { ExtendableGridItem, GridItemOptions, Length, Entry, Component, Text, ForEach, GridItem, Grid, Color } from '@kit.ArkUI';

class MyGridItem extends ExtendableGridItem {
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
    super.rowStart(1);
    super.backgroundColor(Color.Orange);
    return this;
  }
}

@Entry
@Component
struct Index {
  data: number[] = [0, 1, 2, 3, 4, 5];

  build() {
    Grid() {
      ForEach(this.data, (item: number) => {
        MyGridItem() {
          Text('N' + item)
            .height(80)
        }
        .newAttribute() // 调用自定义属性
      })
    }
    .width('90%')
    .border({ width: 1, color: Color.Black })
    .columnsTemplate('repeat(auto-fit, 70)')
    .columnsGap(10)
    .rowsGap(10)
    .height(100)
  }
}
```

