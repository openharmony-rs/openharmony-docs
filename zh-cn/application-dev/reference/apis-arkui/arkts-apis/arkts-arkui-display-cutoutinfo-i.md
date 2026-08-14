# CutoutInfo

挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-display-interface CutoutInfo--><!--Device-display-interface CutoutInfo-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## boundingRects

```TypeScript
readonly boundingRects: Array<Rect>
```

挖孔、刘海等区域的边界矩形。如果没有挖孔、刘海等区域，数组返回为空。

**类型：** Array&lt;Rect&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CutoutInfo-readonly boundingRects: Array<Rect>--><!--Device-CutoutInfo-readonly boundingRects: Array<Rect>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## waterfallDisplayAreaRects

```TypeScript
readonly waterfallDisplayAreaRects: WaterfallDisplayAreaRects
```

瀑布屏曲面部分显示区域。

**类型：** [WaterfallDisplayAreaRects](arkts-arkui-display-waterfalldisplayarearects-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CutoutInfo-readonly waterfallDisplayAreaRects: WaterfallDisplayAreaRects--><!--Device-CutoutInfo-readonly waterfallDisplayAreaRects: WaterfallDisplayAreaRects-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

