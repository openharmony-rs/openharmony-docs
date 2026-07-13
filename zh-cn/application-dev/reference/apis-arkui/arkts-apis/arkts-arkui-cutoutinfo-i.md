# CutoutInfo

挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。

**起始版本：** 9

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## boundingRects

```TypeScript
readonly boundingRects: Array<Rect>
```

挖孔、刘海等区域的边界矩形。如果没有挖孔、刘海等区域，数组返回为空。

**类型：** Array<Rect>

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## waterfallDisplayAreaRects

```TypeScript
readonly waterfallDisplayAreaRects: WaterfallDisplayAreaRects
```

瀑布屏曲面部分显示区域。

**类型：** WaterfallDisplayAreaRects

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

