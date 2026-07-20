# GridItem

网格容器中单项内容容器。

> **说明：**
>
> *
>
> * 仅支持作为[Grid]{@link grid}组件的子组件使用。
>
> * 当GridItem配合[LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)使用时，GridItem子组件在
> GridItem创建时创建。配合[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、
> [ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)使用时，或父组件为Grid时，GridItem子组件在GridItem布局时创
> 建。
>
> * 当Grid中存在大量GridItem时，使用[columnStart]{@link GridItemAttribute#columnStart}/
> [columnEnd]{@link GridItemAttribute#columnEnd}、[rowStart]{@link GridItemAttribute#rowStart}/
> [rowEnd]{@link GridItemAttribute#rowEnd}设置GridItem大小会导致在使用scrollToIndex滑动到指定Index时，依次遍历GridItem节点，耗时较长。建议使用
> [GridLayoutOptions]{@link GridLayoutOptions}布局，以提高查找GridItem位置的效率。最佳实践请参考
> [优化Grid组件加载慢丢帧问题](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-improve_grid_performance)。

## 子组件

可以包含单个子组件。

## GridItem

```TypeScript
GridItem(value?: GridItemOptions)
```

创建网格容器中单项内容容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridItemInterface-(value?: GridItemOptions): GridItemAttribute--><!--Device-GridItemInterface-(value?: GridItemOptions): GridItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [GridItemOptions](arkts-arkui-griditemoptions-i.md) | 否 | 为GridItem提供可选参数，该对象内含有[GridItemStyle]{@link GridItemStyle}枚举类型的style参 数。 |

## 汇总

- [GridItemOptions](arkts-arkui-griditem-griditemoptions-i.md)
- [GridItemStyle](arkts-arkui-griditem-griditemstyle-e.md)
