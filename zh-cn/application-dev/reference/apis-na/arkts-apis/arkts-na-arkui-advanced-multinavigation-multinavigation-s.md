# MultiNavigation

MultiNavigation({navDestination: PageMapBuilder | undefined, multiStack: MultiNavPathStack, onNavigationModeChange?: OnNavigationModeChangeCallback, onHomeShowOnTop?: OnHomeShowOnTopCallback}) 创建并初始化MultiNavigation组件。 MultiNavigation组件遵循默认的左起右清栈规则，这意味着从左侧主页点击时，会触发详情页的加载并同时清除右侧所有其他详情页，确保右侧仅展示最新加载的详情页。然而，若在右侧的详情页上再次执行详情页加载操作，系统将不会执行清栈动 作。效果可参见主页跳转详情页效果演示。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare struct MultiNavigation--><!--Device-unnamed-export declare struct MultiNavigation-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
@Builder
  build(): void
```

The method to build multiNavigation.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MultiNavigation-@Builder  build(): void--><!--Device-MultiNavigation-@Builder  build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## multiStack

```TypeScript
@State
  multiStack: MultiNavPathStack
```

设置路由栈。

**类型：** [MultiNavPathStack](arkts-na-arkui-advanced-multinavigation-multinavpathstack-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MultiNavigation-@State  multiStack: MultiNavPathStack--><!--Device-MultiNavigation-@State  multiStack: MultiNavPathStack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## navDestination

```TypeScript
@BuilderParam
  navDestination: PageMapBuilder | undefined
```

设置加载目标页面的路由规则。 取值为undefined时，不会加载。

**类型：** PageMapBuilder \| undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MultiNavigation-@BuilderParam  navDestination: PageMapBuilder | undefined--><!--Device-MultiNavigation-@BuilderParam  navDestination: PageMapBuilder | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHomeShowOnTop

```TypeScript
onHomeShowOnTop?: OnHomeShowOnTopCallback
```

设置主页处于栈顶时的回调。

**类型：** [OnHomeShowOnTopCallback](arkts-na-onhomeshowontopcallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MultiNavigation-onHomeShowOnTop?: OnHomeShowOnTopCallback--><!--Device-MultiNavigation-onHomeShowOnTop?: OnHomeShowOnTopCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onNavigationModeChange

```TypeScript
onNavigationModeChange?: OnNavigationModeChangeCallback
```

设置MultiNavigation模式变更时的回调。

**类型：** [OnNavigationModeChangeCallback](arkts-na-onnavigationmodechangecallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MultiNavigation-onNavigationModeChange?: OnNavigationModeChangeCallback--><!--Device-MultiNavigation-onNavigationModeChange?: OnNavigationModeChangeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

