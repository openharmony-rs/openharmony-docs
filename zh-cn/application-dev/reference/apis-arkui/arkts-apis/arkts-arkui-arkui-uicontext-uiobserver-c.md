# UIObserver

UIObserver提供了UI组件行为变化的无感监听能力，支持监听Navigation页面状态变化（NavDestination）、滚动事件、路由页面状态、屏幕像素密度变化、 绘制指令下发、布局完成、页面切换等多种UI组件行为。开发者可以通过该模块实现对UI组件状态的实时感知和追踪，适用于需要监控页面生命周期、处理滚动事件、 优化渲染性能等场景，帮助开发者更好地理解和管理UI组件的行为变化。无感监听是指在组件状态变化时，系统自动触发回调函数通知开发者，无需开发者手动轮询或主动查询组件状态。监听器通过注册回调函数实现，当目标组件状态改变时，系统内部的事件分发机制会调用已注册的回调函数，携带状态变化信息。 > **说明：** > - 以下API需先使用UIContext中的[getUIObserver()](arkts-arkui-arkui-uicontext-uicontext-c.md#getUIObserver)方法获取到UIObserver对象，再通过该对象调用对应方法。 > > - UIObserver仅能监听到本进程内的UI组件状态变化信息，不支持获取&lt;!--Del--&gt;UIExtensionComponent等&lt;!--DelEnd--&gt;跨进程场景的信息。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-export class UIObserver--><!--Device-unnamed-export class UIObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addGlobalGestureListener

```TypeScript
addGlobalGestureListener(type: GestureListenerType,
      option: GestureObserverConfigs, callback: GestureListenerCallback): void
```

注册回调函数以监听手势触发信息。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-addGlobalGestureListener(type: GestureListenerType,      option: GestureObserverConfigs, callback: GestureListenerCallback): void--><!--Device-UIObserver-addGlobalGestureListener(type: GestureListenerType,      option: GestureObserverConfigs, callback: GestureListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [GestureListenerType](arkts-arkui-arkui-uicontext-gesturelistenertype-e.md) | 是 | 要监听的手势类型。 |
| option | [GestureObserverConfigs](arkts-arkui-arkui-uicontext-gestureobserverconfigs-i.md) | 是 | 绑定全局监听器时的配置选项。 |
| callback | [GestureListenerCallback](arkts-arkui-gesturelistenercallback-t.md) | 是 | 手势状态更新时的回调函数。 |

## offNavDestinationSizeChange

```TypeScript
offNavDestinationSizeChange(callback?: Callback<observer.NavDestinationInfo>): void
```

移除使用onNavDestinationSizeChange接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-offNavDestinationSizeChange(callback?: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-offNavDestinationSizeChange(callback?: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationInfo&gt; | 否 | 需要被移除的回调函数。不传参数时，移除所有回调函数。 |

## offNavDestinationSizeChangeByUniqueId

```TypeScript
offNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void
```

移除使用onNavDestinationSizeChangeByUniqueId接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-offNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-offNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navigationUniqueId | number | 是 | 希望监听的NavDestination所属的Navigation的唯一ID，可以通过 queryNavigationInfo获取。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationInfo&gt; | 否 | 需要被移除的回调函数。不传参数时，移除所有指定了相同navigationUniqueId的回调函数。 |

## offRouterPageSizeChange

```TypeScript
offRouterPageSizeChange(callback?: Callback<observer.RouterPageInfo>): void
```

移除使用onRouterPageSizeChange接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-offRouterPageSizeChange(callback?: Callback<observer.RouterPageInfo>): void--><!--Device-UIObserver-offRouterPageSizeChange(callback?: Callback<observer.RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.RouterPageInfo&gt; | 否 | 需要被移除的回调函数。不传参数时，移除所有回调函数。 |

## offSwiperContentUpdate

```TypeScript
offSwiperContentUpdate(callback?: Callback<SwiperContentInfo>): void
```

取消监听Swiper内容的切换事件。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-offSwiperContentUpdate(callback?: Callback<SwiperContentInfo>): void--><!--Device-UIObserver-offSwiperContentUpdate(callback?: Callback<SwiperContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | 否 | 需要被注销的回调函数。不传参数时，取消该Swiper上所有的监听回调。 |

## offSwiperContentUpdate

```TypeScript
offSwiperContentUpdate(config: observer.ObserverOptions, callback?: Callback<SwiperContentInfo>): void
```

取消通过Swiper组件id监听的Swiper内容切换事件。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-offSwiperContentUpdate(config: observer.ObserverOptions, callback?: Callback<SwiperContentInfo>): void--><!--Device-UIObserver-offSwiperContentUpdate(config: observer.ObserverOptions, callback?: Callback<SwiperContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | observer.ObserverOptions | 是 | 指定监听的Swiper组件信息。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | 否 | 需要被注销的回调函数。不传参数时，取消该Swiper上所有的监听回调。 |

## off_afterPanEnd

```TypeScript
off(type: 'afterPanEnd', callback?: PanListenerCallback): void
```

取消[on('afterPanEnd')](#on_navDestinationUpdate)监听Pan手势 onActionEnd事件执行后的callback回调。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'afterPanEnd', callback?: PanListenerCallback): void--><!--Device-UIObserver-off(type: 'afterPanEnd', callback?: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanEnd' | 是 | 监听事件，固定为'afterPanEnd'，即Pan手势onActionEnd事件执 行后的指令下发情况。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势 onActionEnd事件执行后的指令下发监听回调。 |

## off_afterPanStart

```TypeScript
off(type: 'afterPanStart', callback?: PanListenerCallback): void
```

取消[on('afterPanStart')](#on_navDestinationUpdate)监听Pan手势 onActionStart事件执行后的callback回调。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'afterPanStart', callback?: PanListenerCallback): void--><!--Device-UIObserver-off(type: 'afterPanStart', callback?: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanStart' | 是 | 监听事件，固定为'afterPanStart'，即Pan手势 onActionStart事件执行后的指令下发情况。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势 onActionStart事件执行后的指令下发监听回调。 |

## off_beforePanEnd

```TypeScript
off(type: 'beforePanEnd', callback?: PanListenerCallback): void
```

取消[on('beforePanEnd')](#on_navDestinationUpdate)监听Pan手势 onActionEnd事件执行前的callback回调。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'beforePanEnd', callback?: PanListenerCallback): void--><!--Device-UIObserver-off(type: 'beforePanEnd', callback?: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanEnd' | 是 | 监听事件，固定为'beforePanEnd'，即Pan手势onActionEnd事 件执行前的指令下发情况。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势 onActionEnd事件执行前的指令下发监听回调。 |

## off_beforePanStart

```TypeScript
off(type: 'beforePanStart', callback?: PanListenerCallback): void
```

取消[on('beforePanStart')](#on_navDestinationUpdate)监听Pan手势 onActionStart事件执行前的callback回调。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'beforePanStart', callback?: PanListenerCallback): void--><!--Device-UIObserver-off(type: 'beforePanStart', callback?: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanStart' | 是 | 监听事件，固定为'beforePanStart'，即Pan手势 onActionStart事件执行前的指令下发情况。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势 onActionStart事件执行前的指令下发监听回调。 |

## off_densityUpdate

```TypeScript
off(type: 'densityUpdate', callback?: Callback<observer.DensityInfo>): void
```

取消监听屏幕像素密度的变化。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'densityUpdate', callback?: Callback<observer.DensityInfo>): void--><!--Device-UIObserver-off(type: 'densityUpdate', callback?: Callback<observer.DensityInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'densityUpdate' | 是 | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.DensityInfo&gt; | 否 | 需要被注销的回调函数。若不指定具体的回调函数，则注销该 [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md#UIContext)下所有屏幕像素密度变化事件监听。 |

## off_didClick

```TypeScript
off(type: 'didClick', callback?: ClickEventListenerCallback): void
```

Removes a callback function to be called after clickEvent is called.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'didClick', callback?: ClickEventListenerCallback): void--><!--Device-UIObserver-off(type: 'didClick', callback?: ClickEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to remove the listener for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_didClick

```TypeScript
off(type: 'didClick', callback?: GestureEventListenerCallback): void
```

Removes a callback function to be called after tapGesture is called.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'didClick', callback?: GestureEventListenerCallback): void--><!--Device-UIObserver-off(type: 'didClick', callback?: GestureEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to remove the listener for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_didLayout

```TypeScript
off(type: 'didLayout', callback?: Callback<void>): void
```

取消监听每一帧布局完成情况。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'didLayout', callback?: Callback<void>): void--><!--Device-UIObserver-off(type: 'didLayout', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 需要被注销的回调函数。不传参数时，取消所有布局完成的监听回调。 |

## off_navDestinationSwitch

```TypeScript
off(
    type: 'navDestinationSwitch',
    callback?: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(    type: 'navDestinationSwitch',    callback?: Callback<observer.NavDestinationSwitchInfo>  ): void--><!--Device-UIObserver-off(    type: 'navDestinationSwitch',    callback?: Callback<observer.NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to remove the listener for. Must be ' navDestinationSwitch'. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationSwitchInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_navDestinationSwitch

```TypeScript
off(
    type: 'navDestinationSwitch',
    observerOptions: observer.NavDestinationSwitchObserverOptions,
    callback?: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(    type: 'navDestinationSwitch',    observerOptions: observer.NavDestinationSwitchObserverOptions,    callback?: Callback<observer.NavDestinationSwitchInfo>  ): void--><!--Device-UIObserver-off(    type: 'navDestinationSwitch',    observerOptions: observer.NavDestinationSwitchObserverOptions,    callback?: Callback<observer.NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to remove the listener for. Must be ' navDestinationSwitch'. |
| observerOptions | observer.NavDestinationSwitchObserverOptions | 是 | Options. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationSwitchInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_navDestinationUpdate

```TypeScript
off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<observer.NavDestinationInfo>): void
```

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | The type of event to remove the listener for. Must be ' navDestinationUpdate'. |
| options | { navigationId: ResourceStr } | 是 | The options object. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type and navigation ID will be removed. |

## off_navDestinationUpdate

```TypeScript
off(type: 'navDestinationUpdate', callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'navDestinationUpdate', callback?: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-off(type: 'navDestinationUpdate', callback?: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | The type of event to remove the listener for. Must be 'navDestinationUpdate '. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_navDestinationUpdateByUniqueId

```TypeScript
off(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-off(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdateByUniqueId' | 是 | The type of event to remove the listener for. Must be ' navDestinationUpdateByUniqueId'. |
| navigationUniqueId | number | 是 | The uniqueId of the navigation. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_nodeRenderState

```TypeScript
off(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback?: NodeRenderStateChangeCallback): void
```

取消监听节点渲染状态发生变化的callback回调。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback?: NodeRenderStateChangeCallback): void--><!--Device-UIObserver-off(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback?: NodeRenderStateChangeCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'nodeRenderState' | 是 | 监听事件，固定为'nodeRenderState'，即节点渲染状态变化指令下发情况。 |
| nodeIdentity | [NodeIdentity](arkts-arkui-nodeidentity-t.md) | 是 | 节点标识。 |
| callback | [NodeRenderStateChangeCallback](arkts-arkui-noderenderstatechangecallback-t.md) | 否 | 需要被注销的回调函数。不传参数时，取消该节点所有的渲染状态变化指令下发监听回调。 |

## off_routerPageUpdate

```TypeScript
off(type: 'routerPageUpdate', callback?: Callback<observer.RouterPageInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'routerPageUpdate', callback?: Callback<observer.RouterPageInfo>): void--><!--Device-UIObserver-off(type: 'routerPageUpdate', callback?: Callback<observer.RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | 是 | The type of event to remove the listener for. Must be 'routerPageUpdate'. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.RouterPageInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_scrollEvent

```TypeScript
off(type: 'scrollEvent', options: observer.ObserverOptions, callback?: Callback<observer.ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'scrollEvent', options: observer.ObserverOptions, callback?: Callback<observer.ScrollEventInfo>): void--><!--Device-UIObserver-off(type: 'scrollEvent', options: observer.ObserverOptions, callback?: Callback<observer.ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to remove the listener for. Must be 'scrollEvent'. |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.ScrollEventInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type and scroll ID will be removed. |

## off_scrollEvent

```TypeScript
off(type: 'scrollEvent', callback?: Callback<observer.ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'scrollEvent', callback?: Callback<observer.ScrollEventInfo>): void--><!--Device-UIObserver-off(type: 'scrollEvent', callback?: Callback<observer.ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to remove the listener for. Must be 'scrollEvent'. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.ScrollEventInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_tabChange

```TypeScript
off(type: 'tabChange', config: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void
```

移除之前通过 `on()` 注册的回调函数。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'tabChange', config: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-off(type: 'tabChange', config: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要移除监听的事件类型。必须是 'tabChange'。 |
| config | observer.ObserverOptions | 是 | 选项对象。包含监听的tabs组件ID。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TabContentInfo&gt; | 否 | 要移除的回调函数。 如果未提供该参数，则将移除该tabs id的所有'tabChange'无感监听回调函数。 |

## off_tabChange

```TypeScript
off(type: 'tabChange', callback?: Callback<observer.TabContentInfo>): void
```

移除之前通过 `on()` 注册的回调函数。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'tabChange', callback?: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-off(type: 'tabChange', callback?: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要移除监听的事件类型。必须是 'tabChange'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TabContentInfo&gt; | 否 | 要移除的回调函数。 如果未提供该参数，则将移除所有tabs的所有'tabChange'无感监听回调函数。 |

## off_tabContentUpdate

```TypeScript
off(type: 'tabContentUpdate', options: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'tabContentUpdate', options: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-off(type: 'tabContentUpdate', options: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to remove the listener for. Must be 'tabContentUpdate'. |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TabContentInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type and Tabs ID will be removed. |

## off_tabContentUpdate

```TypeScript
off(type: 'tabContentUpdate', callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'tabContentUpdate', callback?: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-off(type: 'tabContentUpdate', callback?: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to remove the listener for. Must be 'tabContentUpdate'. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TabContentInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type and Tabs ID will be removed. |

## off_textChange

```TypeScript
off(type: 'textChange', callback?: Callback<observer.TextChangeEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'textChange', callback?: Callback<observer.TextChangeEventInfo>): void--><!--Device-UIObserver-off(type: 'textChange', callback?: Callback<observer.TextChangeEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to remove the listener for. Must be 'textChange'. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TextChangeEventInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_textChange

```TypeScript
off(type: 'textChange', identity: observer.ObserverOptions, callback?: Callback<observer.TextChangeEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'textChange', identity: observer.ObserverOptions, callback?: Callback<observer.TextChangeEventInfo>): void--><!--Device-UIObserver-off(type: 'textChange', identity: observer.ObserverOptions, callback?: Callback<observer.TextChangeEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to remove the listener for. Must be 'textChange'. |
| identity | observer.ObserverOptions | 是 | Identity options. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TextChangeEventInfo&gt; | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_willClick

```TypeScript
off(type: 'willClick', callback?: ClickEventListenerCallback): void
```

Removes a callback function to be called before clickEvent is called.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'willClick', callback?: ClickEventListenerCallback): void--><!--Device-UIObserver-off(type: 'willClick', callback?: ClickEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to remove the listener for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_willClick

```TypeScript
off(type: 'willClick', callback?: GestureEventListenerCallback): void
```

Removes a callback function to be called before tapGesture is called.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'willClick', callback?: GestureEventListenerCallback): void--><!--Device-UIObserver-off(type: 'willClick', callback?: GestureEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to remove the listener for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | 否 | The callback function to remove. If not provided, all callbacks for the given event type will be removed. |

## off_willDraw

```TypeScript
off(type: 'willDraw', callback?: Callback<void>): void
```

取消监听每一帧绘制指令下发情况。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'willDraw', callback?: Callback<void>): void--><!--Device-UIObserver-off(type: 'willDraw', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willDraw' | 是 | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 需要被注销的回调函数。不传参数时，取消所有绘制指令下发事件的监听回调。 |

## off_windowSizeLayoutBreakpointChange

```TypeScript
off(type: 'windowSizeLayoutBreakpointChange', callback?: Callback<observer.WindowSizeLayoutBreakpointInfo>): void
```

移除之前注册的窗口尺寸布局断点变化回调函数。如果未提供回调函数参数，将移除指定上下文的所有回调函数。使用callback异步回调。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-off(type: 'windowSizeLayoutBreakpointChange', callback?: Callback<observer.WindowSizeLayoutBreakpointInfo>): void--><!--Device-UIObserver-off(type: 'windowSizeLayoutBreakpointChange', callback?: Callback<observer.WindowSizeLayoutBreakpointInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeLayoutBreakpointChange' | 是 | 监听事件，固定为'windowSizeLayoutBreakpointChange'，用于监听窗口尺寸布局断点发生改变。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.WindowSizeLayoutBreakpointInfo&gt; | 否 | 需要被注销的回调函数。若不指定具体的回调函数，则注销该 [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md#UIContext)下所有窗口尺寸布局断点变化事件监听。 |

## onNavDestinationSizeChange

```TypeScript
onNavDestinationSizeChange(callback: Callback<observer.NavDestinationInfo>): void
```

注册监听回调函数，当可见的NavDestination大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-onNavDestinationSizeChange(callback: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-onNavDestinationSizeChange(callback: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationInfo&gt; | 是 | 回调函数。携带NavDestinationInfo，返回NavDestination的信息。 |

## onNavDestinationSizeChangeByUniqueId

```TypeScript
onNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void
```

注册监听回调函数，当属于指定Navigation的可见NavDestination的大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-onNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-onNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navigationUniqueId | number | 是 | 希望监听NavDestination所属的Navigation的唯一ID，可以通过queryNavigationInfo获取。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationInfo&gt; | 是 | Callback to be removed. If no parameter is passed, all callbacks with the same **navigationUniqueId** setting are removed. |

## onRouterPageSizeChange

```TypeScript
onRouterPageSizeChange(callback: Callback<observer.RouterPageInfo>): void
```

注册一个callback，当router可见页面尺寸发生变化时触发注册监听回调函数，当可见的Router页面大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-onRouterPageSizeChange(callback: Callback<observer.RouterPageInfo>): void--><!--Device-UIObserver-onRouterPageSizeChange(callback: Callback<observer.RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.RouterPageInfo&gt; | 是 | 回调函数。携带RouterPageInfo，返回Router页面的信息。 |

## onSwiperContentUpdate

```TypeScript
onSwiperContentUpdate(callback: Callback<SwiperContentInfo>): void
```

监听Swiper内容的切换事件。使用callback异步回调。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-onSwiperContentUpdate(callback: Callback<SwiperContentInfo>): void--><!--Device-UIObserver-onSwiperContentUpdate(callback: Callback<SwiperContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | 是 | 回调函数。携带SwiperContentInfo，返回Swiper内容切换的信息。 |

## onSwiperContentUpdate

```TypeScript
onSwiperContentUpdate(config: observer.ObserverOptions, callback: Callback<SwiperContentInfo>): void
```

通过Swiper组件的id监听Swiper内容的切换事件。使用callback异步回调。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-onSwiperContentUpdate(config: observer.ObserverOptions, callback: Callback<SwiperContentInfo>): void--><!--Device-UIObserver-onSwiperContentUpdate(config: observer.ObserverOptions, callback: Callback<SwiperContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | observer.ObserverOptions | 是 | 指定监听的Swiper组件信息。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SwiperContentInfo](arkts-arkui-arkui-uicontext-swipercontentinfo-i.md)&gt; | 是 | 回调函数。携带SwiperContentInfo，返回Swiper内容切换的信息。 |

## on_afterPanEnd

```TypeScript
on(type: 'afterPanEnd', callback: PanListenerCallback): void
```

监听Pan手势onActionEnd事件执行后的指令下发情况，在 onActionEnd事件执行之后执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'afterPanEnd', callback: PanListenerCallback): void--><!--Device-UIObserver-on(type: 'afterPanEnd', callback: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanEnd' | 是 | 监听事件，固定为'afterPanEnd'，用于监听Pan手势onActionEnd 事件执行后的指令下发情况，所注册回调将于Pan手势onActionEnd事件触发后触发。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 是 | 回调函数。可以获得Pan手势事件的 GestureEvent，GestureRecognizer和组件的FrameNode。 |

## on_afterPanStart

```TypeScript
on(type: 'afterPanStart', callback: PanListenerCallback): void
```

监听Pan手势onActionStart事件执行后的指令下发情况，在 onActionStart事件执行之后执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'afterPanStart', callback: PanListenerCallback): void--><!--Device-UIObserver-on(type: 'afterPanStart', callback: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanStart' | 是 | 监听事件，固定为'afterPanStart'，用于监听Pan手势 onActionStart事件执行后的指令下发情况，所注册回调将于Pan手势 onActionStart事件触发后触发。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 是 | 回调函数。可以获得Pan手势事件的 GestureEvent，GestureRecognizer和组件的FrameNode。 |

## on_beforePanEnd

```TypeScript
on(type: 'beforePanEnd', callback: PanListenerCallback): void
```

监听Pan手势onActionEnd事件执行前的指令下发情况，在 onActionEnd事件执行之前执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'beforePanEnd', callback: PanListenerCallback): void--><!--Device-UIObserver-on(type: 'beforePanEnd', callback: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanEnd' | 是 | 监听事件，固定为'beforePanEnd'，用于监听Pan手势 onActionEnd事件执行前的指令下发情况，所注册回调将于Pan手势 onActionEnd事件触发前触发。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 是 | 回调函数。可以获得Pan手势事件的 GestureEvent，GestureRecognizer和组件的FrameNode。 |

## on_beforePanStart

```TypeScript
on(type: 'beforePanStart', callback: PanListenerCallback): void
```

监听Pan手势onActionStart事件，在 onActionStart事件执行之前执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'beforePanStart', callback: PanListenerCallback): void--><!--Device-UIObserver-on(type: 'beforePanStart', callback: PanListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanStart' | 是 | 监听事件，固定为'beforePanStart'，用于监听Pan手势 onActionStart事件执行前的指令下发情况，所注册回调将于Pan手势 onActionStart事件触发前触发。 |
| callback | [PanListenerCallback](arkts-arkui-panlistenercallback-t.md) | 是 | 回调函数。可以获得Pan手势事件的 GestureEvent，GestureRecognizer和组件的FrameNode。 |

## on_densityUpdate

```TypeScript
on(type: 'densityUpdate', callback: Callback<observer.DensityInfo>): void
```

监听屏幕像素密度变化。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'densityUpdate', callback: Callback<observer.DensityInfo>): void--><!--Device-UIObserver-on(type: 'densityUpdate', callback: Callback<observer.DensityInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'densityUpdate' | 是 | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.DensityInfo&gt; | 是 | 回调函数。携带 [DensityInfo](arkts-arkui-uiobserver-densityinfo-c.md#DensityInfo)，返回变化后的屏幕像素密度。 |

## on_didClick

```TypeScript
on(type: 'didClick', callback: ClickEventListenerCallback): void
```

Registers a callback function to be called after clickEvent is called.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'didClick', callback: ClickEventListenerCallback): void--><!--Device-UIObserver-on(type: 'didClick', callback: ClickEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to listen for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | 是 | The callback function to be called when the clickEvent will be trigger or after. |

## on_didClick

```TypeScript
on(type: 'didClick', callback: GestureEventListenerCallback): void
```

Registers a callback function to be called after tapGesture is called.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'didClick', callback: GestureEventListenerCallback): void--><!--Device-UIObserver-on(type: 'didClick', callback: GestureEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to listen for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | 是 | The callback function to be called when the clickEvent will be trigger or after. |

## on_didLayout

```TypeScript
on(type: 'didLayout', callback: Callback<void>): void
```

监听每一帧布局完成情况。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'didLayout', callback: Callback<void>): void--><!--Device-UIObserver-on(type: 'didLayout', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。 |

## on_navDestinationSwitch

```TypeScript
on(
    type: 'navDestinationSwitch',
    callback: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Registers a callback function to be called when the navigation switched to a new navDestination.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(    type: 'navDestinationSwitch',    callback: Callback<observer.NavDestinationSwitchInfo>  ): void--><!--Device-UIObserver-on(    type: 'navDestinationSwitch',    callback: Callback<observer.NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to listen for. Must be 'navDestinationSwitch'. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationSwitchInfo&gt; | 是 | The callback function to be called when the navigation switched to a new navDestination. |

## on_navDestinationSwitch

```TypeScript
on(
    type: 'navDestinationSwitch',
    observerOptions: observer.NavDestinationSwitchObserverOptions,
    callback: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Registers a callback function to be called when the navigation switched to a new navDestination.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(    type: 'navDestinationSwitch',    observerOptions: observer.NavDestinationSwitchObserverOptions,    callback: Callback<observer.NavDestinationSwitchInfo>  ): void--><!--Device-UIObserver-on(    type: 'navDestinationSwitch',    observerOptions: observer.NavDestinationSwitchObserverOptions,    callback: Callback<observer.NavDestinationSwitchInfo>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to listen for. Must be 'navDestinationSwitch'. |
| observerOptions | observer.NavDestinationSwitchObserverOptions | 是 | Options. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationSwitchInfo&gt; | 是 | The callback function to be called when the navigation switched to a new navDestination. |

## on_navDestinationUpdate

```TypeScript
on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback<observer.NavDestinationInfo>): void
```

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | Event type. The value is fixed at **'navDestinationUpdate'**, which indicates the state change event &lt;br&gt;of the **NavDestination** component. |
| options | { navigationId: ResourceStr } | 是 | ID of the target **NavDestination** component. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationInfo&gt; | 是 | Callback used to return the current &lt;br&gt;state of the **NavDestination** component. |

## on_navDestinationUpdate

```TypeScript
on(type: 'navDestinationUpdate', callback: Callback<observer.NavDestinationInfo>): void
```

Subscribes to status changes of this **NavDestination** component.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'navDestinationUpdate', callback: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-on(type: 'navDestinationUpdate', callback: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | Event type. The value is fixed at **'navDestinationUpdate'**, &lt;br&gt;which indicates the state change event of the **NavDestination** component. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationInfo&gt; | 是 | Callback used to return the current state of &lt;br&gt;the **NavDestination** component. |

## on_navDestinationUpdateByUniqueId

```TypeScript
on(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void
```

Registers a callback function to be called when the navigation destination is updated.

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void--><!--Device-UIObserver-on(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdateByUniqueId' | 是 | The type of event to listen for. Must be ' navDestinationUpdateByUniqueId'. |
| navigationUniqueId | number | 是 | The uniqueId of the navigation. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.NavDestinationInfo&gt; | 是 | The callback function to be called when the navigation destination is updated. |

## on_nodeRenderState

```TypeScript
on(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback: NodeRenderStateChangeCallback): void
```

注册一个回调函数，以便在特定节点的渲染状态发生变化时调用，当注册成功时，此回调将立即执行一次。 注意节点数量的限制。出于性能考虑，在单个UI实例中，注册节点太多，将会抛出异常。 通常，当组件被移动到屏幕外时，会收到RENDER_OUT的通知。但在某些情况下，即使组件移动到屏幕外也不会触发RENDER_OUT通知。例如，具有缓存功能的组件Swiper，即使 cachedCount属性中的参数isShown配置为true，也不会触发 RENDER_OUT通知。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback: NodeRenderStateChangeCallback): void--><!--Device-UIObserver-on(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback: NodeRenderStateChangeCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'nodeRenderState' | 是 | 监听事件，固定为'nodeRenderState'，用于监听节点渲染状态发生改变。 |
| nodeIdentity | [NodeIdentity](arkts-arkui-nodeidentity-t.md) | 是 | 节点标识。 |
| callback | [NodeRenderStateChangeCallback](arkts-arkui-noderenderstatechangecallback-t.md) | 是 | 回调函数。可以获得节点渲染状态改变事件的 [NodeRenderState](arkts-arkui-arkui-uicontext-noderenderstate-e.md#NodeRenderState)和组件的FrameNode。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [161001](../errorcode-node-render-monitor.md#161001-监听渲染状态的节点数超过限制) | The count of nodes monitoring render state is over the limitation. |

## on_routerPageUpdate

```TypeScript
on(type: 'routerPageUpdate', callback: Callback<observer.RouterPageInfo>): void
```

Unsubscribes to state changes of the page in the router.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'routerPageUpdate', callback: Callback<observer.RouterPageInfo>): void--><!--Device-UIObserver-on(type: 'routerPageUpdate', callback: Callback<observer.RouterPageInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | 是 | Event type. &lt;br&gt;The value is fixed at 'routerPageUpdate', which indicates the state change event of the page in the router. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.RouterPageInfo&gt; | 是 | Callback to be unregistered. |

## on_scrollEvent

```TypeScript
on(type: 'scrollEvent', options: observer.ObserverOptions, callback: Callback<observer.ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'scrollEvent', options: observer.ObserverOptions, callback: Callback<observer.ScrollEventInfo>): void--><!--Device-UIObserver-on(type: 'scrollEvent', options: observer.ObserverOptions, callback: Callback<observer.ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.ScrollEventInfo&gt; | 是 | The callback function to be called when the scroll event start or stop. |

## on_scrollEvent

```TypeScript
on(type: 'scrollEvent', callback: Callback<observer.ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'scrollEvent', callback: Callback<observer.ScrollEventInfo>): void--><!--Device-UIObserver-on(type: 'scrollEvent', callback: Callback<observer.ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.ScrollEventInfo&gt; | 是 | The callback function to be called when the scroll event start or stop. |

## on_tabChange

```TypeScript
on(type: 'tabChange', config: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void
```

注册一个回调函数，当 tabContent 显示或隐藏时被调用。包括tabs首次加载时的tabContent显示情况以及 tabs 索引切换时tabContent显示情况。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'tabChange', config: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-on(type: 'tabChange', config: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要监听的事件类型。必须是 'tabChange'。 |
| config | observer.ObserverOptions | 是 | 选项对象。包含监听的tabs组件ID。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TabContentInfo&gt; | 是 | 回调函数，当 tabContent 显示或隐藏时被调用。 |

## on_tabChange

```TypeScript
on(type: 'tabChange', callback: Callback<observer.TabContentInfo>): void
```

注册一个回调函数，当 tabContent 显示或隐藏时被调用。包括tabs首次加载时的tabContent显示情况以及 tabs 索引切换时tabContent显示情况。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'tabChange', callback: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-on(type: 'tabChange', callback: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要监听的事件类型。必须是 'tabChange'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TabContentInfo&gt; | 是 | 回调函数，当 tabContent 显示或隐藏时调用。 |

## on_tabContentUpdate

```TypeScript
on(type: 'tabContentUpdate', options: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void
```

Registers a callback function to be called when the tabContent is showed or hidden.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'tabContentUpdate', options: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-on(type: 'tabContentUpdate', options: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to listen for. Must be 'tabContentUpdate'. |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TabContentInfo&gt; | 是 | The callback function to be called when the tabContent show or hide. |

## on_tabContentUpdate

```TypeScript
on(type: 'tabContentUpdate', callback: Callback<observer.TabContentInfo>): void
```

Registers a callback function to be called when the tabContent is showed or hidden.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'tabContentUpdate', callback: Callback<observer.TabContentInfo>): void--><!--Device-UIObserver-on(type: 'tabContentUpdate', callback: Callback<observer.TabContentInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to listen for. Must be 'tabContentUpdate'. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TabContentInfo&gt; | 是 | The callback function to be called when the tabContent is showed or hidden. |

## on_textChange

```TypeScript
on(type: 'textChange', callback: Callback<observer.TextChangeEventInfo>): void
```

Registers a callback function to be called when text field's content is changed.

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'textChange', callback: Callback<observer.TextChangeEventInfo>): void--><!--Device-UIObserver-on(type: 'textChange', callback: Callback<observer.TextChangeEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to listen for. Must be 'textChange'. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TextChangeEventInfo&gt; | 是 | The callback function to be called when text field's content is changed. |

## on_textChange

```TypeScript
on(type: 'textChange', identity: observer.ObserverOptions, callback: Callback<observer.TextChangeEventInfo>): void
```

Registers a callback function to be called when text field's content is changed.

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'textChange', identity: observer.ObserverOptions, callback: Callback<observer.TextChangeEventInfo>): void--><!--Device-UIObserver-on(type: 'textChange', identity: observer.ObserverOptions, callback: Callback<observer.TextChangeEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to listen for. Must be 'textChange'. |
| identity | observer.ObserverOptions | 是 | Identity options. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.TextChangeEventInfo&gt; | 是 | The callback function to be called when the text field's content is changed. |

## on_willClick

```TypeScript
on(type: 'willClick', callback: ClickEventListenerCallback): void
```

Registers a callback function to be called before clickEvent is called.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'willClick', callback: ClickEventListenerCallback): void--><!--Device-UIObserver-on(type: 'willClick', callback: ClickEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to listen for. |
| callback | [ClickEventListenerCallback](arkts-arkui-clickeventlistenercallback-t.md) | 是 | The callback function to be called when the clickEvent will be trigger or after. |

## on_willClick

```TypeScript
on(type: 'willClick', callback: GestureEventListenerCallback): void
```

Registers a callback function to be called before tapGesture is called.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'willClick', callback: GestureEventListenerCallback): void--><!--Device-UIObserver-on(type: 'willClick', callback: GestureEventListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to listen for. |
| callback | [GestureEventListenerCallback](arkts-arkui-gestureeventlistenercallback-t.md) | 是 | The callback function to be called when the clickEvent will be trigger or after. |

## on_willDraw

```TypeScript
on(type: 'willDraw', callback: Callback<void>): void
```

监听每一帧绘制指令下发情况。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'willDraw', callback: Callback<void>): void--><!--Device-UIObserver-on(type: 'willDraw', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willDraw' | 是 | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数。 |

## on_windowSizeLayoutBreakpointChange

```TypeScript
on(type: 'windowSizeLayoutBreakpointChange', callback: Callback<observer.WindowSizeLayoutBreakpointInfo>): void
```

注册窗口尺寸布局断点变化的回调函数。该方法用于监听窗口尺寸断点变化，可用于根据窗口尺寸自适应调整UI布局。使用callback异步回调。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-on(type: 'windowSizeLayoutBreakpointChange', callback: Callback<observer.WindowSizeLayoutBreakpointInfo>): void--><!--Device-UIObserver-on(type: 'windowSizeLayoutBreakpointChange', callback: Callback<observer.WindowSizeLayoutBreakpointInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeLayoutBreakpointChange' | 是 | 监听事件，固定为'windowSizeLayoutBreakpointChange'，用于监听窗口尺寸布局断点发生改变。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;observer.WindowSizeLayoutBreakpointInfo&gt; | 是 | 回调函数。携带WindowSizeLayoutBreakpointinfo，包含窗口宽 度和高度所在的布局断点枚举。 |

## removeGlobalGestureListener

```TypeScript
removeGlobalGestureListener(type: GestureListenerType, callback?: GestureListenerCallback): void
```

移除某一手势监听器类型的回调函数。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UIObserver-removeGlobalGestureListener(type: GestureListenerType, callback?: GestureListenerCallback): void--><!--Device-UIObserver-removeGlobalGestureListener(type: GestureListenerType, callback?: GestureListenerCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [GestureListenerType](arkts-arkui-arkui-uicontext-gesturelistenertype-e.md) | 是 | 要移除监听器的事件类型。 |
| callback | [GestureListenerCallback](arkts-arkui-gesturelistenercallback-t.md) | 否 | 待移除的回调函数（未提供时将清除该手势类型的所有回调）。 |

