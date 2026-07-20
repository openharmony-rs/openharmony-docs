# GridRowDirection

栅格元素排列方向。

> **说明：**  
>  
> - 栅格元素仅支持Row/RowReverse排列，不支持column/ColumnReverse方向排列。  
>  
> - 栅格子组件仅能通过span、offset计算子组件位置与大小。多个子组件span超过规定列数时自动换行。  
>  
> - 单个元素span大小超过最大列数时后台默认span为最大column数。  
>  
> - 新一行的Offset加上子组件的span超过总列数时，将下一个子组件在新的一行放置。  
>  
> - 例：Item1: GridCol({ span: 6 })， Item2: GridCol({ span: 8, offset:11 })。  
> >  
> > !  
> [figures/gridRowOffsetToNextLine.png](docroot://reference/apis-arkui/arkui-ts/figures/gridRowOffsetToNextLine.png)

**起始版本：** 9

<!--Device-unnamed-declare enum GridRowDirection--><!--Device-unnamed-declare enum GridRowDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Row

```TypeScript
Row = 0
```

栅格元素按照行方向排列。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowDirection-Row = 0--><!--Device-GridRowDirection-Row = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RowReverse

```TypeScript
RowReverse = 1
```

栅格元素按照逆序行方向排列。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowDirection-RowReverse = 1--><!--Device-GridRowDirection-RowReverse = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

