# ArkListOptions

包含创建ArcList组件的基础参数。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## header

```TypeScript
header?: ComponentContent
```

ArcList的头部组件，用于在列表顶部显示标题或自定义内容。不设置时不显示头部组件。

**类型：** ComponentContent

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## initialIndex

```TypeScript
initialIndex?: number
```

设置当前ArcList初次加载时视窗起始位置显示的item的索引值。默认值：0  
**说明：**设置为负数或超过了当前ArcList最后一个item的索引值时视为无效取值，无效取值按默认值显示。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## scroller

```TypeScript
scroller?: Scroller
```

可滚动组件的控制器。与ArcList绑定后，可以通过它控制ArcList的滚动。不设置时不绑定滚动控制器。  
**说明：**不允许和其他滚动类组件，如：List、Grid、 Scroll和WaterFlow绑定同一个滚动控制对 象。

**类型：** [Scroller](../arkts-components/arkts-arkui-scroller-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle
