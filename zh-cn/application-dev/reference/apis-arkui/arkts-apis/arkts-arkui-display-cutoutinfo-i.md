# CutoutInfo

挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。

**起始版本：** 9

<!--Device-display-interface CutoutInfo--><!--Device-display-interface CutoutInfo-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## boundingRects

```TypeScript
readonly boundingRects: Array<Rect>
```

挖孔、刘海等区域的边界矩形。如果没有挖孔、刘海等区域，数组返回为空。

**类型：** Array<Rect>

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CutoutInfo-readonly boundingRects: Array<Rect>--><!--Device-CutoutInfo-readonly boundingRects: Array<Rect>-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## waterfallDisplayAreaRects

```TypeScript
readonly waterfallDisplayAreaRects: WaterfallDisplayAreaRects
```

瀑布屏曲面部分显示区域。

**类型：** WaterfallDisplayAreaRects

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CutoutInfo-readonly waterfallDisplayAreaRects: WaterfallDisplayAreaRects--><!--Device-CutoutInfo-readonly waterfallDisplayAreaRects: WaterfallDisplayAreaRects-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

