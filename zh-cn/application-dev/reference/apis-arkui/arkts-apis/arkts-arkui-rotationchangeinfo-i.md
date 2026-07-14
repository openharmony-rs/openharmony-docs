# RotationChangeInfo

窗口旋转变化时的窗口信息。

**起始版本：** 19

**系统能力：** SystemCapability.Window.SessionManager

## displayId

```TypeScript
displayId: number
```

窗口所在屏幕Id。

**类型：** number

**起始版本：** 19

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## displayRect

```TypeScript
displayRect: Rect
```

窗口所在屏幕旋转后的矩形区域大小。

**类型：** Rect

**起始版本：** 19

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## orientation

```TypeScript
orientation: number
```

窗口显示方向。

- 0表示竖屏。
- 1表示反向横屏。
- 2表示反向竖屏。
- 3表示横屏。

开发者在使用时，需要注意该方向与display对象的属性orientation含义不一致。

**类型：** number

**起始版本：** 19

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## type

```TypeScript
type: RotationChangeType
```

窗口旋转事件类型。

**类型：** RotationChangeType

**起始版本：** 19

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

