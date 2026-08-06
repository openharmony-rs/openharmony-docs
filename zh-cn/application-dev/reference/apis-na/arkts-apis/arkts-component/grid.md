# component/grid

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ExtendableGrid](grid-extendablegrid-c.md) | 可扩展Grid组件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ComputedBarAttribute](grid-computedbarattribute-i.md) | 滚动条位置和长度对象。 |
| [GridLayoutOptions](grid-gridlayoutoptions-i.md) | Grid布局选项。 |
| [UIGridEvent](grid-uigridevent-i.md) | frameNode中\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法的返回值，可用于给Grid 节点设置滚动事件。 UIGridEvent继承于[UIScrollableCommonEvent]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [GridLayoutOptions](grid-gridlayoutoptions-i-sys.md) | Grid布局选项。 |
| [StartLineInfo](grid-startlineinfo-i-sys.md) | 用于记录Grid页面内起始行的位置信息。 **系统接口：** 此接口为系统接口。 **模型约束：** 此接口仅可在Stage模型下使用。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GridDirection](grid-griddirection-e.md) | 主轴布局方向枚举。 |
| [GridItemAlignment](grid-griditemalignment-e.md) | GridItem的对齐方式枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnGridScrollIndexCallback](arkts-na-ongridscrollindexcallback-t.md) | Grid组件可见区域item变化事件的回调类型。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [OnGetStartIndexByIndexCallback](arkts-na-ongetstartindexbyindexcallback-t-sys.md) | 根据指定的目标索引，计算Grid滚动到该位置时页面内对应的起始行，用于支持[scrollToIndex]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_等操作。 **系统接口：** 此接口为系统接口。 **模型约束：** 此接口仅可在Stage模型下使用。 |
| [OnGetStartIndexByOffsetCallback](arkts-na-ongetstartindexbyoffsetcallback-t-sys.md) | 根据Grid的总偏移量，计算当前页面起始行的位置，用于快速滑动或反向滑动场景。 **系统接口：** 此接口为系统接口。 **模型约束：** 此接口仅可在Stage模型下使用。 |
<!--DelEnd-->

