# @ohos.atomicservice.AtomicServiceNavigation(This section describes the interfaces used by AtomicServiceNavigation)

###### 子组件
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
| [AtomicServiceNavigation(This section describes the interfaces used by AtomicServiceNavigation)](arkts-arkui-atomicservice-atomicservicenavigation-atomicservicenavigation-s.md) | 作为Page页面的根容器使用，其内部默认包含了标题栏、内容区。其中，内容区在首页默认显示导航内容，在非首页显示 NavDestination的子组件，首页和非首页通过路由进行切换。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [GradientBackground(This section describes the interfaces used by AtomicServiceNavigation)](arkts-arkui-atomicservice-atomicservicenavigation-gradientbackground-i.md) | 品牌渐变色选项。 |
| [SideBarOptions(This section describes the interfaces used by AtomicServiceNavigation)](arkts-arkui-atomicservice-atomicservicenavigation-sidebaroptions-i.md) | 侧边栏的功能选项。 |
| [TitleOptions(This section describes the interfaces used by AtomicServiceNavigation)](arkts-arkui-atomicservice-atomicservicenavigation-titleoptions-i.md) | 标题栏选项。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [BackgroundTheme(This section describes the interfaces used by AtomicServiceNavigation)](arkts-arkui-atomicservice-atomicservicenavigation-backgroundtheme-e.md) | 导航栏背景底色的可选项。 |
| [GradientAlpha(This section describes the interfaces used by AtomicServiceNavigation)](arkts-arkui-atomicservice-atomicservicenavigation-gradientalpha-e.md) | 渐变色显示区域不透明度的可选项。 |
| [MixMode(This section describes the interfaces used by AtomicServiceNavigation)](arkts-arkui-atomicservice-atomicservicenavigation-mixmode-e.md) | 背景色混合模式的可选项。 |
| [TitleBarType(This section describes the interfaces used by AtomicServiceNavigation)](arkts-arkui-atomicservice-atomicservicenavigation-titlebartype-e.md) | 标题栏类型的可选项，默认值为ROUND_ICON。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [NavDestinationBuilder(This section describes the interfaces used by AtomicServiceNavigation)](arkts-arkui-navdestinationbuilder-t.md) | 用于创建NavDestination组件内容的构建器类型。 |
