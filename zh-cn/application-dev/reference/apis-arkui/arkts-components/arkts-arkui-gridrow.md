# GridRow

栅格布局可以为布局提供规律性的结构，解决多尺寸多设备的动态布局问题，保证不同设备上各个模块的布局一致性。
栅格容器组件，仅可以和栅格子组件(GridCol)在栅格布局场景中使用。
支持根据设备尺寸和断点动态调整列数与间距，实现响应式布局。
> **说明：** > > 该组件从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件

可以包含GridCol子组件。

## GridRow

```TypeScript
GridRow(option?: GridRowOptions)
```

栅格行布局容器。仅可以和栅格子组件在栅格布局场景中使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [GridRowOptions](arkts-arkui-gridrowoptions-i.md) | 否 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BreakPoints](arkts-arkui-breakpoints-i.md) | 设置栅格容器组件的断点。更多断点的说明参考[栅格容器断点](../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)。<!--code_no_check--> |
| [GridRowColumnOption](arkts-arkui-gridrowcolumnoption-i.md) | 栅格在不同宽度设备类型下的栅格列数配置。API version 20之前，仅配置部分断点下GridRow组件的栅格列数，取已配置的相邻较小断点（如md的相邻较小断点为sm）的栅格列数补全未配置的栅格列数。若未配置相邻较小断点的栅格列数，以默认栅格列数12补全未配置的栅格列 数。<!--code_no_check-->API version 20及以后，仅配置部分断点下GridRow组件的栅格列数，取已配置的相邻较小断点的栅格列数补全未配置的栅格列数。若未配置相邻较小断点的栅格列数，取已配置的更大断点的栅格列数补全未配置的栅格列数。<!--code_no_check-->建议手动配置不同断点下GridRow组件的栅格列数，避免默认补全的栅格列数的布局效果不符合预期。每列栅格的宽度为GridRow的内容区大小减去栅格子组件的间距gutter，再除以总的栅格列数。比如，宽800vp的GridRow设置columns为12，gutter设置为10vp，padding设置为20vp，那么每列栅格的宽度为 (800 - 20 * 2 - 10 * 11) / 12。 |
| [GridRowOptions](arkts-arkui-gridrowoptions-i.md) | 设置栅格行布局容器的布局选项。 |
| [GridRowSizeOption](arkts-arkui-gridrowsizeoption-i.md) | 栅格在不同宽度设备类型下的gutter大小配置。 |
| [GutterOption](arkts-arkui-gutteroption-i.md) | 栅格布局间距类型，用于描述栅格子组件不同方向的间距。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BreakpointsReference](arkts-arkui-breakpointsreference-e.md) | 设置栅格容器组件的断点参照物。 |
| [GridRowDirection](arkts-arkui-gridrowdirection-e.md) | 栅格元素排列方向。 |

## 示例

本示例展示GridRow组件的基本用法。

```TypeScript
// xxx.ets
@Entry
@Component
struct GridRowExample {
  @State bgColors: Color[] = [Color.Red, Color.Orange, Color.Yellow, Color.Green, Color.Pink, Color.Grey, Color.Blue, Color.Brown]
  @State currentBp: string = 'unknown'

  build() {
    Column() {
      GridRow({
        columns: 5,
        gutter: { x: 5, y: 10 },
        breakpoints: { value: ['400vp', '600vp', '800vp'],
          reference: BreakpointsReference.WindowSize },
        direction: GridRowDirection.Row
      }) {
        ForEach(this.bgColors, (color: Color) => {
          GridCol({ span: { xs: 1, sm: 2, md: 3, lg: 4 }, offset: 0, order: 0 }) {
            Row().width('100%').height('20vp')
          }.borderColor(color).borderWidth(2)
        })
      }.width('100%').height('100%')
      .onBreakpointChange((breakpoint) => {
        this.currentBp = breakpoint
      })
    }.width('80%').margin({ left: 10, top: 5, bottom: 5 }).height(200)
    .border({ color: '#880606', width: 2 })
  }
}
```

本示例展示GridCol组件在不同alignItems对齐方式下的效果。

```TypeScript
@ComponentV2
struct AlignItemsDemo {
  bgColors: Color[] = [Color.Red, Color.Orange, Color.Yellow, Color.Green, Color.Pink];
  @Param alignment: ItemAlign = ItemAlign.Start; // 接收父组件传入的alignItems属性值

  ToString(alignment: ItemAlign): string {
    switch (alignment) {
      case ItemAlign.Start:
        return 'ItemAlign.Start';
      case ItemAlign.Center:
        return 'ItemAlign.Center';
      case ItemAlign.End:
        return 'ItemAlign.End';
      case ItemAlign.Stretch:
        return 'ItemAlign.Stretch';
      default:
        return 'ItemAlign.Auto';
    }
  }

  build() {
    Column() {
      Text(this.ToString(this.alignment))
        .fontSize(9)
        .fontColor(0xCCCCCC)
        .width('90%')
        .alignSelf(ItemAlign.Start)
      GridRow({
        columns: 5,
        gutter: { x: 5, y: 10 },
      }) {
        ForEach(this.bgColors, (color: Color, index: number) => {
          GridCol({ span: 1 }) {
            Row() {
            }.width('100%').height(`${(index + 1) * 20}%`) // GridCol内的Row设置不同的高度，方便观察alignItems属性的效果
          }.borderColor(color).borderWidth(2)
        })
      }
      .border({ color: '#880606', width: 2 })
      .alignItems(this.alignment)
      .width('100%')
    }
    .height('20%')
  }
}

@Entry
@ComponentV2
struct GridRowExample {
  alignmentArray: ItemAlign[] = [ItemAlign.Start, ItemAlign.Center, ItemAlign.End, ItemAlign.Stretch];

  build() {
    Column({ space: 15 }) {
      ForEach(this.alignmentArray, (ele: ItemAlign) => {
        AlignItemsDemo({ alignment: ele })
      })
    }.width('80%').margin({ left: 10, top: 5, bottom: 5 }).height('100%')
  }
}
```
