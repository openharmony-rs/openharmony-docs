# SideBarOptions

侧边栏的功能选项。

**起始版本：** 18

<!--Device-unnamed-export interface SideBarOptions--><!--Device-unnamed-export interface SideBarOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceNavigation, NavDestinationBuilder, MixMode, GradientAlpha, BackgroundTheme, TitleBarType, SideBarOptions, TitleOptions, GradientBackground } from '@kit.ArkUI';
```

## onChange

```TypeScript
onChange?: Callback<boolean>
```

侧边栏显示隐藏回调。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt;

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarOptions-onChange?: Callback<boolean>--><!--Device-SideBarOptions-onChange?: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sideBarBackground

```TypeScript
sideBarBackground?: ResourceColor
```

设置侧边栏的背景颜色。

**类型：** ResourceColor

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarOptions-sideBarBackground?: ResourceColor--><!--Device-SideBarOptions-sideBarBackground?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sideBarIcon

```TypeScript
sideBarIcon?: Resource | SymbolGlyphModifier
```

侧边栏的展开图标。

**类型：** Resource \| SymbolGlyphModifier

**默认值：** $r('sys.symbol.open_sidebar')

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SideBarOptions-sideBarIcon?: Resource | SymbolGlyphModifier--><!--Device-SideBarOptions-sideBarIcon?: Resource | SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

