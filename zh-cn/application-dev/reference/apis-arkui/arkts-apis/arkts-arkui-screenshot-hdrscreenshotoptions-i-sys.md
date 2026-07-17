# HdrScreenshotOptions（系统接口）

设置截取HDR图像的信息。

**起始版本：** 20

<!--Device-screenshot-interface HdrScreenshotOptions--><!--Device-screenshot-interface HdrScreenshotOptions-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { screenshot } from '@kit.ArkUI';
```

## displayId

```TypeScript
displayId?: number
```

表示截取图像的显示设备[Display](arkts-arkui-display-displaystate-e.md)的ID号，该参数应为整数。默认为0。

**类型：** number

**默认值：** The ID of the current display. The value is a positive integer greater than or equal to 0.

**起始版本：** 20

<!--Device-HdrScreenshotOptions-displayId?: long--><!--Device-HdrScreenshotOptions-displayId?: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## displayIntent

```TypeScript
displayIntent?: DisplayIntentType
```

截取图像的显示类型。

**类型：** DisplayIntentType

**默认值：** DisplayIntentType.CANONICAL

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HdrScreenshotOptions-displayIntent?: DisplayIntentType--><!--Device-HdrScreenshotOptions-displayIntent?: DisplayIntentType-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## isCaptureFullOfScreen

```TypeScript
isCaptureFullOfScreen?: boolean
```

表示是否截取当前物理屏上所有DisplayId对应的逻辑屏。对于一个物理屏上有多个DisplayId的场景，true表示截取整个物理屏，false表示只截取DisplayId所在区域的逻辑屏。默认值为false。

**类型：** boolean

**默认值：** false

**起始版本：** 20

<!--Device-HdrScreenshotOptions-isCaptureFullOfScreen?: boolean--><!--Device-HdrScreenshotOptions-isCaptureFullOfScreen?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

## isNotificationNeeded

```TypeScript
isNotificationNeeded?: boolean
```

表示截取图像之后是否发送截屏通知，true表示发送截屏通知，false表示不发送截屏通知，默认值为true。截屏通知可以通过[captureStatusChange](arkts-arkui-display-on-f.md#on-7)接口监听。

**类型：** boolean

**默认值：** true

**起始版本：** 20

<!--Device-HdrScreenshotOptions-isNotificationNeeded?: boolean--><!--Device-HdrScreenshotOptions-isNotificationNeeded?: boolean-End-->

**系统能力：** SystemCapability.Window.SessionManager

**系统接口：** 此接口为系统接口。

