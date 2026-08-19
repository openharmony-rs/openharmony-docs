# onNavDestinationUpdate

## 导入模块

```TypeScript
```

## onNavDestinationUpdate

```TypeScript
export function onNavDestinationUpdate(
    options: NavDestinationSwitchObserverOptions, 
    callback: Callback<NavDestinationInfo>
  ): void
```

监听NavDestination组件的状态变化。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onNavDestinationUpdate(    options: NavDestinationSwitchObserverOptions,     callback: Callback<NavDestinationInfo>  ): void--><!--Device-uiObserver-export function onNavDestinationUpdate(    options: NavDestinationSwitchObserverOptions,     callback: Callback<NavDestinationInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [NavDestinationSwitchObserverOptions](../../apis-arkui/arkts-apis/arkts-arkui-uiobserver-navdestinationswitchobserveroptions-i.md) | 是 | 指定监听的Navigation的id。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;NavDestinationInfo&gt; | 是 | 回调函数。返回当前的NavDestination组件状态。 |


## onNavDestinationUpdate

```TypeScript
export function onNavDestinationUpdate(callback: Callback<NavDestinationInfo>): void
```

监听NavDestination组件的状态变化。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function onNavDestinationUpdate(callback: Callback<NavDestinationInfo>): void--><!--Device-uiObserver-export function onNavDestinationUpdate(callback: Callback<NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;NavDestinationInfo&gt; | 是 | 回调函数。返回当前的NavDestination组件状态。 |

