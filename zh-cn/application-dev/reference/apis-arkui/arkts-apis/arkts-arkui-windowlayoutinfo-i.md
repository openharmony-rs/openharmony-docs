# WindowLayoutInfo

窗口布局信息。

**起始版本：** 15

**系统能力：** SystemCapability.Window.SessionManager

## windowAlpha

```TypeScript
windowAlpha?: number
```

窗口透明度。有效值范围为[0.0, 1.0]，0.0表示完全透明，1.0表示完全不透明。默认值是-1.0，表示未查询到窗口透明度或者查询失败。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## windowRect

```TypeScript
windowRect: Rect
```

窗口尺寸，窗口在屏幕上的实际位置和大小。

**类型：** Rect

**起始版本：** 15

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

