# off_navDestinationSwitch

## off_navDestinationSwitch

```TypeScript
export function off(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    callback?: Callback<NavDestinationSwitchInfo>
  ): void
```

取消监听Navigation的页面切换事件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    callback?: Callback<NavDestinationSwitchInfo>  ): void--><!--Device-uiObserver-export function off(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    callback?: Callback<NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) \| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | 否 | 需要被注销的回调函数。 |


## off_navDestinationSwitch

```TypeScript
export function off(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    observerOptions: NavDestinationSwitchObserverOptions,
    callback?: Callback<NavDestinationSwitchInfo>
  ): void
```

取消监听Navigation的页面切换事件。与[uiObserver.off](arkts-arkui-uiobserver-offnavdestinationupdate-f.md#off_navDestinationUpdate)相比，新增了observerOptions参数，即支持设置监听选项。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    observerOptions: NavDestinationSwitchObserverOptions,    callback?: Callback<NavDestinationSwitchInfo>  ): void--><!--Device-uiObserver-export function off(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    observerOptions: NavDestinationSwitchObserverOptions,    callback?: Callback<NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) \| [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| observerOptions | [NavDestinationSwitchObserverOptions](arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | 是 | 监听选项。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[NavDestinationSwitchInfo](arkts-arkui-uiobserver-navdestinationswitchinfo-i.md)&gt; | 否 | 需要被注销的回调函数。 |

