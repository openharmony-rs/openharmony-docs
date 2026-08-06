# BrightnessInfo

屏幕亮度信息。此类型中的信息均来自底层屏幕信息数据。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-display-interface BrightnessInfo--><!--Device-display-interface BrightnessInfo-End-->

**系统能力：** SystemCapability.Window.SessionManager

## currentHeadroom

```TypeScript
readonly currentHeadroom: double
```

当前亮度动态余量，该参数为大于0的浮点数。默认值为1.0。

**类型：** double

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-BrightnessInfo-readonly currentHeadroom: double--><!--Device-BrightnessInfo-readonly currentHeadroom: double-End-->

**系统能力：** SystemCapability.Window.SessionManager

## maxHeadroom

```TypeScript
readonly maxHeadroom: double
```

当前最大亮度余量，该参数为大于0的浮点数。默认值为1.0。

**类型：** double

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-BrightnessInfo-readonly maxHeadroom: double--><!--Device-BrightnessInfo-readonly maxHeadroom: double-End-->

**系统能力：** SystemCapability.Window.SessionManager

## sdrNits

```TypeScript
readonly sdrNits: double
```

屏幕的亮度，该参数为大于0的浮点数。默认值为500.0。

**类型：** double

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-BrightnessInfo-readonly sdrNits: double--><!--Device-BrightnessInfo-readonly sdrNits: double-End-->

**系统能力：** SystemCapability.Window.SessionManager

