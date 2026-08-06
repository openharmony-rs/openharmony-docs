# AvoidAreaType

窗口内容的避让区域的类型枚举。 窗口内容做\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_适配时，需要按照AvoidAreaType对应的 [AvoidArea]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_做窗口内容避让。 \_\_\_MD\_COMMENT\_DESC\_USD\_2\_\_\_ \_\_\_MD\_COMMENT\_DESC\_USD\_3\_\_\_

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-window-enum AvoidAreaType--><!--Device-window-enum AvoidAreaType-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## TYPE_SYSTEM

```TypeScript
TYPE_SYSTEM = 0
```

表示系统默认区域。\_\_\_MD\_COMMENT\_DESC\_USD\_0\_\_\_包含状态栏和三键导航栏区域。\_\_\_MD\_COMMENT\_DESC\_USD\_1\_\_\_

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AvoidAreaType-TYPE_SYSTEM = 0--><!--Device-AvoidAreaType-TYPE_SYSTEM = 0-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## TYPE_CUTOUT

```TypeScript
TYPE_CUTOUT = 1
```

表示挖孔区域。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AvoidAreaType-TYPE_CUTOUT = 1--><!--Device-AvoidAreaType-TYPE_CUTOUT = 1-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## TYPE_SYSTEM_GESTURE

```TypeScript
TYPE_SYSTEM_GESTURE = 2
```

表示侧边返回手势区域。当前所有设备均无此类型避让区域。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AvoidAreaType-TYPE_SYSTEM_GESTURE = 2--><!--Device-AvoidAreaType-TYPE_SYSTEM_GESTURE = 2-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## TYPE_KEYBOARD

```TypeScript
TYPE_KEYBOARD = 3
```

表示固定态软键盘区域。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AvoidAreaType-TYPE_KEYBOARD = 3--><!--Device-AvoidAreaType-TYPE_KEYBOARD = 3-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## TYPE_NAVIGATION_INDICATOR

```TypeScript
TYPE_NAVIGATION_INDICATOR = 4
```

表示底部导航区域。当三键导航显示时，底部导航避让区域始终存在。\_\_\_MD\_COMMENT\_DESC\_USD\_0\_\_\_OpenHarmony各设备不支持此能力。\_\_\_MD\_COMMENT\_DESC\_USD\_1\_\_\_

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AvoidAreaType-TYPE_NAVIGATION_INDICATOR = 4--><!--Device-AvoidAreaType-TYPE_NAVIGATION_INDICATOR = 4-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## TYPE_FLOAT_NAVIGATION

```TypeScript
TYPE_FLOAT_NAVIGATION = 5
```

表示三键导航区域。\_\_\_MD\_COMMENT\_DESC\_USD\_0\_\_\_OpenHarmony各设备不支持此能力。\_\_\_MD\_COMMENT\_DESC\_USD\_1\_\_\_

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AvoidAreaType-TYPE_FLOAT_NAVIGATION = 5--><!--Device-AvoidAreaType-TYPE_FLOAT_NAVIGATION = 5-End-->

**系统能力：** SystemCapability.Window.SessionManager

