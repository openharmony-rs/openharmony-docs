# RotationChangeResult

应用在窗口旋转变化时返回的信息，系统会根据此信息改变当前窗口矩形区域大小。当返回主窗口旋转变化的信息时，系统不改变主窗口的大小。

应用窗口与系统窗口大小存在限制，具体限制与相关规则可见
[resize](arkts-arkui-window-i.md#resize-2)。

**起始版本：** 19

**系统能力：** SystemCapability.Window.SessionManager

## rectType

```TypeScript
rectType: RectType
```

窗口矩形区域坐标系类型。

**类型：** RectType

**起始版本：** 19

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect: Rect
```

相对于屏幕或父窗坐标系的窗口矩形区域信息。

**类型：** Rect

**起始版本：** 19

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

