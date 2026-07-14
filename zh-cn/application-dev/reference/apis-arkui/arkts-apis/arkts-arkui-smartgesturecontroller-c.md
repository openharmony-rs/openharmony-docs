# SmartGestureController

提供智慧手势使能、监听、选中态控制，以及动态决策智慧手势行为的能力。

> **说明：**
>
> 以下API需先使用UIContext中的[getSmartGestureController()](arkts-arkui-uicontext-c.md#getsmartgesturecontroller-1)方法获取SmartGestureController实例，
> 再通过该实例调用对应方法。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clearMonitors

```TypeScript
clearMonitors(): void
```

清空当前UIContext下注册的全部智慧手势监听回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## clearSelected

```TypeScript
clearSelected(): void
```

清空当前智慧手势选中节点。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableSmartTapAndSlideGestures

```TypeScript
enableSmartTapAndSlideGestures(enabled: boolean): void
```

设置是否启用智慧手势的敲一敲和划一划操作。

> **说明：**
>
> - 该接口仅影响智慧手势的敲一敲和划一划手势，不影响翻腕手势。
>
> - 关闭后，组件侧[smartGestureShortcut](../arkts-components/arkts-arkui-commonmethod-c.md#smartgestureshortcut-1)配置仍会保留，但不会响应智慧手势的敲一敲和划一划手势。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否启用智慧手势的敲一敲和划一划手势处理。true表示启用，false表示关闭。 |

## registerMonitor

```TypeScript
registerMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void
```

注册智慧手势监听回调。在系统处理当前智慧手势前，应用可接收当前手势的默认动作处理并进行自定义干预。使用callback异步回调。

> **说明：**
>
> - 该接口使应用能够在系统处理当前智慧手势事件前接收其处理意图，并进行自定义干预。
>
> - 用户可通过该回调自定义决策本次智慧手势的行为。
>
> - 用户可注册多个监听回调，按照后注册先执行的顺序触发，当某个监听回调消费智慧手势事件后，即返回值[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md).
> isConsumed为true时，后续监听回调不再执行。
>
> - 当用户重复注册相同回调时，只会保存首次注册的回调，重复注册不生效。
>
> - 回调返回值必须是合法的[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md)实例，否则本次改写不生效。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monitorCallback | Callback&lt;BaseGestureHandlingProposal, GestureHandlingResolution&gt; | 是 | 智慧手势监听回调。回调参数为系统给出的默认动作处理，返回值用于声明是否消费当前智慧手势以及是否替换默认动作处理。 |

## requestSelected

```TypeScript
requestSelected(id: string): void
```

请求将指定组件设置为当前智慧手势选中节点。成功选中后会显示选中提示框，选中框样式根据设备有所不同。

> **说明：**
>
> - 仅当目标组件满足以下全部条件时，请求才会生效：组件可以响应智慧手势，且组件在屏幕内可见，且组件绑定了
> [onClick](../arkts-components/arkts-arkui-commonmethod-c.md#onclick-2)或绑定了单击手势[TapGesture](TapGesture)。
>
> - 组件能否响应智慧手势由[smartGestureShortcut](../arkts-components/arkts-arkui-commonmethod-c.md#smartgestureshortcut-1)中的enabled决定。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 组件的[id](../arkts-components/arkts-arkui-commonmethod-c.md#id-1)。 |

## unregisterMonitor

```TypeScript
unregisterMonitor(monitorCallback: Callback<BaseGestureHandlingProposal, GestureHandlingResolution>): void
```

注销智慧手势监听回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monitorCallback | Callback&lt;BaseGestureHandlingProposal, GestureHandlingResolution&gt; | 是 | 需要注销的智慧手势监听回调。 |

