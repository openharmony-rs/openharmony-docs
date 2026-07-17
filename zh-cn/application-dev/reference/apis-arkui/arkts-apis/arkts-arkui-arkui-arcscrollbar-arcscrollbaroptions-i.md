# ArcScrollBarOptions

ArcScrollBar的构造函数参数。

> **说明：**  
>  
> ArcScrollBar与可滚动组件需通过scroller进行绑定后方能实现联动，且ArcScrollBar与可滚动组件仅限于一对一的绑定方式。

**起始版本：** 18

<!--Device-unnamed-declare interface ArcScrollBarOptions--><!--Device-unnamed-declare interface ArcScrollBarOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcScrollBarAttribute, ArcScrollBar } from '@kit.ArkUI';
```

## scroller

```TypeScript
scroller: Scroller
```

可滚动组件的控制器，用于与可滚动组件进行绑定。

**类型：** Scroller

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcScrollBarOptions-scroller: Scroller--><!--Device-ArcScrollBarOptions-scroller: Scroller-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## state

```TypeScript
state?: BarState
```

滚动条状态。<br/>默认值：BarState.Auto

**类型：** BarState

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcScrollBarOptions-state?: BarState--><!--Device-ArcScrollBarOptions-state?: BarState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

