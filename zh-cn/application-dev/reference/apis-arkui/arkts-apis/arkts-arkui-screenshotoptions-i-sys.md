# ScreenshotOptions（系统接口）

设置截取图像的信息。

**起始版本：** 7

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## displayId

```TypeScript
displayId?: number
```

表示截取图像的显示设备[Display](arkts-arkui-displaystate-e.md)的ID号，该参数应为整数。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## imageSize

```TypeScript
imageSize?: Size
```

表示截取图像的区域，不传值默认返回displayId所在逻辑屏的区域。

**类型：** Size

**起始版本：** 7

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## isCaptureFullOfScreen

```TypeScript
isCaptureFullOfScreen?: boolean
```

表示是否截取当前Screen上的所有display。对于一个Screen上有多个display的场景，为true表示截取整个Screen，false则只截取displayId所在逻辑屏的区域，默认值为false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## isNotificationNeeded

```TypeScript
isNotificationNeeded?: boolean
```

表示截取图像之后是否发送截屏通知，true表示发送截屏通知，false表示不发送截屏通知，默认值为true。截屏通知可以通过
[captureStatusChange](arkts-arkui-on-f.md#on-7)接口
监听。

**类型：** boolean

**起始版本：** 14

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: number
```

表示截取图像后要旋转的角度，当前仅支持输入值为0，默认值为0。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## screenRect

```TypeScript
screenRect?: Rect
```

表示截取图像的区域，不传值默认返回displayId所在逻辑屏的区域。

**类型：** Rect

**起始版本：** 7

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

