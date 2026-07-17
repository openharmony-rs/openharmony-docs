# RotationInfoType

旋转信息类型枚举。

**起始版本：** 23

<!--Device-window-enum RotationInfoType--><!--Device-window-enum RotationInfoType-End-->

**系统能力：** SystemCapability.Window.SessionManager

## WINDOW_ORIENTATION

```TypeScript
WINDOW_ORIENTATION = 0
```

窗口所在屏幕的显示方向，以窗口模块对横竖屏的定义方式表示。

开发者在使用时，需要注意该方向表示[RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md)中的orientation参数。

**起始版本：** 23

<!--Device-RotationInfoType-WINDOW_ORIENTATION = 0--><!--Device-RotationInfoType-WINDOW_ORIENTATION = 0-End-->

**系统能力：** SystemCapability.Window.SessionManager

## DISPLAY_ORIENTATION

```TypeScript
DISPLAY_ORIENTATION = 1
```

屏幕显示方向，以屏幕模块对横竖屏的定义方式表示。

开发者在使用时，需要注意该方向表示[display](arkts-arkui-display-displaystate-e.md)对象的orientation属性。

**起始版本：** 23

<!--Device-RotationInfoType-DISPLAY_ORIENTATION = 1--><!--Device-RotationInfoType-DISPLAY_ORIENTATION = 1-End-->

**系统能力：** SystemCapability.Window.SessionManager

## DISPLAY_ROTATION

```TypeScript
DISPLAY_ROTATION = 2
```

设备的屏幕顺时针旋转角度。

开发者在使用时，需要注意该方向表示[display](arkts-arkui-display-displaystate-e.md)对象的rotation属性。

**起始版本：** 23

<!--Device-RotationInfoType-DISPLAY_ROTATION = 2--><!--Device-RotationInfoType-DISPLAY_ROTATION = 2-End-->

**系统能力：** SystemCapability.Window.SessionManager

