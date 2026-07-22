# Orientation

窗口显示方向类型枚举。<!--Del-->不同枚举值之间的区别可查询[窗口Orientation枚举值8\~10或12和枚举值13\~16的区别(API9)](../../../faqs/faqs-window-manager.md#窗口orientation枚举值810或12和枚举值1316的区别api9)。<!--DelEnd-->

**起始版本：** 9

<!--Device-window-enum Orientation--><!--Device-window-enum Orientation-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## UNSPECIFIED

```TypeScript
UNSPECIFIED = 0
```

表示未定义方向模式，由系统判定。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-UNSPECIFIED = 0--><!--Device-Orientation-UNSPECIFIED = 0-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## PORTRAIT

```TypeScript
PORTRAIT = 1
```

表示竖屏显示模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-PORTRAIT = 1--><!--Device-Orientation-PORTRAIT = 1-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## LANDSCAPE

```TypeScript
LANDSCAPE = 2
```

表示横屏显示模式。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-LANDSCAPE = 2--><!--Device-Orientation-LANDSCAPE = 2-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## PORTRAIT_INVERTED

```TypeScript
PORTRAIT_INVERTED = 3
```

表示反向竖屏显示模式。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-PORTRAIT_INVERTED = 3--><!--Device-Orientation-PORTRAIT_INVERTED = 3-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## LANDSCAPE_INVERTED

```TypeScript
LANDSCAPE_INVERTED = 4
```

表示反向横屏显示模式。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-LANDSCAPE_INVERTED = 4--><!--Device-Orientation-LANDSCAPE_INVERTED = 4-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION

```TypeScript
AUTO_ROTATION = 5
```

跟随传感器自动旋转，可以旋转到竖屏、横屏、反向竖屏、反向横屏四个方向，且不受控制中心的旋转开关控制。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-AUTO_ROTATION = 5--><!--Device-Orientation-AUTO_ROTATION = 5-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_PORTRAIT

```TypeScript
AUTO_ROTATION_PORTRAIT = 6
```

跟随传感器自动竖向旋转，可以旋转到竖屏、反向竖屏，无法旋转到横屏、反向横屏，且不受控制中心的旋转开关控制。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-AUTO_ROTATION_PORTRAIT = 6--><!--Device-Orientation-AUTO_ROTATION_PORTRAIT = 6-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_LANDSCAPE

```TypeScript
AUTO_ROTATION_LANDSCAPE = 7
```

跟随传感器自动横向旋转，可以旋转到横屏、反向横屏，无法旋转到竖屏、反向竖屏，且不受控制中心的旋转开关控制。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-AUTO_ROTATION_LANDSCAPE = 7--><!--Device-Orientation-AUTO_ROTATION_LANDSCAPE = 7-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_RESTRICTED

```TypeScript
AUTO_ROTATION_RESTRICTED = 8
```

跟随传感器自动旋转，可以旋转到竖屏、横屏、反向竖屏、反向横屏四个方向，且受控制中心的旋转开关控制。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-AUTO_ROTATION_RESTRICTED = 8--><!--Device-Orientation-AUTO_ROTATION_RESTRICTED = 8-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_PORTRAIT_RESTRICTED

```TypeScript
AUTO_ROTATION_PORTRAIT_RESTRICTED = 9
```

跟随传感器自动竖向旋转，可以旋转到竖屏、反向竖屏，无法旋转到横屏、反向横屏，且受控制中心的旋转开关控制。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-AUTO_ROTATION_PORTRAIT_RESTRICTED = 9--><!--Device-Orientation-AUTO_ROTATION_PORTRAIT_RESTRICTED = 9-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_LANDSCAPE_RESTRICTED

```TypeScript
AUTO_ROTATION_LANDSCAPE_RESTRICTED = 10
```

跟随传感器自动横向旋转，可以旋转到横屏、反向横屏，无法旋转到竖屏、反向竖屏，且受控制中心的旋转开关控制。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-AUTO_ROTATION_LANDSCAPE_RESTRICTED = 10--><!--Device-Orientation-AUTO_ROTATION_LANDSCAPE_RESTRICTED = 10-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## LOCKED

```TypeScript
LOCKED = 11
```

表示锁定模式，窗口显示方向与屏幕当前方向一致。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-LOCKED = 11--><!--Device-Orientation-LOCKED = 11-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_UNSPECIFIED

```TypeScript
AUTO_ROTATION_UNSPECIFIED = 12
```

跟随传感器自动旋转，受控制中心的旋转开关控制，且可旋转方向受系统判定（如在某种设备，可以旋转到竖屏、横屏、反向横屏三个方向，无法旋转到反向竖屏）。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-AUTO_ROTATION_UNSPECIFIED = 12--><!--Device-Orientation-AUTO_ROTATION_UNSPECIFIED = 12-End-->

**系统能力：** SystemCapability.Window.SessionManager

## USER_ROTATION_PORTRAIT

```TypeScript
USER_ROTATION_PORTRAIT = 13
```

调用时临时旋转到竖屏，之后跟随传感器自动旋转，受控制中心的旋转开关控制，且可旋转方向受系统判定。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-USER_ROTATION_PORTRAIT = 13--><!--Device-Orientation-USER_ROTATION_PORTRAIT = 13-End-->

**系统能力：** SystemCapability.Window.SessionManager

## USER_ROTATION_LANDSCAPE

```TypeScript
USER_ROTATION_LANDSCAPE = 14
```

调用时临时旋转到横屏，之后跟随传感器自动旋转，受控制中心的旋转开关控制，且可旋转方向受系统判定。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-USER_ROTATION_LANDSCAPE = 14--><!--Device-Orientation-USER_ROTATION_LANDSCAPE = 14-End-->

**系统能力：** SystemCapability.Window.SessionManager

## USER_ROTATION_PORTRAIT_INVERTED

```TypeScript
USER_ROTATION_PORTRAIT_INVERTED = 15
```

调用时临时旋转到反向竖屏，之后跟随传感器自动旋转，受控制中心的旋转开关控制，且可旋转方向受系统判定。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-USER_ROTATION_PORTRAIT_INVERTED = 15--><!--Device-Orientation-USER_ROTATION_PORTRAIT_INVERTED = 15-End-->

**系统能力：** SystemCapability.Window.SessionManager

## USER_ROTATION_LANDSCAPE_INVERTED

```TypeScript
USER_ROTATION_LANDSCAPE_INVERTED = 16
```

调用时临时旋转到反向横屏，之后跟随传感器自动旋转，受控制中心的旋转开关控制，且可旋转方向受系统判定。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-USER_ROTATION_LANDSCAPE_INVERTED = 16--><!--Device-Orientation-USER_ROTATION_LANDSCAPE_INVERTED = 16-End-->

**系统能力：** SystemCapability.Window.SessionManager

## FOLLOW_DESKTOP

```TypeScript
FOLLOW_DESKTOP = 17
```

表示跟随桌面的旋转模式，如果桌面可以旋转则可旋转，桌面不可旋转则不可旋转。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Orientation-FOLLOW_DESKTOP = 17--><!--Device-Orientation-FOLLOW_DESKTOP = 17-End-->

**系统能力：** SystemCapability.Window.SessionManager

