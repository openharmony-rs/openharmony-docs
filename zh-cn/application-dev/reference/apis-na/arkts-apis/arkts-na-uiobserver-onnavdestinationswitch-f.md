# onNavDestinationSwitch

## 导入模块

```TypeScript
```

## onNavDestinationSwitch

```TypeScript
export function onNavDestinationSwitch(
    context: UIAbilityContext | UIContext,
    callback: Callback<NavDestinationSwitchInfo>
  ): void
```

监听Navigation的页面切换事件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onNavDestinationSwitch(    context: UIAbilityContext | UIContext,    callback: Callback<NavDestinationSwitchInfo>  ): void--><!--Device-uiObserver-export function onNavDestinationSwitch(    context: UIAbilityContext | UIContext,    callback: Callback<NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) \| [UIContext](arkts-na-arkui-uicontext-uicontext-c.md) | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[NavDestinationSwitchInfo](../../apis-arkui/arkts-apis/arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | 是 | 回调函数。携带NavDestinationSwitchInfo，返回页面切换事件的信息。 |


## onNavDestinationSwitch

```TypeScript
export function onNavDestinationSwitch(
    context: UIAbilityContext | UIContext,
    observerOptions: NavDestinationSwitchObserverOptions,
    callback: Callback<NavDestinationSwitchInfo>
  ): void
```

监听Navigation的页面切换事件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onNavDestinationSwitch(    context: UIAbilityContext | UIContext,    observerOptions: NavDestinationSwitchObserverOptions,    callback: Callback<NavDestinationSwitchInfo>  ): void--><!--Device-uiObserver-export function onNavDestinationSwitch(    context: UIAbilityContext | UIContext,    observerOptions: NavDestinationSwitchObserverOptions,    callback: Callback<NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) \| [UIContext](arkts-na-arkui-uicontext-uicontext-c.md) | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| observerOptions | [NavDestinationSwitchObserverOptions](../../apis-arkui/arkts-apis/arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | 是 | 监听选项。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[NavDestinationSwitchInfo](../../apis-arkui/arkts-apis/arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | 是 | 回调函数。携带NavDestinationSwitchInfo，返回页面切换事件的信息。 |

