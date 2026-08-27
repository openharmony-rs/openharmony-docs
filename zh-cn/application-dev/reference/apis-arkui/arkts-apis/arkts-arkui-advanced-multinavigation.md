# @ohos.arkui.advanced.MultiNavigation

## 导入模块

```TypeScript
import { SplitPolicy, MultiNavigation, MultiNavPathStack } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [MultiNavPathStack](arkts-arkui-arkui-advanced-multinavigation-multinavpathstack-c.md) | MultiNavigation的路由栈仅支持由使用方自行创建，不支持通过回调方式获取。请勿使用NavDestination的 onReady等类似事件或接口来获取NavPathStack并进行栈操作，因为这可能会导致不可预知的问题。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [MultiNavigation](arkts-arkui-arkui-advanced-multinavigation-multinavigation-s.md) | MultiNavigation是一个支持分栏导航的组件，提供多层页面栈管理能力，通过MultiNavPathStack统一管理主页、详情页、全屏页等不同类型页面的导航栈。 支持左起右清栈等智能路由策略，适用于平板、折叠屏等大尺寸设备的复杂导航场景，能够优化页面跳转体验、提升用户操作效率。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SplitPolicy](arkts-arkui-arkui-advanced-multinavigation-splitpolicy-e.md) | 表示MultiNavigation中页面的类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [NavDestinationBuildFunction](arkts-arkui-navdestinationbuildfunction-t.md) | MultiNavigation用以加载NavDestination的方法。 |
| [OnHomeShowOnTopCallback](arkts-arkui-onhomeshowontopcallback-t.md) | 当主页在栈顶显示时触发的回调函数。 |
| [OnNavigationModeChangeCallback](arkts-arkui-onnavigationmodechangecallback-t.md) | 当MultiNavigation的mode变化时触发的回调函数。 |
