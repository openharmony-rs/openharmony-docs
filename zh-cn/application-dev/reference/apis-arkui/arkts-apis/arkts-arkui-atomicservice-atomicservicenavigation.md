# @ohos.atomicservice.AtomicServiceNavigation(This section describes the interfaces used by AtomicServiceNavigation)

## 子组件

可以包含子组件。

从API version 10开始，推荐使用[NavPathStack](../arkts-components/arkts-arkui-navpathstack-c.md)进行页面路由。

## 导入模块

```TypeScript
import { AtomicServiceNavigation, NavDestinationBuilder, MixMode, GradientAlpha, BackgroundTheme, TitleBarType, SideBarOptions, TitleOptions, GradientBackground } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [AtomicServiceNavigation](arkts-arkui-atomicservice-atomicservicenavigation-atomicservicenavigation-s.md) | 作为Page页面的根容器使用，其内部默认包含了标题栏、内容区。其中，内容区在首页默认显示导航内容，在非首页显示NavDestination的子组件，首页和非首页通过路由进行切换。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [GradientBackground](arkts-arkui-atomicservice-atomicservicenavigation-gradientbackground-i.md) | 品牌渐变色选项。 |
| [SideBarOptions](arkts-arkui-atomicservice-atomicservicenavigation-sidebaroptions-i.md) | 侧边栏的功能选项。 |
| [TitleOptions](arkts-arkui-atomicservice-atomicservicenavigation-titleoptions-i.md) | 标题栏选项。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BackgroundTheme](arkts-arkui-atomicservice-atomicservicenavigation-backgroundtheme-e.md) | 导航栏背景底色的可选项。 |
| [GradientAlpha](arkts-arkui-atomicservice-atomicservicenavigation-gradientalpha-e.md) | 渐变色显示区域不透明度的可选项。 |
| [MixMode](arkts-arkui-atomicservice-atomicservicenavigation-mixmode-e.md) | 背景色混合模式的可选项。 |
| [TitleBarType](arkts-arkui-atomicservice-atomicservicenavigation-titlebartype-e.md) | 标题栏类型的可选项，默认值为ROUND_ICON。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [NavDestinationBuilder](arkts-arkui-navdestinationbuilder-t.md) | 用于创建NavDestination组件内容的构建器类型。 |

## 示例

```TypeScript
### 示例1（AtomicServiceNavigation页面布局与渐变色背景）

展示AtomicServiceNavigation的基础样式与渐变色背景。


```

```TypeScript
### 示例2（抽屉样式，宽屏场景下插入自定义布局）

设备宽屏场景（宽度大于600vp）下设置抽屉模式，在标题栏插入自定义布局。


```

```TypeScript
### 示例3（侧边栏使用场景）

设置侧边栏：背景色与内容样式。
```
