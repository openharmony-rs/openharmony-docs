# off

## off('navDestinationUpdate')

```TypeScript
export function off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<NavDestinationInfo>): void
```

取消监听NavDestination组件的状态变化。与[uiObserver.off]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_相比，新增了options参数，即支持指定监听的Navigation的id。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<NavDestinationInfo>): void--><!--Device-uiObserver-export function off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| options | { navigationId: ResourceStr } | 是 | 指定监听的Navigation的id。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationInfo&gt; | 否 | 回调函数。返回当前的NavDestination组件状态。 |


## off('navDestinationUpdate')

```TypeScript
export function off(type: 'navDestinationUpdate', callback?: Callback<NavDestinationInfo>): void
```

取消监听NavDestination组件的状态变化。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'navDestinationUpdate', callback?: Callback<NavDestinationInfo>): void--><!--Device-uiObserver-export function off(type: 'navDestinationUpdate', callback?: Callback<NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationInfo&gt; | 否 | 回调函数。返回当前的NavDestination组件状态。 |


## off('scrollEvent')

```TypeScript
export function off(type: 'scrollEvent', options: ObserverOptions, callback?: Callback<ScrollEventInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'scrollEvent', options: ObserverOptions, callback?: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function off(type: 'scrollEvent', options: ObserverOptions, callback?: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to remove the listener for. Must be 'scrollEvent'. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The options object. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ScrollEventInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type and scroll ID will be removed. |


## off('scrollEvent')

```TypeScript
export function off(type: 'scrollEvent', callback?: Callback<ScrollEventInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'scrollEvent', callback?: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function off(type: 'scrollEvent', callback?: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to remove the listener for. Must be 'scrollEvent'. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ScrollEventInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |


## off('routerPageUpdate')

```TypeScript
export function off(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback?: Callback<RouterPageInfo>): void
```

取消监听router中page页面的状态变化。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback?: Callback<RouterPageInfo>): void--><!--Device-uiObserver-export function off(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback?: Callback<RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | 是 | 监听事件，固定为'routerPageUpdate'，即router中page页面的状态变化。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| UIContext | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RouterPageInfo&gt; | 否 | 需要被注销的回调函数。 |


## off('densityUpdate')

```TypeScript
export function off(type: 'densityUpdate', context: UIContext, callback?: Callback<DensityInfo>): void
```

取消监听屏幕像素密度的变化。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'densityUpdate', context: UIContext, callback?: Callback<DensityInfo>): void--><!--Device-uiObserver-export function off(type: 'densityUpdate', context: UIContext, callback?: Callback<DensityInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'densityUpdate' | 是 | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DensityInfo&gt; | 否 | 需要被注销的回调函数。若不指定具体的回调函数，则注销指定UIContext下所有densityUpdate事件监听。 |


## off('willDraw')

```TypeScript
export function off(type: 'willDraw', context: UIContext, callback?: Callback<void>): void
```

取消监听每一帧绘制指令下发情况。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'willDraw', context: UIContext, callback?: Callback<void>): void--><!--Device-uiObserver-export function off(type: 'willDraw', context: UIContext, callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willDraw' | 是 | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 需要被注销的回调函数。 |


## off('didLayout')

```TypeScript
export function off(type: 'didLayout', context: UIContext, callback?: Callback<void>): void
```

取消监听每一帧布局完成情况。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'didLayout', context: UIContext, callback?: Callback<void>): void--><!--Device-uiObserver-export function off(type: 'didLayout', context: UIContext, callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 上下文信息，用以指定监听页面的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 需要被注销的回调函数。 |


## off('tabContentUpdate')

```TypeScript
export function off(type: 'tabContentUpdate', options: ObserverOptions, callback?: Callback<TabContentInfo>): void
```

取消监听指定Tabs组件id的TabContent页面切换事件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'tabContentUpdate', options: ObserverOptions, callback?: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function off(type: 'tabContentUpdate', options: ObserverOptions, callback?: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定监听的Tabs组件的id。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TabContentInfo&gt; | 否 | 需要被注销的回调函数。 |


## off('tabContentUpdate')

```TypeScript
export function off(type: 'tabContentUpdate', callback?: Callback<TabContentInfo>): void
```

取消监听TabContent页面的切换事件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(type: 'tabContentUpdate', callback?: Callback<TabContentInfo>): void--><!--Device-uiObserver-export function off(type: 'tabContentUpdate', callback?: Callback<TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;TabContentInfo&gt; | 否 | 需要被注销的回调函数。 |


## off('navDestinationSwitch')

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

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    callback?: Callback<NavDestinationSwitchInfo>  ): void--><!--Device-uiObserver-export function off(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    callback?: Callback<NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| UIContext | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationSwitchInfo&gt; | 否 | 需要被注销的回调函数。 |


## off('navDestinationSwitch')

```TypeScript
export function off(
    type: 'navDestinationSwitch',
    context: UIAbilityContext | UIContext,
    observerOptions: NavDestinationSwitchObserverOptions,
    callback?: Callback<NavDestinationSwitchInfo>
  ): void
```

取消监听Navigation的页面切换事件。与[uiObserver.off]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_相比，新增了observerOptions参数，即支持设置监听选项。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function off(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    observerOptions: NavDestinationSwitchObserverOptions,    callback?: Callback<NavDestinationSwitchInfo>  ): void--><!--Device-uiObserver-export function off(    type: 'navDestinationSwitch',    context: UIAbilityContext | UIContext,    observerOptions: NavDestinationSwitchObserverOptions,    callback?: Callback<NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| context | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| UIContext | 是 | 上下文信息，用以指定监听页面切换事件的范围。 |
| observerOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 监听选项。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationSwitchInfo&gt; | 否 | 需要被注销的回调函数。 |

