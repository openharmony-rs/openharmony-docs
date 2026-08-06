# FocusMode

枚举，焦距模式。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-camera-enum FocusMode--><!--Device-camera-enum FocusMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_MANUAL

```TypeScript
FOCUS_MODE_MANUAL = 0
```

手动对焦。通过手动修改相机焦距来改变对焦位置，不支持对焦点设置。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-FocusMode-FOCUS_MODE_MANUAL = 0--><!--Device-FocusMode-FOCUS_MODE_MANUAL = 0-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_CONTINUOUS_AUTO

```TypeScript
FOCUS_MODE_CONTINUOUS_AUTO = 1
```

连续自动对焦。不支持对焦点设置。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-FocusMode-FOCUS_MODE_CONTINUOUS_AUTO = 1--><!--Device-FocusMode-FOCUS_MODE_CONTINUOUS_AUTO = 1-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_AUTO

```TypeScript
FOCUS_MODE_AUTO = 2
```

自动对焦。支持对焦点设置，可以使用[Focus.setFocusPoint]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_设置对焦点，根据对焦点执行一次自动对焦。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-FocusMode-FOCUS_MODE_AUTO = 2--><!--Device-FocusMode-FOCUS_MODE_AUTO = 2-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_LOCKED

```TypeScript
FOCUS_MODE_LOCKED = 3
```

对焦锁定。不支持对焦点设置。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-FocusMode-FOCUS_MODE_LOCKED = 3--><!--Device-FocusMode-FOCUS_MODE_LOCKED = 3-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

