# GridItem

网格容器中单项内容容器。
> **说明：** > > * > > * 仅支持作为Grid组件的子组件使用。 > > * 当GridItem配合[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，GridItem子组件在 > GridItem创建时创建。配合[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或父组件为Grid时，GridItem子组件在GridItem布局时创 > 建。 > > * 当Grid中存在大量GridItem时，使用[columnStart](arkts-arkui-griditem-attribute.md#columnstart)/ > [columnEnd](arkts-arkui-griditem-attribute.md#columnend)、[rowStart](arkts-arkui-griditem-attribute.md#rowstart)/ > [rowEnd](arkts-arkui-griditem-attribute.md#rowend)设置GridItem大小会导致在使用scrollToIndex滑动到指定Index时，依次遍历GridItem节点，耗时较长。建议使用 > [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md)布局，以提高查找GridItem位置的效率。最佳实践请参考 > [优化Grid组件加载慢丢帧问题](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-improve_grid_performance)。

## 子组件

可以包含单个子组件。

## GridItem

```TypeScript
GridItem(value?: GridItemOptions)
```

创建网格容器中单项内容容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [GridItemOptions](arkts-arkui-griditemoptions-i.md) | 否 | 为GridItem提供可选参数，该对象内包含[GridItemStyle](arkts-arkui-griditemstyle-e.md)枚举类型的style参数。不传入时使用默认样 式，即GridItemStyle.NONE。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [GridItemOptions](arkts-arkui-griditemoptions-i.md) | GridItem样式对象，用于配置GridItem的样式选项。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GridItemStyle](arkts-arkui-griditemstyle-e.md) | GridItem样式枚举，用于定义GridItem的交互态样式。 |

## 示例

GridItem通过设置合理的rowStart、rowEnd、columnStart、columnEnd属性来设置自身位置。需要指定GridItem起始行列号和所占行列数的场景推荐使用Grid的GridLayoutOptions参数，详细可参考Grid的示例1（固定行列Grid）和示例3（可滚动Grid设置跨行跨列节点）。

```TypeScript
// xxx.ets
@Entry
@Component
struct GridItemExample {
  @State numbers: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15'];

  build() {
    Column() {
      Grid() {
        GridItem() {
          Text('4')
            .fontSize(16)
            .backgroundColor(0xFAEEE0)
            .width('100%')
            .height('100%')
            .textAlign(TextAlign.Center)
        }.rowStart(1).rowEnd(2).columnStart(1).columnEnd(2) // 同时设置合理的行列号

        ForEach(this.numbers, (item: string) => {
          GridItem() {
            Text(item)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height('100%')
              .textAlign(TextAlign.Center)
          }
        }, (item: string) => item)

        GridItem() {
          Text('5')
            .fontSize(16)
            .backgroundColor(0xDBD0C0)
            .width('100%')
            .height('100%')
            .textAlign(TextAlign.Center)
        }.columnStart(1).columnEnd(4) // 未设置行号，不按columnStart(1)定位；此处从第5行、索引为0的列开始并跨4列布局
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr 1fr 1fr')
      .width('90%').height(300)
    }.width('100%').margin({ top: 5 })
  }
}
```

使用GridItemOptions设置GridItem样式。

```TypeScript
// xxx.ets
@Entry
@Component
struct GridItemExample {
  @State numbers: string[] = ['0', '1', '2'];

  build() {
    Column({ space: 5 }) {
      Grid() {
        ForEach(this.numbers, (rowItem: string) => {
          ForEach(this.numbers, (item: string) => {
            GridItem({ style: GridItemStyle.NONE }) {
              Text(item)
                .fontSize(16)
                .width('100%')
                .height('100%')
                .textAlign(TextAlign.Center)
                .focusable(true)
            }
            .backgroundColor(0xF9CF93)
          }, (item: string) => item)
        }, (rowItem: string) => rowItem)
      }
      .columnsTemplate('1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr')
      .columnsGap(4)
      .rowsGap(4)
      .width('60%')
      .backgroundColor(0xFAEEE0)
      .height(150)
      .padding(4)

      Grid() {
        ForEach(this.numbers, (rowItem: string) => {
          ForEach(this.numbers, (item: string) => {
            GridItem({ style: GridItemStyle.PLAIN }) {
              Text(item)
                .fontSize(16)
                .width('100%')
                .height('100%')
                .textAlign(TextAlign.Center)
                .focusable(true)
            }
            .backgroundColor(0xF9CF93)
          }, (item: string) => item)
        }, (rowItem: string) => rowItem)
      }
      .columnsTemplate('1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr')
      .columnsGap(4)
      .rowsGap(4)
      .width('60%')
      .backgroundColor(0xFAEEE0)
      .height(150)
      .padding(4)
    }.width('100%').margin({ top: 5 })
  }
}
```
