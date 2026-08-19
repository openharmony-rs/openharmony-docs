# GradientBackground

品牌渐变色选项。

**起始版本：** 18

<!--Device-unnamed-export interface GradientBackground--><!--Device-unnamed-export interface GradientBackground-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceNavigation, NavDestinationBuilder, MixMode, GradientAlpha, BackgroundTheme, TitleBarType, SideBarOptions, TitleOptions, GradientBackground } from '@kit.ArkUI';
```

## alpha

```TypeScript
alpha?: GradientAlpha
```

设置渐变色显示区域的不透明度。

**类型：** [GradientAlpha](arkts-arkui-atomicservice-atomicservicenavigation-gradientalpha-e.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GradientBackground-alpha?: GradientAlpha--><!--Device-GradientBackground-alpha?: GradientAlpha-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundTheme

```TypeScript
backgroundTheme?: BackgroundTheme
```

导航栏背景底色。

**类型：** [BackgroundTheme](arkts-arkui-atomicservice-atomicservicenavigation-backgroundtheme-e.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GradientBackground-backgroundTheme?: BackgroundTheme--><!--Device-GradientBackground-backgroundTheme?: BackgroundTheme-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mixMode

```TypeScript
mixMode?: MixMode
```

同时设置primaryColor和secondaryColor时此参数生效。表示双色渐变下两种颜色的融合方式。

**类型：** [MixMode](arkts-arkui-atomicservice-atomicservicenavigation-mixmode-e.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GradientBackground-mixMode?: MixMode--><!--Device-GradientBackground-mixMode?: MixMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryColor

```TypeScript
primaryColor: ResourceColor
```

单色渐变色彩值和双色渐变第一色彩值。

**类型：** ResourceColor

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GradientBackground-primaryColor: ResourceColor--><!--Device-GradientBackground-primaryColor: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryColor

```TypeScript
secondaryColor?: ResourceColor
```

双色渐变色第二色彩值。

**类型：** ResourceColor

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GradientBackground-secondaryColor?: ResourceColor--><!--Device-GradientBackground-secondaryColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

