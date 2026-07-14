# @ohos.arkui.advanced.MultiNavigation

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [MultiNavPathStack](arkts-arkui-multinavpathstack-c.md) | 当前，MultiNavigation的路由栈仅支持由使用方自行创建，不支持通过回调方式获取。请勿使用[NavDestination](../arkts-components/arkts-arkui-navdestination.md)的[onReady](NavDestinationAttribute#onReady)等类似事件或接口来获取NavPathStack并进行栈操作，因为这可能会导致不可预知的问题。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [MultiNavigation](arkts-arkui-multinavigation-s.md) | MultiNavigation用于在大尺寸设备上分栏显示、进行路由跳转。@link NavPathStack#getParent}、&gt; [setInterception](../arkts-components/arkts-arkui-navpathstack-c.md#setinterception-1)、&gt; [pushDestination](../arkts-components/arkts-arkui-navpathstack-c.md#pushdestination-1)等)，可能会发生无法预期的问题。&gt; MultiNavigation在深层嵌套场景下，可能存在路由动效异常的问题。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SplitPolicy](arkts-arkui-splitpolicy-e.md) | 表示MultiNavigation中页面的类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [NavDestinationBuildFunction](arkts-arkui-navdestinationbuildfunction-t.md) | MultiNavigation用以加载NavDestination的方法。 |
| [OnHomeShowOnTopCallback](arkts-arkui-onhomeshowontopcallback-t.md) | 当主页在栈顶显示时触发的回调函数。 |
| [OnNavigationModeChangeCallback](arkts-arkui-onnavigationmodechangecallback-t.md) | 当MultiNavigation的mode变化时触发的回调函数。 |

