# UIObserver

注册回调来观察ArkUI的行为。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class UIObserver--><!--Device-unnamed-export declare class UIObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addGlobalGestureListener

```TypeScript
addGlobalGestureListener(type: GestureListenerType,
      option: GestureObserverConfigs, callback: GestureListenerCallback): void
```

注册一个用于监听界面中的手势触发的监听器

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-addGlobalGestureListener(type: GestureListenerType,      option: GestureObserverConfigs, callback: GestureListenerCallback): void--><!--Device-UIObserver-addGlobalGestureListener(type: GestureListenerType,      option: GestureObserverConfigs, callback: GestureListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要监听的手势类型 |
| option | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 全局监听的选项 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 监听回调函数 |

## offAfterPanEnd

```TypeScript
offAfterPanEnd(callback?: PanListenerCallback): void
```

删除无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offAfterPanEnd(callback?: PanListenerCallback): void--><!--Device-UIObserver-offAfterPanEnd(callback?: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要移除的回调函数。如果未提供该参数，则将移除给定事件类型的所有回调函数。 |

## offAfterPanStart

```TypeScript
offAfterPanStart(callback?: PanListenerCallback): void
```

删除无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offAfterPanStart(callback?: PanListenerCallback): void--><!--Device-UIObserver-offAfterPanStart(callback?: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要移除的回调函数。如果未提供该参数，则将移除给定事件类型的所有回调函数。 |

## offBeforePanEnd

```TypeScript
offBeforePanEnd(callback?: PanListenerCallback): void
```

删除无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offBeforePanEnd(callback?: PanListenerCallback): void--><!--Device-UIObserver-offBeforePanEnd(callback?: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要移除的回调函数。如果未提供该参数，则将移除给定事件类型的所有回调函数。 |

## offBeforePanStart

```TypeScript
offBeforePanStart(callback?: PanListenerCallback): void
```

移除无感监听回调函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offBeforePanStart(callback?: PanListenerCallback): void--><!--Device-UIObserver-offBeforePanStart(callback?: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要移除的回调函数。如果未提供该参数，则将移除给定事件类型的所有回调函数。 |

## offDensityUpdate

```TypeScript
offDensityUpdate(callback?: Callback<observer.DensityInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offDensityUpdate(callback?: Callback<observer.DensityInfo>): void--><!--Device-UIObserver-offDensityUpdate(callback?: Callback<observer.DensityInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.DensityInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## offDidClick

```TypeScript
offDidClick(callback?: ClickEventListenerCallback): void
```

解注册无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offDidClick(callback?: ClickEventListenerCallback): void--><!--Device-UIObserver-offDidClick(callback?: ClickEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要移除的回调函数。如果未提供该参数，则将移除给定事件类型的所有回调函数。 |

## offDidLayout

```TypeScript
offDidLayout(callback?: Callback<void>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offDidLayout(callback?: Callback<void>): void--><!--Device-UIObserver-offDidLayout(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## offDidTap

```TypeScript
offDidTap(callback?: GestureEventListenerCallback): void
```

移除无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offDidTap(callback?: GestureEventListenerCallback): void--><!--Device-UIObserver-offDidTap(callback?: GestureEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要移除的回调函数。如果未提供该参数，则将移除给定事件类型的所有回调函数。 |

## offNavDestinationSizeChange

```TypeScript
offNavDestinationSizeChange(callback?: Callback<observer.NavDestinationInfo>): void
```

移除使用onNavDestinationSizeChange接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offNavDestinationSizeChange(callback?: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-offNavDestinationSizeChange(callback?: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationInfo&gt; | 否 | 需要被移除的回调函数。不传参数时，移除所有回调函数。 |

## offNavDestinationSizeChangeByUniqueId

```TypeScript
offNavDestinationSizeChangeByUniqueId(navigationUniqueId: int, callback?: Callback<observer.NavDestinationInfo>): void
```

移除使用onNavDestinationSizeChangeByUniqueId接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offNavDestinationSizeChangeByUniqueId(navigationUniqueId: int, callback?: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-offNavDestinationSizeChangeByUniqueId(navigationUniqueId: int, callback?: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navigationUniqueId | int | 是 | 希望监听的NavDestination所属的Navigation的唯一ID，可以通过\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值限定为整数。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationInfo&gt; | 否 | 需要被删除的callback，如果没提供删除所有注册的回调。 |

## offNavDestinationSwitch

```TypeScript
offNavDestinationSwitch(callback?: Callback<observer.NavDestinationSwitchInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offNavDestinationSwitch(callback?: Callback<observer.NavDestinationSwitchInfo>): void--><!--Device-UIObserver-offNavDestinationSwitch(callback?: Callback<observer.NavDestinationSwitchInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationSwitchInfo&gt; | 否 | The callback function to remove.If not provided, all callbacks for the given event type will be removed. |

## offNavDestinationSwitch

```TypeScript
offNavDestinationSwitch(
    observerOptions: observer.NavDestinationSwitchObserverOptions,
    callback?: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offNavDestinationSwitch(    observerOptions: observer.NavDestinationSwitchObserverOptions,    callback?: Callback<observer.NavDestinationSwitchInfo>  ): void--><!--Device-UIObserver-offNavDestinationSwitch(    observerOptions: observer.NavDestinationSwitchObserverOptions,    callback?: Callback<observer.NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observerOptions | observer.NavDestinationSwitchObserverOptions | 是 | Options. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationSwitchInfo&gt; | 否 | The callback function to remove.If not provided, all callbacks for the given event type will be removed. |

## offNavDestinationUpdate

```TypeScript
offNavDestinationUpdate(
    options: observer.NavDestinationSwitchObserverOptions,
    callback?: Callback<observer.NavDestinationInfo>
    ): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offNavDestinationUpdate(    options: observer.NavDestinationSwitchObserverOptions,    callback?: Callback<observer.NavDestinationInfo>    ): void--><!--Device-UIObserver-offNavDestinationUpdate(    options: observer.NavDestinationSwitchObserverOptions,    callback?: Callback<observer.NavDestinationInfo>    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | observer.NavDestinationSwitchObserverOptions | 是 | The options object. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationInfo&gt; | 否 | The callback function to remove.If not provided, all callbacks for the given event type and navigation ID will be removed. |

## offNavDestinationUpdate

```TypeScript
offNavDestinationUpdate(callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offNavDestinationUpdate(callback?: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-offNavDestinationUpdate(callback?: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationInfo&gt; | 否 | The callback function to remove.If not provided, all callbacks for the given event type will be removed. |

## offNavDestinationUpdateByUniqueId

```TypeScript
offNavDestinationUpdateByUniqueId(navigationUniqueId: int, callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offNavDestinationUpdateByUniqueId(navigationUniqueId: int, callback?: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-offNavDestinationUpdateByUniqueId(navigationUniqueId: int, callback?: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navigationUniqueId | int | 是 | The uniqueId of the navigation. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationInfo&gt; | 否 | The callback function to remove. If not provided,all callbacks for the given event type will be removed. |

## offNodeRenderState

```TypeScript
offNodeRenderState(nodeIdentity: NodeIdentity, callback?: NodeRenderStateChangeCallback): void
```

删除节点渲染状态监听回调

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offNodeRenderState(nodeIdentity: NodeIdentity, callback?: NodeRenderStateChangeCallback): void--><!--Device-UIObserver-offNodeRenderState(nodeIdentity: NodeIdentity, callback?: NodeRenderStateChangeCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nodeIdentity | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The identity of the target node |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要移除的回调函数。如果未提供该参数，则将移除给定事件类型的所有回调函数。 |

## offRouterPageSizeChange

```TypeScript
offRouterPageSizeChange(callback?: Callback<observer.RouterPageInfo>): void
```

移除使用onRouterPageSizeChange接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offRouterPageSizeChange(callback?: Callback<observer.RouterPageInfo>): void--><!--Device-UIObserver-offRouterPageSizeChange(callback?: Callback<observer.RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.RouterPageInfo&gt; | 否 | 需要被移除的回调函数。不传参数时，移除所有回调函数。 |

## offRouterPageUpdate

```TypeScript
offRouterPageUpdate(callback?: Callback<observer.RouterPageInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offRouterPageUpdate(callback?: Callback<observer.RouterPageInfo>): void--><!--Device-UIObserver-offRouterPageUpdate(callback?: Callback<observer.RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.RouterPageInfo&gt; | 否 | The callback function to remove. If not provided,all callbacks for the given event type will be removed. |

## offScrollEvent

```TypeScript
offScrollEvent(options: observer.ObserverOptions, callback?: Callback<observer.ScrollEventInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offScrollEvent(options: observer.ObserverOptions, callback?: Callback<observer.ScrollEventInfo>): void--><!--Device-UIObserver-offScrollEvent(options: observer.ObserverOptions, callback?: Callback<observer.ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.ScrollEventInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type and scroll ID will be removed. |

## offScrollEvent

```TypeScript
offScrollEvent(callback?: Callback<observer.ScrollEventInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offScrollEvent(callback?: Callback<observer.ScrollEventInfo>): void--><!--Device-UIObserver-offScrollEvent(callback?: Callback<observer.ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.ScrollEventInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## offSwiperContentUpdate

```TypeScript
offSwiperContentUpdate(callback?: Callback<SwiperContentInfo>): void
```

取消监听Swiper内容的切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offSwiperContentUpdate(callback?: Callback<SwiperContentInfo>): void--><!--Device-UIObserver-offSwiperContentUpdate(callback?: Callback<SwiperContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SwiperContentInfo&gt; | 否 | 需要被注销的回调函数。不传参数时，取消该Swiper上所有的监听回调。 |

## offSwiperContentUpdate

```TypeScript
offSwiperContentUpdate(config: observer.ObserverOptions, callback?: Callback<SwiperContentInfo>): void
```

取消通过Swiper组件id监听的Swiper内容切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offSwiperContentUpdate(config: observer.ObserverOptions, callback?: Callback<SwiperContentInfo>): void--><!--Device-UIObserver-offSwiperContentUpdate(config: observer.ObserverOptions, callback?: Callback<SwiperContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | observer.ObserverOptions | 是 | 指定监听的Swiper组件信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SwiperContentInfo&gt; | 否 | 需要被注销的回调函数。不传参数时，取消该Swiper上所有的监听回调。 |

## offTabChange

```TypeScript
offTabChange(config: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void
```

移除之前通过 \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_ 注册的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offTabChange(config: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-offTabChange(config: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | observer.ObserverOptions | 是 | 选项对象。包含监听的tabs组件ID。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TabContentInfo&gt; | 否 | 要移除的回调函数。如果未提供该参数，则将移除该tabs id的所有'tabChange'无感监听回调函数。 |

## offTabChange

```TypeScript
offTabChange(callback?: Callback<observer.TabContentInfo>): void
```

移除之前通过 \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_ 注册的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offTabChange(callback?: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-offTabChange(callback?: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TabContentInfo&gt; | 否 | 要移除的回调函数。如果未提供该参数，则将移除所有tabs的所有'tabChange'无感监听回调函数。 |

## offTabContentUpdate

```TypeScript
offTabContentUpdate(options: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offTabContentUpdate(options: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-offTabContentUpdate(options: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TabContentInfo&gt; | 否 | The callback function to remove. If not provided,all callbacks for the given event type and Tabs ID will be removed. |

## offTabContentUpdate

```TypeScript
offTabContentUpdate(callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offTabContentUpdate(callback?: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-offTabContentUpdate(callback?: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TabContentInfo&gt; | 否 | The callback function to remove. If not provided,all callbacks for the given event type and Tabs ID will be removed. |

## offTextChange

```TypeScript
offTextChange(callback?: Callback<observer.TextChangeEventInfo>): void
```

删除以前使用\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_注册的回调函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offTextChange(callback?: Callback<observer.TextChangeEventInfo>): void--><!--Device-UIObserver-offTextChange(callback?: Callback<observer.TextChangeEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TextChangeEventInfo&gt; | 否 | 要删除的回调函数。如果不提供，将删除给定事件类型的所有回调。 |

## offTextChange

```TypeScript
offTextChange(identity: observer.ObserverOptions, callback?: Callback<observer.TextChangeEventInfo>): void
```

删除以前使用\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_注册的回调函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offTextChange(identity: observer.ObserverOptions, callback?: Callback<observer.TextChangeEventInfo>): void--><!--Device-UIObserver-offTextChange(identity: observer.ObserverOptions, callback?: Callback<observer.TextChangeEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| identity | observer.ObserverOptions | 是 | 身份选项。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TextChangeEventInfo&gt; | 否 | 要删除的回调函数。如果不提供，将删除给定事件类型的所有回调。 |

## offWillClick

```TypeScript
offWillClick(callback?: ClickEventListenerCallback): void
```

解注册点击事件无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offWillClick(callback?: ClickEventListenerCallback): void--><!--Device-UIObserver-offWillClick(callback?: ClickEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要移除的回调函数。如果未提供该参数，则将移除给定事件类型的所有回调函数。 |

## offWillDraw

```TypeScript
offWillDraw(callback?: Callback<void>): void
```

Removes a callback function that was previously registered with \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offWillDraw(callback?: Callback<void>): void--><!--Device-UIObserver-offWillDraw(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## offWillTap

```TypeScript
offWillTap(callback?: GestureEventListenerCallback): void
```

删除无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offWillTap(callback?: GestureEventListenerCallback): void--><!--Device-UIObserver-offWillTap(callback?: GestureEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要移除的回调函数。如果未提供该参数，则将移除给定事件类型的所有回调函数。 |

## offWindowSizeLayoutBreakpointChange

```TypeScript
offWindowSizeLayoutBreakpointChange(callback?: Callback<observer.WindowSizeLayoutBreakpointInfo>): void
```

移除之前注册的窗口大小布局断点更改的回调函数。 如果没有提供回调，则将删除指定上下文的所有回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-offWindowSizeLayoutBreakpointChange(callback?: Callback<observer.WindowSizeLayoutBreakpointInfo>): void--><!--Device-UIObserver-offWindowSizeLayoutBreakpointChange(callback?: Callback<observer.WindowSizeLayoutBreakpointInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.WindowSizeLayoutBreakpointInfo&gt; | 否 | 要删除的特定回调函数。如果未提供，则将删除给定事件类型和上下文的所有回调。 |

## onAfterPanEnd

```TypeScript
onAfterPanEnd(callback: PanListenerCallback): void
```

注册无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onAfterPanEnd(callback: PanListenerCallback): void--><!--Device-UIObserver-onAfterPanEnd(callback: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 无感监听回调函数 |

## onAfterPanStart

```TypeScript
onAfterPanStart(callback: PanListenerCallback): void
```

注册无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onAfterPanStart(callback: PanListenerCallback): void--><!--Device-UIObserver-onAfterPanStart(callback: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 滑动手势无感监听回调函数 |

## onBeforePanEnd

```TypeScript
onBeforePanEnd(callback: PanListenerCallback): void
```

注册滑动手势的无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onBeforePanEnd(callback: PanListenerCallback): void--><!--Device-UIObserver-onBeforePanEnd(callback: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 滑动手势无感监听回调函数 |

## onBeforePanStart

```TypeScript
onBeforePanStart(callback: PanListenerCallback): void
```

注册无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onBeforePanStart(callback: PanListenerCallback): void--><!--Device-UIObserver-onBeforePanStart(callback: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 监听滑动手势事件的无感监听回调函数 |

## onDensityUpdate

```TypeScript
onDensityUpdate(callback: Callback<observer.DensityInfo>): void
```

注册回调函数，在屏幕密度变化时调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onDensityUpdate(callback: Callback<observer.DensityInfo>): void--><!--Device-UIObserver-onDensityUpdate(callback: Callback<observer.DensityInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.DensityInfo&gt; | 是 | The callback function to be called when the screen density is updated. |

## onDidClick

```TypeScript
onDidClick(callback: ClickEventListenerCallback): void
```

注册一个在点击事件触发后执行的回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onDidClick(callback: ClickEventListenerCallback): void--><!--Device-UIObserver-onDidClick(callback: ClickEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 无感监听回调函数 |

## onDidLayout

```TypeScript
onDidLayout(callback: Callback<void>): void
```

注册回调函数，在布局完成时调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onDidLayout(callback: Callback<void>): void--><!--Device-UIObserver-onDidLayout(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | The callback function to be called when the layout is done. |

## onDidTap

```TypeScript
onDidTap(callback: GestureEventListenerCallback): void
```

注册无感监听函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onDidTap(callback: GestureEventListenerCallback): void--><!--Device-UIObserver-onDidTap(callback: GestureEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 注册无感监听回调函数 |

## onNavDestinationSizeChange

```TypeScript
onNavDestinationSizeChange(callback: Callback<observer.NavDestinationInfo>): void
```

注册监听回调函数，当可见的NavDestination大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onNavDestinationSizeChange(callback: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-onNavDestinationSizeChange(callback: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationInfo&gt; | 是 | 回调函数。携带NavDestinationInfo，返回NavDestination的信息。 |

## onNavDestinationSizeChangeByUniqueId

```TypeScript
onNavDestinationSizeChangeByUniqueId(navigationUniqueId: int, callback: Callback<observer.NavDestinationInfo>): void
```

注册监听回调函数，当属于指定Navigation的可见NavDestination的大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onNavDestinationSizeChangeByUniqueId(navigationUniqueId: int, callback: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-onNavDestinationSizeChangeByUniqueId(navigationUniqueId: int, callback: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navigationUniqueId | int | 是 | 希望监听NavDestination所属的Navigation的唯一ID，可以通过\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 获取。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值限定为整数。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationInfo&gt; | 是 | 回调函数。携带NavDestinationInfo，返回NavDestination的信息。 |

## onNavDestinationSwitch

```TypeScript
onNavDestinationSwitch(callback: Callback<observer.NavDestinationSwitchInfo>): void
```

监听Navigation的页面切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onNavDestinationSwitch(callback: Callback<observer.NavDestinationSwitchInfo>): void--><!--Device-UIObserver-onNavDestinationSwitch(callback: Callback<observer.NavDestinationSwitchInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationSwitchInfo&gt; | 是 | The callback function to be called when the navigation switched to a new navDestination. |

## onNavDestinationSwitch

```TypeScript
onNavDestinationSwitch(
    observerOptions: observer.NavDestinationSwitchObserverOptions,
    callback: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

监听Navigation的页面切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onNavDestinationSwitch(    observerOptions: observer.NavDestinationSwitchObserverOptions,    callback: Callback<observer.NavDestinationSwitchInfo>  ): void--><!--Device-UIObserver-onNavDestinationSwitch(    observerOptions: observer.NavDestinationSwitchObserverOptions,    callback: Callback<observer.NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observerOptions | observer.NavDestinationSwitchObserverOptions | 是 | Options. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationSwitchInfo&gt; | 是 | The callback function to be called when the navigation switched to a new navDestination. |

## onNavDestinationUpdate

```TypeScript
onNavDestinationUpdate(
    options: observer.NavDestinationSwitchObserverOptions,
    callback: Callback<observer.NavDestinationInfo>
    ): void
```

监听NavDestination组件的状态变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onNavDestinationUpdate(    options: observer.NavDestinationSwitchObserverOptions,    callback: Callback<observer.NavDestinationInfo>    ): void--><!--Device-UIObserver-onNavDestinationUpdate(    options: observer.NavDestinationSwitchObserverOptions,    callback: Callback<observer.NavDestinationInfo>    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | observer.NavDestinationSwitchObserverOptions | 是 | The options object. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationInfo&gt; | 是 | The callback function to be called when the navigation destination is updated. |

## onNavDestinationUpdate

```TypeScript
onNavDestinationUpdate(callback: Callback<observer.NavDestinationInfo>): void
```

监听NavDestination组件的状态变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onNavDestinationUpdate(callback: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-onNavDestinationUpdate(callback: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationInfo&gt; | 是 | The callback function to be called when the navigation destination is updated. |

## onNavDestinationUpdateByUniqueId

```TypeScript
onNavDestinationUpdateByUniqueId(navigationUniqueId: int, callback: Callback<observer.NavDestinationInfo>): void
```

监听NavDestination组件的状态变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onNavDestinationUpdateByUniqueId(navigationUniqueId: int, callback: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-onNavDestinationUpdateByUniqueId(navigationUniqueId: int, callback: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navigationUniqueId | int | 是 | The uniqueId of the navigation. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.NavDestinationInfo&gt; | 是 | The callback function to be called when the navigation destination is updated. |

## onNodeRenderState

```TypeScript
onNodeRenderState(nodeIdentity: NodeIdentity, callback: NodeRenderStateChangeCallback): void
```

注册一个回调函数，当特定节点的渲染状态发生变化时调用该回调函数。 注册成功后，该回调函数会立即执行一次。 [注意事项]： 1. 请注意节点数量的限制： 出于性能考虑，系统对单个UI实例中可以注册监控的节点数量进行了限制，如果超过限制，则会抛出异常。请谨慎使用此接口。 2. 理解可能不触发通知的场景： 通常，在具有视图或页面切换功能的容器组件中， 当屏幕内的视图或页面被移出屏幕时，之前位于屏幕内的组件应从渲染树中移除，并应收到RENDER\_OUT通知。然而，这并不总是发生，因为某些场景中，视图或组件被移出屏幕显示范围时，并不会触发RENDER\_OUT通知。 例如，一些具有缓存能力的组件可能会影响此行为，轮播组件（swiper）就是其中之一。轮播组件的cacheCount属性允许你通过其第二个参数isShow来强制设置，即使当前页面被移出显示范围，它仍会保留在渲染树中。 这在屏幕上同时显示多个页面时非常有用。 另一个例子是列表（list）或滚动（scroll）等滚动组件，它们的内部内容即使被滚动到屏幕显示范围之外，只要没有使用lazyForEach/Repeat，它们仍会保留在渲染树中。因此，渲染状态不会发生变化。 一旦你理解了渲染状态变化触发的原理，这些场景就会更容易理解。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onNodeRenderState(nodeIdentity: NodeIdentity, callback: NodeRenderStateChangeCallback): void--><!--Device-UIObserver-onNodeRenderState(nodeIdentity: NodeIdentity, callback: NodeRenderStateChangeCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nodeIdentity | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标节点的标识 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当组件节点的渲染状态发生变化时执行的回调函数 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [161001](../errorcode-node-render-monitor.md#161001-监听渲染状态的节点数超过限制) | The count of nodes monitoring render state is over the limitation. |

## onRouterPageSizeChange

```TypeScript
onRouterPageSizeChange(callback: Callback<observer.RouterPageInfo>): void
```

注册监听回调函数，当可见的Router页面大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onRouterPageSizeChange(callback: Callback<observer.RouterPageInfo>): void--><!--Device-UIObserver-onRouterPageSizeChange(callback: Callback<observer.RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.RouterPageInfo&gt; | 是 | 回调函数。携带RouterPageInfo，返回Router页面的信息。 |

## onRouterPageUpdate

```TypeScript
onRouterPageUpdate(callback: Callback<observer.RouterPageInfo>): void
```

监听router中page页面的状态变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onRouterPageUpdate(callback: Callback<observer.RouterPageInfo>): void--><!--Device-UIObserver-onRouterPageUpdate(callback: Callback<observer.RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.RouterPageInfo&gt; | 是 | The callback function to be called when the router page is updated. |

## onScrollEvent

```TypeScript
onScrollEvent(options: observer.ObserverOptions, callback: Callback<observer.ScrollEventInfo>): void
```

注册回调函数，在滚动事件开始或停止时调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onScrollEvent(options: observer.ObserverOptions, callback: Callback<observer.ScrollEventInfo>): void--><!--Device-UIObserver-onScrollEvent(options: observer.ObserverOptions, callback: Callback<observer.ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.ScrollEventInfo&gt; | 是 | The callback function to be called when the scroll event start or stop. |

## onScrollEvent

```TypeScript
onScrollEvent(callback: Callback<observer.ScrollEventInfo>): void
```

注册回调函数，在滚动事件开始或停止时调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onScrollEvent(callback: Callback<observer.ScrollEventInfo>): void--><!--Device-UIObserver-onScrollEvent(callback: Callback<observer.ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.ScrollEventInfo&gt; | 是 | The callback function to be called when the scroll event start or stop. |

## onSwiperContentUpdate

```TypeScript
onSwiperContentUpdate(callback: Callback<SwiperContentInfo>): void
```

监听Swiper内容的切换事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onSwiperContentUpdate(callback: Callback<SwiperContentInfo>): void--><!--Device-UIObserver-onSwiperContentUpdate(callback: Callback<SwiperContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SwiperContentInfo&gt; | 是 | 回调函数。携带SwiperContentInfo，返回Swiper内容切换的信息。 |

## onSwiperContentUpdate

```TypeScript
onSwiperContentUpdate(config: observer.ObserverOptions, callback: Callback<SwiperContentInfo>): void
```

通过Swiper组件的id监听Swiper内容的切换事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onSwiperContentUpdate(config: observer.ObserverOptions, callback: Callback<SwiperContentInfo>): void--><!--Device-UIObserver-onSwiperContentUpdate(config: observer.ObserverOptions, callback: Callback<SwiperContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | observer.ObserverOptions | 是 | 指定监听的Swiper组件信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SwiperContentInfo&gt; | 是 | 回调函数。携带SwiperContentInfo，返回Swiper内容切换的信息。 |

## onTabChange

```TypeScript
onTabChange(config: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void
```

注册一个回调函数，当 tabContent 显示或隐藏时被调用。包括tabs首次加载时的tabContent显示情况以及 tabs 索引切换时tabContent显示情况。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onTabChange(config: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-onTabChange(config: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | observer.ObserverOptions | 是 | 选项对象。包含监听的tabs组件ID。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TabContentInfo&gt; | 是 | 回调函数。当 tabContent 显示或隐藏时被调用。 |

## onTabChange

```TypeScript
onTabChange(callback: Callback<observer.TabContentInfo>): void
```

注册一个回调函数，当 tabContent 显示或隐藏时被调用。包括tabs首次加载时的tabContent显示情况以及 tabs 索引切换时tabContent显示情况。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onTabChange(callback: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-onTabChange(callback: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TabContentInfo&gt; | 是 | 回调函数。当 tabContent 显示或隐藏时被调用。 |

## onTabContentUpdate

```TypeScript
onTabContentUpdate(options: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void
```

监听TabContent页面的切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onTabContentUpdate(options: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-onTabContentUpdate(options: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TabContentInfo&gt; | 是 | The callback function to be called when the tabContent show or hide. |

## onTabContentUpdate

```TypeScript
onTabContentUpdate(callback: Callback<observer.TabContentInfo>): void
```

监听TabContent页面的切换事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onTabContentUpdate(callback: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-onTabContentUpdate(callback: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TabContentInfo&gt; | 是 | The callback function to be called when the tabContent is showed or hidden. |

## onTextChange

```TypeScript
onTextChange(callback: Callback<observer.TextChangeEventInfo>): void
```

注册一个回调函数，当文本字段的内容被更改时将被调用。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onTextChange(callback: Callback<observer.TextChangeEventInfo>): void--><!--Device-UIObserver-onTextChange(callback: Callback<observer.TextChangeEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TextChangeEventInfo&gt; | 是 | 在以下情况下要调用的回调函数：文本字段的内容被更改。 |

## onTextChange

```TypeScript
onTextChange(identity: observer.ObserverOptions, callback: Callback<observer.TextChangeEventInfo>): void
```

注册一个回调函数，当文本字段的内容被更改时将被调用。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onTextChange(identity: observer.ObserverOptions, callback: Callback<observer.TextChangeEventInfo>): void--><!--Device-UIObserver-onTextChange(identity: observer.ObserverOptions, callback: Callback<observer.TextChangeEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| identity | observer.ObserverOptions | 是 | 身份选项。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.TextChangeEventInfo&gt; | 是 | 回调函数在文本字段的内容被更改时调用。 |

## onWillClick

```TypeScript
onWillClick(callback: ClickEventListenerCallback): void
```

注册监听点击事件的无感监听函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onWillClick(callback: ClickEventListenerCallback): void--><!--Device-UIObserver-onWillClick(callback: ClickEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 点击事件触发时的回调函数 |

## onWillDraw

```TypeScript
onWillDraw(callback: Callback<void>): void
```

注册回调函数，在绘制命令即将绘制时调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onWillDraw(callback: Callback<void>): void--><!--Device-UIObserver-onWillDraw(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | The callback function to be called when the draw command will be drawn. |

## onWillTap

```TypeScript
onWillTap(callback: GestureEventListenerCallback): void
```

注册无感监听回调函数

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onWillTap(callback: GestureEventListenerCallback): void--><!--Device-UIObserver-onWillTap(callback: GestureEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 无感监听回调函数 |

## onWindowSizeLayoutBreakpointChange

```TypeScript
onWindowSizeLayoutBreakpointChange(callback: Callback<observer.WindowSizeLayoutBreakpointInfo>): void
```

注册一个回调函数，当窗口大小布局断点改变时调用。 此方法允许观察窗口大小断点的变化，可用于 根据窗口尺寸调整UI布局。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-onWindowSizeLayoutBreakpointChange(callback: Callback<observer.WindowSizeLayoutBreakpointInfo>): void--><!--Device-UIObserver-onWindowSizeLayoutBreakpointChange(callback: Callback<observer.WindowSizeLayoutBreakpointInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;observer.WindowSizeLayoutBreakpointInfo&gt; | 是 | 当窗口大小布局断点更改时调用的回调函数。回调函数接收到一个包含当前宽度和高度断点类型的\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_对象。 |

## removeGlobalGestureListener

```TypeScript
removeGlobalGestureListener(type: GestureListenerType, callback?: GestureListenerCallback): void
```

删除指定类型的手势监听器

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIObserver-removeGlobalGestureListener(type: GestureListenerType, callback?: GestureListenerCallback): void--><!--Device-UIObserver-removeGlobalGestureListener(type: GestureListenerType, callback?: GestureListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要监听的事件类型 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 要移除的回调函数。如果未提供该参数，则将移除给定事件类型的所有回调函数。 |

