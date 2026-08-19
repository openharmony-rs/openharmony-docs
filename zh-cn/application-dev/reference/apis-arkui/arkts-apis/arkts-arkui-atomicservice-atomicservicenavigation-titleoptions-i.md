# TitleOptions

标题栏选项。

**起始版本：** 12

<!--Device-unnamed-export interface TitleOptions--><!--Device-unnamed-export interface TitleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceNavigation, NavDestinationBuilder, MixMode, GradientAlpha, BackgroundTheme, TitleBarType, SideBarOptions, TitleOptions, GradientBackground } from '@kit.ArkUI';
```

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

标题栏背景颜色。

**类型：** ResourceColor

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TitleOptions-backgroundColor?: ResourceColor--><!--Device-TitleOptions-backgroundColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## barStyle

```TypeScript
barStyle?: BarStyle
```

设置标题栏样式。

**类型：** BarStyle

**默认值：** BarStyle.STANDARD

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TitleOptions-barStyle?: BarStyle--><!--Device-TitleOptions-barStyle?: BarStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isBlurEnabled

```TypeScript
isBlurEnabled?: boolean
```

标题栏是否模糊。

**类型：** boolean

**默认值：** true

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TitleOptions-isBlurEnabled?: boolean--><!--Device-TitleOptions-isBlurEnabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## titleBarType

```TypeScript
titleBarType?: TitleBarType
```

设置标题栏类型。

**类型：** [TitleBarType](arkts-arkui-atomicservice-atomicservicenavigation-titlebartype-e.md)

**默认值：** TitleBarType.ROUND_ICON

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TitleOptions-titleBarType?: TitleBarType--><!--Device-TitleOptions-titleBarType?: TitleBarType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## titleIcon

```TypeScript
titleIcon?: Resource | SymbolGlyphModifier
```

设置标题栏的图标。

**类型：** Resource \| SymbolGlyphModifier

**默认值：** atomicservice icon

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TitleOptions-titleIcon?: Resource | SymbolGlyphModifier--><!--Device-TitleOptions-titleIcon?: Resource | SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

