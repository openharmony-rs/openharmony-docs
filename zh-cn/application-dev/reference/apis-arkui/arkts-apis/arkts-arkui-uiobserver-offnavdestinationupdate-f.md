# offNavDestinationUpdate

## offNavDestinationUpdate

```TypeScript
export function offNavDestinationUpdate(
    options: NavDestinationSwitchObserverOptions, 
    callback?: Callback<NavDestinationInfo>
  ): void
```

取消监听NavDestination组件的状态变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function offNavDestinationUpdate(    options: NavDestinationSwitchObserverOptions,     callback?: Callback<NavDestinationInfo>  ): void--><!--Device-uiObserver-export function offNavDestinationUpdate(    options: NavDestinationSwitchObserverOptions,     callback?: Callback<NavDestinationInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定监听的Navigation的id。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationInfo&gt; | 否 | 回调函数。返回当前的NavDestination组件状态。 |


## offNavDestinationUpdate

```TypeScript
export function offNavDestinationUpdate(callback?: Callback<NavDestinationInfo>): void
```

取消监听NavDestination组件的状态变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiObserver-export function offNavDestinationUpdate(callback?: Callback<NavDestinationInfo>): void--><!--Device-uiObserver-export function offNavDestinationUpdate(callback?: Callback<NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;NavDestinationInfo&gt; | 否 | 回调函数。返回当前的NavDestination组件状态。 |

