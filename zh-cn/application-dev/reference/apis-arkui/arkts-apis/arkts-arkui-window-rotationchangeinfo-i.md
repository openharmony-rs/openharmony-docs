# RotationChangeInfo

窗口旋转变化时的窗口信息。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

<!--Device-window-interface RotationChangeInfo--><!--Device-window-interface RotationChangeInfo-End-->

**系统能力：** SystemCapability.Window.SessionManager

## displayId

```TypeScript
displayId: long
```

窗口所在屏幕Id。

**类型：** long

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-RotationChangeInfo-displayId: long--><!--Device-RotationChangeInfo-displayId: long-End-->

**系统能力：** SystemCapability.Window.SessionManager

## displayRect

```TypeScript
displayRect: Rect
```

窗口所在屏幕旋转后的矩形区域大小。

**类型：** Rect

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-RotationChangeInfo-displayRect: Rect--><!--Device-RotationChangeInfo-displayRect: Rect-End-->

**系统能力：** SystemCapability.Window.SessionManager

## orientation

```TypeScript
orientation: int
```

窗口显示方向。 - 0表示竖屏。 - 1表示反向横屏。 - 2表示反向竖屏。 - 3表示横屏。 开发者在使用时，需要注意该方向与display对象的属性orientation含义不一致。

**类型：** int

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-RotationChangeInfo-orientation: int--><!--Device-RotationChangeInfo-orientation: int-End-->

**系统能力：** SystemCapability.Window.SessionManager

## type

```TypeScript
type: RotationChangeType
```

窗口旋转事件类型。

**类型：** RotationChangeType

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-RotationChangeInfo-type: RotationChangeType--><!--Device-RotationChangeInfo-type: RotationChangeType-End-->

**系统能力：** SystemCapability.Window.SessionManager

