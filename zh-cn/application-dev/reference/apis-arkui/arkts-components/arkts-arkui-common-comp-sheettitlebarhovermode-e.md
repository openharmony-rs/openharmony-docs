# SheetTitleBarHoverMode

```TypeScript
declare enum SheetTitleBarHoverMode
```

标题栏悬浮模式枚举。

**起始版本：** 26.0.1

<!--Device-unnamed-declare enum SheetTitleBarHoverMode--><!--Device-unnamed-declare enum SheetTitleBarHoverMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SAFE_AREA_PADDING

```TypeScript
SAFE_AREA_PADDING = 2
```

安全区域填充模式：标题栏放置在安全区域padding区域。内容扩展到安全区域，滚动内容裁剪到安全区域。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-SheetTitleBarHoverMode-SAFE_AREA_PADDING = 2--><!--Device-SheetTitleBarHoverMode-SAFE_AREA_PADDING = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## STACK

```TypeScript
STACK = 1
```

堆叠模式：标题栏悬浮于内容之上。开发者需要在内容顶部添加padding以避免遮挡。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-SheetTitleBarHoverMode-STACK = 1--><!--Device-SheetTitleBarHoverMode-STACK = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 0
```

标准模式：标题栏与内容上下排布，无重叠。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-SheetTitleBarHoverMode-STANDARD = 0--><!--Device-SheetTitleBarHoverMode-STANDARD = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
