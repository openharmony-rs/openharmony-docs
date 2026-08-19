# ArkListOptions

包含创建ArcList组件的基础参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ArkListOptions--><!--Device-unnamed-export declare interface ArkListOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## header

```TypeScript
header?: ComponentContentBase
```

支持标题设置。

**类型：** [ComponentContentBase](../../apis-na/arkts-apis/arkts-na-componentcontent-componentcontentbase-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ArkListOptions-header?: ComponentContentBase--><!--Device-ArkListOptions-header?: ComponentContentBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## initialIndex

```TypeScript
initialIndex?: int
```

设置当前ArcList初次加载时视窗起始位置显示的item的索引值。<br/>。 取值限定为整数。默认值：0<br/>设置为负数或超过了当前ArcList最后一个item的索引值时视为无效取值，无效取值按默认值显示。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ArkListOptions-initialIndex?: int--><!--Device-ArkListOptions-initialIndex?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## scroller

```TypeScript
scroller?: Scroller
```

可滚动组件的控制器。与ArcList绑定后，可以通过它控制ArcList的滚动。<br/>不允许和其他滚动类组件绑定同一个滚动控制对象。

**类型：** Scroller

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-ArkListOptions-scroller?: Scroller--><!--Device-ArkListOptions-scroller?: Scroller-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

