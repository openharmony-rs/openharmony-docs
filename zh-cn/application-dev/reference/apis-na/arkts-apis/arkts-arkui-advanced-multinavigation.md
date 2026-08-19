# @ohos.arkui.advanced.MultiNavigation

## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [MultiNavPathStack](arkts-na-arkui-advanced-multinavigation-multinavpathstack-c.md) | 当前，MultiNavigation的路由栈仅支持由使用方自行创建，不支持通过回调方式获取。请勿使用NavDestination的 [onReady](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onready11)等类似事件或接口来获取 NavPathStack并进行栈操作，因为这可能会导致不可预知的问题。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [MultiNavigation](arkts-na-arkui-advanced-multinavigation-multinavigation-s.md) | MultiNavigation({navDestination: PageMapBuilder \| undefined, multiStack: MultiNavPathStack, onNavigationModeChange?: OnNavigationModeChangeCallback, onHomeShowOnTop?: OnHomeShowOnTopCallback}) 创建并初始化MultiNavigation组件。 MultiNavigation组件遵循默认的左起右清栈规则，这意味着从左侧主页点击时，会触发详情页的加载并同时清除右侧所有其他详情页，确保右侧仅展示最新加载的详情页。然而，若在右侧的详情页上再次执行详情页加载操作，系统将不会执行清栈动 作。效果可参见主页跳转详情页效果演示。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SplitPolicy](arkts-na-arkui-advanced-multinavigation-splitpolicy-e.md) | 表示MultiNavigation中页面的类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnHomeShowOnTopCallback](arkts-na-onhomeshowontopcallback-t.md) | 当主页在栈顶显示时触发的回调函数。 |
| [OnNavigationModeChangeCallback](arkts-na-onnavigationmodechangecallback-t.md) | 当MultiNavigation的mode变化时触发的回调函数。 |

