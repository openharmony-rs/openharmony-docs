# GridItem

网格容器中单项内容容器。

> **说明：** > > * > > * 仅支持作为Grid组件的子组件使用。 > > * 当GridItem配合[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，GridItem子组件在 > GridItem创建时创建。配合[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或父组件为Grid时，GridItem子组件在GridItem布局时创 > 建。 > > * 当Grid中存在大量GridItem时，使用[columnStart](arkts-arkui-griditem-comp-attribute.md#columnstart)/ > [columnEnd](arkts-arkui-griditem-comp-attribute.md#columnend)、[rowStart](arkts-arkui-griditem-comp-attribute.md#rowstart)/ > [rowEnd](arkts-arkui-griditem-comp-attribute.md#rowend)设置GridItem大小会导致在使用scrollToIndex滑动到指定Index时，依次遍历GridItem节点，耗时较长。建议使用 > [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md)布局，以提高查找GridItem位置的效率。最佳实践请参考 > [优化Grid组件加载慢丢帧问题](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-improve_grid_performance)。

## 子组件

可以包含单个子组件。

## GridItem

```TypeScript
GridItem(value?: GridItemOptions)
```

创建网格容器中单项内容容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [GridItemOptions](arkts-arkui-griditemoptions-i.md) | 否 | 为GridItem提供可选参数，该对象内包含[GridItemStyle](arkts-arkui-griditemstyle-e.md)枚举类型的style参数。不传入时使用默认样式，即GridItemStyle.NONE。<br> |

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

```TypeScript
### 示例1（GridItem设置自身位置）

GridItem通过设置合理的rowStart、rowEnd、columnStart、columnEnd属性来设置自身位置。需要指定GridItem起始行列号和所占行列数的场景推荐使用Grid的[GridLayoutOptions](ts-container-grid.md#gridlayoutoptions10对象说明)参数，详细可参考Grid的[示例1（固定行列Grid）](ts-container-grid.md#示例1固定行列grid)和[示例3（可滚动Grid设置跨行跨列节点）](ts-container-grid.md#示例3可滚动grid设置跨行跨列节点)。


```

```TypeScript
### 示例2（设置GridItem样式）

使用GridItemOptions设置GridItem样式。
```
