# UIObserver

提供UI组件行为变化的无感监听能力。

> **说明：**

> - 以下API需先使用UIContext中的[getUIObserver()](arkts-arkui-uicontext-c.md#getuiobserver-1)方法获取到UIObserver对象，再通过该对象调用对应方法。
>
> - UIObserver仅能监听到本进程内的相关信息，不支持获取<!--Del-->[UIExtensionComponent](ui_extension_component)等<!--DelEnd-->跨进程场景的信
> 息。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addGlobalGestureListener

```TypeScript
addGlobalGestureListener(type: GestureListenerType,
      option: GestureObserverConfigs, callback: GestureListenerCallback): void
```

注册回调函数以监听手势触发信息。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | GestureListenerType | 是 | 要监听的手势类型。 |
| option | GestureObserverConfigs | 是 | 绑定全局监听器时的配置选项。 |
| callback | GestureListenerCallback | 是 | 手势状态更新时的回调函数。 |

## off('navDestinationUpdate')

```TypeScript
off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback<observer.NavDestinationInfo>): void
```

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | The type of event to remove the listener for. Must be 'navDestinationUpdate'. |
| options | { navigationId: ResourceStr } | 是 | The options object. |
| callback | Callback&lt;observer.NavDestinationInfo&gt; | 否 | The callback function to remove. If not provided, allcallbacks for the given event type andnavigation ID will be removed. |

## off('navDestinationUpdate')

```TypeScript
off(type: 'navDestinationUpdate', callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | The type of event to remove the listener for. Must be 'navDestinationUpdate'. |
| callback | Callback&lt;observer.NavDestinationInfo&gt; | 否 | The callback function to remove. If not provided, allcallbacks for the given event typewill be removed. |

## off('navDestinationUpdateByUniqueId')

```TypeScript
off(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdateByUniqueId' | 是 | The type of event to remove the listener for. Must be 'navDestinationUpdateByUniqueId'. |
| navigationUniqueId | number | 是 | The uniqueId of the navigation. |
| callback | Callback&lt;observer.NavDestinationInfo&gt; | 否 | The callback function to remove. If not provided, allcallbacks for the given event typewill be removed. |

## off('scrollEvent')

```TypeScript
off(type: 'scrollEvent', options: observer.ObserverOptions, callback?: Callback<observer.ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to remove the listener for. Must be 'scrollEvent'. |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | Callback&lt;observer.ScrollEventInfo&gt; | 否 | The callback function to remove. If not provided, allcallbacks for the given event type andscroll ID will be removed. |

## off('scrollEvent')

```TypeScript
off(type: 'scrollEvent', callback?: Callback<observer.ScrollEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to remove the listener for. Must be 'scrollEvent'. |
| callback | Callback&lt;observer.ScrollEventInfo&gt; | 否 | The callback function to remove. If not provided, allcallbacks for the given event typewill be removed. |

## off('routerPageUpdate')

```TypeScript
off(type: 'routerPageUpdate', callback?: Callback<observer.RouterPageInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | 是 | The type of event to remove the listener for. Must be 'routerPageUpdate'. |
| callback | Callback&lt;observer.RouterPageInfo&gt; | 否 | The callback function to remove. If not provided, allcallbacks for the given event typewill be removed. |

## off('densityUpdate')

```TypeScript
off(type: 'densityUpdate', callback?: Callback<observer.DensityInfo>): void
```

取消监听屏幕像素密度的变化。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'densityUpdate' | 是 | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| callback | Callback&lt;observer.DensityInfo&gt; | 否 | 需要被注销的回调函数。若不指定具体的回调函数，则注销该[UIContext](arkts-arkui-uicontext.md)下所有屏幕像素密度变化事件监听。 |

## off('willDraw')

```TypeScript
off(type: 'willDraw', callback?: Callback<void>): void
```

取消监听每一帧绘制指令下发情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willDraw' | 是 | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| callback | Callback&lt;void&gt; | 否 | 需要被注销的回调函数。不传参数时，取消所有绘制指令下发事件的监听回调。 |

## off('didLayout')

```TypeScript
off(type: 'didLayout', callback?: Callback<void>): void
```

取消监听每一帧布局完成情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| callback | Callback&lt;void&gt; | 否 | 需要被注销的回调函数。不传参数时，取消所有布局完成的监听回调。 |

## off('navDestinationSwitch')

```TypeScript
off(
    type: 'navDestinationSwitch',
    callback?: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to remove the listener for. Must be 'navDestinationSwitch'. |
| callback | Callback&lt;observer.NavDestinationSwitchInfo&gt; | 否 | The callback function to remove. If notprovided,all callbacks for the given event type will be removed. |

## off('navDestinationSwitch')

```TypeScript
off(
    type: 'navDestinationSwitch',
    observerOptions: observer.NavDestinationSwitchObserverOptions,
    callback?: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to remove the listener for. Must be 'navDestinationSwitch'. |
| observerOptions | observer.NavDestinationSwitchObserverOptions | 是 | Options. |
| callback | Callback&lt;observer.NavDestinationSwitchInfo&gt; | 否 | The callback function to remove. If notprovided,all callbacks for the given event type will be removed. |

## off('willClick')

```TypeScript
off(type: 'willClick', callback?: ClickEventListenerCallback): void
```

Removes a callback function to be called before clickEvent is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to remove the listener for. |
| callback | ClickEventListenerCallback | 否 | The callback function to remove. If not provided,all callbacks for the given event type will be removed. |

## off('didClick')

```TypeScript
off(type: 'didClick', callback?: ClickEventListenerCallback): void
```

Removes a callback function to be called after clickEvent is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to remove the listener for. |
| callback | ClickEventListenerCallback | 否 | The callback function to remove. If not provided,all callbacks for the given event type will be removed. |

## off('willClick')

```TypeScript
off(type: 'willClick', callback?: GestureEventListenerCallback): void
```

Removes a callback function to be called before tapGesture is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to remove the listener for. |
| callback | GestureEventListenerCallback | 否 | The callback function to remove. If not provided,all callbacks for the given event type will be removed. |

## off('didClick')

```TypeScript
off(type: 'didClick', callback?: GestureEventListenerCallback): void
```

Removes a callback function to be called after tapGesture is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to remove the listener for. |
| callback | GestureEventListenerCallback | 否 | The callback function to remove. If not provided,all callbacks for the given event type will be removed. |

## off('beforePanStart')

```TypeScript
off(type: 'beforePanStart', callback?: PanListenerCallback): void
```

取消[on('beforePanStart')](arkts-arkui-uiobserver-c.md#on-16)监听Pan手势
[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件执行前的callback回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanStart' | 是 | 监听事件，固定为'beforePanStart'，即Pan手势[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件执行前的指令下发情况。 |
| callback | PanListenerCallback | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件执行前的指令下发监听回调。 |

## off('beforePanEnd')

```TypeScript
off(type: 'beforePanEnd', callback?: PanListenerCallback): void
```

取消[on('beforePanEnd')](arkts-arkui-uiobserver-c.md#on-17)监听Pan手势
[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行前的callback回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanEnd' | 是 | 监听事件，固定为'beforePanEnd'，即Pan手势[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行前的指令下发情况。 |
| callback | PanListenerCallback | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行前的指令下发监听回调。 |

## off('afterPanStart')

```TypeScript
off(type: 'afterPanStart', callback?: PanListenerCallback): void
```

取消[on('afterPanStart')](arkts-arkui-uiobserver-c.md#on-18)监听Pan手势
[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件执行后的callback回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanStart' | 是 | 监听事件，固定为'afterPanStart'，即Pan手势[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件执行后的指令下发情况。 |
| callback | PanListenerCallback | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件执行后的指令下发监听回调。 |

## off('afterPanEnd')

```TypeScript
off(type: 'afterPanEnd', callback?: PanListenerCallback): void
```

取消[on('afterPanEnd')](arkts-arkui-uiobserver-c.md#on-19)监听Pan手势
[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行后的callback回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanEnd' | 是 | 监听事件，固定为'afterPanEnd'，即Pan手势[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行后的指令下发情况。 |
| callback | PanListenerCallback | 否 | 需要被注销的回调函数。不传参数时，取消所有的Pan手势[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行后的指令下发监听回调。 |

## off('tabContentUpdate')

```TypeScript
off(type: 'tabContentUpdate', options: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to remove the listener for. Must be 'tabContentUpdate'. |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | Callback&lt;observer.TabContentInfo&gt; | 否 | The callback function to remove. If not provided,all callbacks for the given event type and Tabs ID will be removed. |

## off('tabContentUpdate')

```TypeScript
off(type: 'tabContentUpdate', callback?: Callback<observer.TabContentInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to remove the listener for. Must be 'tabContentUpdate'. |
| callback | Callback&lt;observer.TabContentInfo&gt; | 否 | The callback function to remove. If not provided,all callbacks for the given event type and Tabs ID will be removed. |

## off('tabChange')

```TypeScript
off(type: 'tabChange', config: observer.ObserverOptions, callback?: Callback<observer.TabContentInfo>): void
```

移除之前通过 `on()` 注册的回调函数。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要移除监听的事件类型。必须是 'tabChange'。 |
| config | observer.ObserverOptions | 是 | 选项对象。包含监听的tabs组件ID。 |
| callback | Callback&lt;observer.TabContentInfo&gt; | 否 | 要移除的回调函数。如果未提供该参数，则将移除该tabs id的所有'tabChange'无感监听回调函数。 |

## off('tabChange')

```TypeScript
off(type: 'tabChange', callback?: Callback<observer.TabContentInfo>): void
```

移除之前通过 `on()` 注册的回调函数。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要移除监听的事件类型。必须是 'tabChange'。 |
| callback | Callback&lt;observer.TabContentInfo&gt; | 否 | 要移除的回调函数。如果未提供该参数，则将移除所有tabs的所有'tabChange'无感监听回调函数。 |

## off('windowSizeLayoutBreakpointChange')

```TypeScript
off(type: 'windowSizeLayoutBreakpointChange', callback?: Callback<observer.WindowSizeLayoutBreakpointInfo>): void
```

移除之前注册的窗口尺寸布局断点变化回调函数。如果未提供回调函数参数，将移除指定上下文的所有回调函数。使用callback异步回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeLayoutBreakpointChange' | 是 | 监听事件，固定为'windowSizeLayoutBreakpointChange'，用于监听窗口尺寸布局断点发生改变。 |
| callback | Callback&lt;observer.WindowSizeLayoutBreakpointInfo&gt; | 否 | 需要被注销的回调函数。若不指定具体的回调函数，则注销该[UIContext](arkts-arkui-uicontext.md)下所有窗口尺寸布局断点变化事件监听。 |

## off('nodeRenderState')

```TypeScript
off(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback?: NodeRenderStateChangeCallback): void
```

取消监听节点渲染状态发生变化的callback回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'nodeRenderState' | 是 | 监听事件，固定为'nodeRenderState'，即节点渲染状态变化指令下发情况。 |
| nodeIdentity | NodeIdentity | 是 | 节点标识。 |
| callback | NodeRenderStateChangeCallback | 否 | 需要被注销的回调函数。不传参数时，取消该节点所有的渲染状态变化指令下发监听回调。 |

## off('textChange')

```TypeScript
off(type: 'textChange', callback?: Callback<observer.TextChangeEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to remove the listener for. Must be 'textChange'. |
| callback | Callback&lt;observer.TextChangeEventInfo&gt; | 否 | The callback function to remove. If not provided,all callbacks for the given event type will be removed. |

## off('textChange')

```TypeScript
off(type: 'textChange', identity: observer.ObserverOptions, callback?: Callback<observer.TextChangeEventInfo>): void
```

Removes a callback function that was previously registered with `on()`.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to remove the listener for. Must be 'textChange'. |
| identity | observer.ObserverOptions | 是 | Identity options. |
| callback | Callback&lt;observer.TextChangeEventInfo&gt; | 否 | The callback function to remove. If not provided,all callbacks for the given event type will be removed. |

## offNavDestinationSizeChange

```TypeScript
offNavDestinationSizeChange(callback?: Callback<observer.NavDestinationInfo>): void
```

移除使用onNavDestinationSizeChange接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;observer.NavDestinationInfo&gt; | 否 | 需要被移除的回调函数。不传参数时，移除所有回调函数。 |

## offNavDestinationSizeChangeByUniqueId

```TypeScript
offNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback?: Callback<observer.NavDestinationInfo>): void
```

移除使用onNavDestinationSizeChangeByUniqueId接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navigationUniqueId | number | 是 | 希望监听的NavDestination所属的Navigation的唯一ID，可以通过 [queryNavigationInfo]{@linkBaseCustomComponent#queryNavigationInfo}获取。 |
| callback | Callback&lt;observer.NavDestinationInfo&gt; | 否 | 需要被移除的回调函数。不传参数时，移除所有指定了相同navigationUniqueId的回调函数。 |

## offRouterPageSizeChange

```TypeScript
offRouterPageSizeChange(callback?: Callback<observer.RouterPageInfo>): void
```

移除使用onRouterPageSizeChange接口注册的监听回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;observer.RouterPageInfo&gt; | 否 | 需要被移除的回调函数。不传参数时，移除所有回调函数。 |

## offSwiperContentUpdate

```TypeScript
offSwiperContentUpdate(callback?: Callback<SwiperContentInfo>): void
```

取消监听Swiper内容的切换事件。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;SwiperContentInfo&gt; | 否 | 需要被注销的回调函数。不传参数时，取消该Swiper上所有的监听回调。 |

## offSwiperContentUpdate

```TypeScript
offSwiperContentUpdate(config: observer.ObserverOptions, callback?: Callback<SwiperContentInfo>): void
```

取消通过Swiper组件id监听的Swiper内容切换事件。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | observer.ObserverOptions | 是 | 指定监听的Swiper组件信息。 |
| callback | Callback&lt;SwiperContentInfo&gt; | 否 | 需要被注销的回调函数。不传参数时，取消该Swiper上所有的监听回调。 |

## on('navDestinationUpdate')

```TypeScript
on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback<observer.NavDestinationInfo>): void
```

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | Event type.The value is fixed at **'navDestinationUpdate'**, which indicates the state change event<br>of the **NavDestination** component. |
| options | { navigationId: ResourceStr } | 是 | ID of the target **NavDestination** component. |
| callback | Callback&lt;observer.NavDestinationInfo&gt; | 是 | Callback used to return the current<br>state of the **NavDestination** component. |

## on('navDestinationUpdate')

```TypeScript
on(type: 'navDestinationUpdate', callback: Callback<observer.NavDestinationInfo>): void
```

Subscribes to status changes of this **NavDestination** component.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdate' | 是 | Event type.The value is fixed at **'navDestinationUpdate'**,<br>which indicates the state change event of the **NavDestination** component. |
| callback | Callback&lt;observer.NavDestinationInfo&gt; | 是 | Callback used to return the current state of<br>the **NavDestination** component. |

## on('navDestinationUpdateByUniqueId')

```TypeScript
on(type: 'navDestinationUpdateByUniqueId', navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void
```

Registers a callback function to be called when the navigation destination is updated.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationUpdateByUniqueId' | 是 | The type of event to listen for. Must be 'navDestinationUpdateByUniqueId'. |
| navigationUniqueId | number | 是 | The uniqueId of the navigation. |
| callback | Callback&lt;observer.NavDestinationInfo&gt; | 是 | The callback function to be called when the navigationdestination is updated. |

## on('scrollEvent')

```TypeScript
on(type: 'scrollEvent', options: observer.ObserverOptions, callback: Callback<observer.ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | Callback&lt;observer.ScrollEventInfo&gt; | 是 | The callback function to be called when the scroll eventstart or stop. |

## on('scrollEvent')

```TypeScript
on(type: 'scrollEvent', callback: Callback<observer.ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| callback | Callback&lt;observer.ScrollEventInfo&gt; | 是 | The callback function to be called when the scroll eventstart or stop. |

## on('routerPageUpdate')

```TypeScript
on(type: 'routerPageUpdate', callback: Callback<observer.RouterPageInfo>): void
```

Unsubscribes to state changes of the page in the router.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'routerPageUpdate' | 是 | Event type.<br>The value is fixed at 'routerPageUpdate', which indicates the state change event of the page in the router. |
| callback | Callback&lt;observer.RouterPageInfo&gt; | 是 | Callback to be unregistered. |

## on('densityUpdate')

```TypeScript
on(type: 'densityUpdate', callback: Callback<observer.DensityInfo>): void
```

监听屏幕像素密度变化。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'densityUpdate' | 是 | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| callback | Callback&lt;observer.DensityInfo&gt; | 是 | 回调函数。携带[DensityInfo](arkts-arkui-densityinfo-c.md)，返回变化后的屏幕像素密度。 |

## on('willDraw')

```TypeScript
on(type: 'willDraw', callback: Callback<void>): void
```

监听每一帧绘制指令下发情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willDraw' | 是 | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| callback | Callback&lt;void&gt; | 是 | 回调函数。 |

## on('didLayout')

```TypeScript
on(type: 'didLayout', callback: Callback<void>): void
```

监听每一帧布局完成情况。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didLayout' | 是 | 监听事件，固定为'didLayout'，即是否布局完成。 |
| callback | Callback&lt;void&gt; | 是 | 回调函数。 |

## on('navDestinationSwitch')

```TypeScript
on(
    type: 'navDestinationSwitch',
    callback: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Registers a callback function to be called when the navigation switched to a new navDestination.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to listen for. Must be 'navDestinationSwitch'. |
| callback | Callback&lt;observer.NavDestinationSwitchInfo&gt; | 是 | The callback function to be called whenthe navigation switched to a new navDestination. |

## on('navDestinationSwitch')

```TypeScript
on(
    type: 'navDestinationSwitch',
    observerOptions: observer.NavDestinationSwitchObserverOptions,
    callback: Callback<observer.NavDestinationSwitchInfo>
  ): void
```

Registers a callback function to be called when the navigation switched to a new navDestination.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'navDestinationSwitch' | 是 | The type of event to listen for. Must be 'navDestinationSwitch'. |
| observerOptions | observer.NavDestinationSwitchObserverOptions | 是 | Options. |
| callback | Callback&lt;observer.NavDestinationSwitchInfo&gt; | 是 | The callback function to be called when thenavigation switched to a new navDestination. |

## on('willClick')

```TypeScript
on(type: 'willClick', callback: ClickEventListenerCallback): void
```

Registers a callback function to be called before clickEvent is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to listen for. |
| callback | ClickEventListenerCallback | 是 | The callback function to be calledwhen the clickEvent will be trigger or after. |

## on('didClick')

```TypeScript
on(type: 'didClick', callback: ClickEventListenerCallback): void
```

Registers a callback function to be called after clickEvent is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to listen for. |
| callback | ClickEventListenerCallback | 是 | The callback function to be calledwhen the clickEvent will be trigger or after. |

## on('willClick')

```TypeScript
on(type: 'willClick', callback: GestureEventListenerCallback): void
```

Registers a callback function to be called before tapGesture is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'willClick' | 是 | The type of event to listen for. |
| callback | GestureEventListenerCallback | 是 | The callback function to be calledwhen the clickEvent will be trigger or after. |

## on('didClick')

```TypeScript
on(type: 'didClick', callback: GestureEventListenerCallback): void
```

Registers a callback function to be called after tapGesture is called.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'didClick' | 是 | The type of event to listen for. |
| callback | GestureEventListenerCallback | 是 | The callback function to be calledwhen the clickEvent will be trigger or after. |

## on('beforePanStart')

```TypeScript
on(type: 'beforePanStart', callback: PanListenerCallback): void
```

监听Pan手势[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件，在
[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件执行之前执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanStart' | 是 | 监听事件，固定为'beforePanStart'，用于监听Pan手势[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件执行前的指令下发情况，所注册回调将于Pan手势[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件触发前触发。 |
| callback | PanListenerCallback | 是 | 回调函数。可以获得Pan手势事件的[GestureEvent](../arkts-components/arkts-arkui-gestureevent-i.md)，[GestureRecognizer](../arkts-components/arkts-arkui-gesturerecognizer-c.md)和组件的[FrameNode](arkts-arkui-framenode-c.md)。 |

## on('beforePanEnd')

```TypeScript
on(type: 'beforePanEnd', callback: PanListenerCallback): void
```

监听Pan手势[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行前的指令下发情况，在
[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行之前执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'beforePanEnd' | 是 | 监听事件，固定为'beforePanEnd'，用于监听Pan手势[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行前的指令下发情况，所注册回调将于Pan手势[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件触发前触发。 |
| callback | PanListenerCallback | 是 | 回调函数。可以获得Pan手势事件的[GestureEvent](../arkts-components/arkts-arkui-gestureevent-i.md)，[GestureRecognizer](../arkts-components/arkts-arkui-gesturerecognizer-c.md)和组件的[FrameNode](arkts-arkui-framenode-c.md)。 |

## on('afterPanStart')

```TypeScript
on(type: 'afterPanStart', callback: PanListenerCallback): void
```

监听Pan手势[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件执行后的指令下发情况，在
[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件执行之后执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanStart' | 是 | 监听事件，固定为'afterPanStart'，用于监听Pan手势[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件执行后的指令下发情况，所注册回调将于Pan手势[onActionStart](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionstart-1)事件触发后触发。 |
| callback | PanListenerCallback | 是 | 回调函数。可以获得Pan手势事件的[GestureEvent](../arkts-components/arkts-arkui-gestureevent-i.md)，[GestureRecognizer](../arkts-components/arkts-arkui-gesturerecognizer-c.md)和组件的[FrameNode](arkts-arkui-framenode-c.md)。 |

## on('afterPanEnd')

```TypeScript
on(type: 'afterPanEnd', callback: PanListenerCallback): void
```

监听Pan手势[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行后的指令下发情况，在
[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行之后执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'afterPanEnd' | 是 | 监听事件，固定为'afterPanEnd'，用于监听Pan手势[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件执行后的指令下发情况，所注册回调将于Pan手势[onActionEnd](../arkts-components/arkts-arkui-pangestureinterface-i.md#onactionend-1)事件触发后触发。 |
| callback | PanListenerCallback | 是 | 回调函数。可以获得Pan手势事件的[GestureEvent](../arkts-components/arkts-arkui-gestureevent-i.md)，[GestureRecognizer](../arkts-components/arkts-arkui-gesturerecognizer-c.md)和组件的[FrameNode](arkts-arkui-framenode-c.md)。 |

## on('tabContentUpdate')

```TypeScript
on(type: 'tabContentUpdate', options: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void
```

Registers a callback function to be called when the tabContent is showed or hidden.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to listen for. Must be 'tabContentUpdate'. |
| options | observer.ObserverOptions | 是 | The options object. |
| callback | Callback&lt;observer.TabContentInfo&gt; | 是 | The callback function to be calledwhen the tabContent show or hide. |

## on('tabContentUpdate')

```TypeScript
on(type: 'tabContentUpdate', callback: Callback<observer.TabContentInfo>): void
```

Registers a callback function to be called when the tabContent is showed or hidden.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabContentUpdate' | 是 | The type of event to listen for. Must be 'tabContentUpdate'. |
| callback | Callback&lt;observer.TabContentInfo&gt; | 是 | The callback function to be calledwhen the tabContent is showed or hidden. |

## on('tabChange')

```TypeScript
on(type: 'tabChange', config: observer.ObserverOptions, callback: Callback<observer.TabContentInfo>): void
```

注册一个回调函数，当 tabContent 显示或隐藏时被调用。包括tabs首次加载时的tabContent显示情况以及 tabs 索引切换时tabContent显示情况。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要监听的事件类型。必须是 'tabChange'。 |
| config | observer.ObserverOptions | 是 | 选项对象。包含监听的tabs组件ID。 |
| callback | Callback&lt;observer.TabContentInfo&gt; | 是 | 回调函数，当 tabContent 显示或隐藏时被调用。 |

## on('tabChange')

```TypeScript
on(type: 'tabChange', callback: Callback<observer.TabContentInfo>): void
```

注册一个回调函数，当 tabContent 显示或隐藏时被调用。包括tabs首次加载时的tabContent显示情况以及 tabs 索引切换时tabContent显示情况。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'tabChange' | 是 | 要监听的事件类型。必须是 'tabChange'。 |
| callback | Callback&lt;observer.TabContentInfo&gt; | 是 | 回调函数，当 tabContent 显示或隐藏时调用。 |

## on('windowSizeLayoutBreakpointChange')

```TypeScript
on(type: 'windowSizeLayoutBreakpointChange', callback: Callback<observer.WindowSizeLayoutBreakpointInfo>): void
```

注册窗口尺寸布局断点变化的回调函数。该方法用于监听窗口尺寸断点变化，可用于根据窗口尺寸自适应调整UI布局。使用callback异步回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'windowSizeLayoutBreakpointChange' | 是 | 监听事件，固定为'windowSizeLayoutBreakpointChange'，用于监听窗口尺寸布局断点发生改变。 |
| callback | Callback&lt;observer.WindowSizeLayoutBreakpointInfo&gt; | 是 | 回调函数。携带WindowSizeLayoutBreakpointinfo，包含窗口宽度和高度所在的布局断点枚举。 |

## on('nodeRenderState')

```TypeScript
on(type: 'nodeRenderState', nodeIdentity: NodeIdentity, callback: NodeRenderStateChangeCallback): void
```

注册一个回调函数，以便在特定节点的渲染状态发生变化时调用，当注册成功时，此回调将立即执行一次。

注意节点数量的限制。出于性能考虑，在单个UI实例中，注册节点太多，将会抛出异常。

通常，当组件被移动到屏幕外时，会收到RENDER_OUT的通知。但在某些情况下，即使组件移动到屏幕外也不会触发RENDER_OUT通知。例如，具有缓存功能的组件[Swiper](../arkts-components/arkts-arkui-swiper.md)，即使
[cachedCount](SwiperAttribute#cachedCount(count: number, isShown: boolean))属性中的参数isShown配置为true，也不会触发
RENDER_OUT通知。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'nodeRenderState' | 是 | 监听事件，固定为'nodeRenderState'，用于监听节点渲染状态发生改变。 |
| nodeIdentity | NodeIdentity | 是 | 节点标识。 |
| callback | NodeRenderStateChangeCallback | 是 | 回调函数。可以获得节点渲染状态改变事件的[NodeRenderState](arkts-arkui-noderenderstate-e.md)和组件的[FrameNode](arkts-arkui-framenode-c.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [161001](../errorcode-node-render-monitor.md#161001-监听渲染状态的节点数超过限制) | The count of nodes monitoring render state is over the limitation. |

## on('textChange')

```TypeScript
on(type: 'textChange', callback: Callback<observer.TextChangeEventInfo>): void
```

Registers a callback function to be called when text field's content is changed.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to listen for. Must be 'textChange'. |
| callback | Callback&lt;observer.TextChangeEventInfo&gt; | 是 | The callback function to be called whentext field's content is changed. |

## on('textChange')

```TypeScript
on(type: 'textChange', identity: observer.ObserverOptions, callback: Callback<observer.TextChangeEventInfo>): void
```

Registers a callback function to be called when text field's content is changed.

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | The type of event to listen for. Must be 'textChange'. |
| identity | observer.ObserverOptions | 是 | Identity options. |
| callback | Callback&lt;observer.TextChangeEventInfo&gt; | 是 | The callback function to be called when thetext field's content is changed. |

## onNavDestinationSizeChange

```TypeScript
onNavDestinationSizeChange(callback: Callback<observer.NavDestinationInfo>): void
```

注册监听回调函数，当可见的NavDestination大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;observer.NavDestinationInfo&gt; | 是 | 回调函数。携带NavDestinationInfo，返回NavDestination的信息。 |

## onNavDestinationSizeChangeByUniqueId

```TypeScript
onNavDestinationSizeChangeByUniqueId(navigationUniqueId: number, callback: Callback<observer.NavDestinationInfo>): void
```

注册监听回调函数，当属于指定Navigation的可见NavDestination的大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| navigationUniqueId | number | 是 | 希望监听NavDestination所属的Navigation的唯一ID，可以通过[queryNavigationInfo]{@linkBaseCustomComponent#queryNavigationInfo}获取。 |
| callback | Callback&lt;observer.NavDestinationInfo&gt; | 是 | Callback to be removed. If no parameter is passed,all callbacks with the same **navigationUniqueId** setting are removed. |

## onRouterPageSizeChange

```TypeScript
onRouterPageSizeChange(callback: Callback<observer.RouterPageInfo>): void
```

注册一个callback，当router可见页面尺寸发生变化时触发注册监听回调函数，当可见的Router页面大小发生变化时，会触发该回调函数。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;observer.RouterPageInfo&gt; | 是 | 回调函数。携带RouterPageInfo，返回Router页面的信息。 |

## onSwiperContentUpdate

```TypeScript
onSwiperContentUpdate(callback: Callback<SwiperContentInfo>): void
```

监听Swiper内容的切换事件。使用callback异步回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;SwiperContentInfo&gt; | 是 | 回调函数。携带SwiperContentInfo，返回Swiper内容切换的信息。 |

## onSwiperContentUpdate

```TypeScript
onSwiperContentUpdate(config: observer.ObserverOptions, callback: Callback<SwiperContentInfo>): void
```

通过Swiper组件的id监听Swiper内容的切换事件。使用callback异步回调。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | observer.ObserverOptions | 是 | 指定监听的Swiper组件信息。 |
| callback | Callback&lt;SwiperContentInfo&gt; | 是 | 回调函数。携带SwiperContentInfo，返回Swiper内容切换的信息。 |

## removeGlobalGestureListener

```TypeScript
removeGlobalGestureListener(type: GestureListenerType, callback?: GestureListenerCallback): void
```

移除某一手势监听器类型的回调函数。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | GestureListenerType | 是 | 要移除监听器的事件类型。 |
| callback | GestureListenerCallback | 否 | 待移除的回调函数（未提供时将清除该手势类型的所有回调）。 |

