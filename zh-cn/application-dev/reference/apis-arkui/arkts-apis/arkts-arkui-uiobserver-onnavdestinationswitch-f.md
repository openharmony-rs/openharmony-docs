# onNavDestinationSwitch

## onNavDestinationSwitch

```TypeScript
export function onNavDestinationSwitch(
    context: UIAbilityContext | UIContext,
    callback: Callback<NavDestinationSwitchInfo>
  ): void
```

监听Navigation的页面切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onNavDestinationSwitch(    context: UIAbilityContext | UIContext,    callback: Callback<NavDestinationSwitchInfo>  ): void--><!--Device-uiObserver-export function onNavDestinationSwitch(    context: UIAbilityContext | UIContext,    callback: Callback<NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| UIContext | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationSwitchInfo&gt; | 是 | 回调函数。携带NavDestinationSwitchInfo，返回页面切换事件的信息。 |


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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onNavDestinationSwitch(    context: UIAbilityContext | UIContext,    observerOptions: NavDestinationSwitchObserverOptions,    callback: Callback<NavDestinationSwitchInfo>  ): void--><!--Device-uiObserver-export function onNavDestinationSwitch(    context: UIAbilityContext | UIContext,    observerOptions: NavDestinationSwitchObserverOptions,    callback: Callback<NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| UIContext | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| observerOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 监听选项。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationSwitchInfo&gt; | 是 | 回调函数。携带NavDestinationSwitchInfo，返回页面切换事件的信息。 |

