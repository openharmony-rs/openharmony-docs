# MultiScreenPositionOptions（系统接口）

屏幕位置信息。

**起始版本：** 23

<!--Device-screen-interface MultiScreenPositionOptions--><!--Device-screen-interface MultiScreenPositionOptions-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { screen } from '@kit.ArkUI';
import { screenshot } from '@kit.ArkUI';
```

## id

```TypeScript
id: long
```

屏幕的ID，该参数应为正整数，非正整数会作为非法参数报错。

**类型：** long

**起始版本：** 23

<!--Device-MultiScreenPositionOptions-id: long--><!--Device-MultiScreenPositionOptions-id: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## startX

```TypeScript
startX: long
```

屏幕的起始X轴坐标。以两块屏幕外接矩形的左上顶点为原点，向右为正方向。该参数应为正整数，非正整数会作为非法参数报错。

**类型：** long

**起始版本：** 23

<!--Device-MultiScreenPositionOptions-startX: long--><!--Device-MultiScreenPositionOptions-startX: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## startY

```TypeScript
startY: long
```

屏幕的起始Y轴坐标。以两块屏幕外接矩形的左上顶点为原点，向下为正方向。该参数应为正整数，非正整数会作为非法参数报错。

**类型：** long

**起始版本：** 23

<!--Device-MultiScreenPositionOptions-startY: long--><!--Device-MultiScreenPositionOptions-startY: long-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

