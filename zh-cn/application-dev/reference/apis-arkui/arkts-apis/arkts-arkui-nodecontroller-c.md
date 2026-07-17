# NodeController

通常搭配{@link node_container}进行使用。用于创建控制器管理绑定的{@link node_container}组件。一个NodeController只允许与一个{@link node_container}进行绑定。最佳实践请参考[组件动态创建-组件动态添加、更新和删除](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-ui-dynamic-operations#section153921947151012)。

**起始版本：** 11

<!--Device-unnamed-export abstract class NodeController--><!--Device-unnamed-export abstract class NodeController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
aboutToAppear?(): void
```

当NodeController绑定的[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)挂载显示后触发此回调。

> **说明：**  
>  
> 回调时机参考[onAppear](../arkts-components/arkts-arkui-common-commonmethod-c.md#onappear-1)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToAppear?(): void--><!--Device-NodeController-aboutToAppear?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
aboutToDisappear?(): void
```

当NodeController绑定的[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)销毁时触发此回调。

> **说明：**  
>  
> 回调时机参考[onDisAppear](../arkts-components/arkts-arkui-common-commonmethod-c.md#ondisappear-1)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToDisappear?(): void--><!--Device-NodeController-aboutToDisappear?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToResize

```TypeScript
aboutToResize?(size: Size): void
```

当NodeController绑定的[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)布局的时候触发此回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToResize?(size: Size): void--><!--Device-NodeController-aboutToResize?(size: Size): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [Size](../arkts-components/arkts-arkui-canvas-size-i.md) | 是 | 用于返回组件布局大小的宽和高，单位为vp。 |

## makeNode

```TypeScript
abstract makeNode(uiContext: UIContext): FrameNode | null
```

当实例绑定的[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)创建的时候进行回调。回调方法将返回一个节点，将该节点挂载至[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)。

或者可以通过NodeController的rebuild()方法进行回调的触发。

> **说明：**  
>  
> [NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)不支持跨实例复用。如果出现跨实例复用[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)，传入  
> [NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)的[NodeController](arkts-arkui-nodecontroller-c.md)触发  
> [makeNode](arkts-arkui-nodecontroller-c.md#makenode-1)回调方法时，入参中的[UIContext](arkts-arkui-uicontext.md)对象可能为undefined，此时需要开发者  
> 判断入参中的[UIContext](arkts-arkui-uicontext.md)对象是否为undefined，防止后续使用此入参时出现  
> [UIContext无效的JS异常](../../../../ui/arkts-wrong-uicontext-debug.md#定位uicontext错误问题)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-abstract makeNode(uiContext: UIContext): FrameNode | null--><!--Device-NodeController-abstract makeNode(uiContext: UIContext): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](../arkts-components/arkts-arkui-uicontext-t.md) | 是 | 回调该方法的时候，绑定[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)的UI上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](../arkts-components/arkts-arkui-framenode-t.md) | **FrameNode** object, which will be mounted to the placeholder node of the [NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md) component. If a null object is returned, the child nodes of the corresponding [NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md) component are removed. |

## onAttach

```TypeScript
onAttach?(): void
```

当NodeController绑定的[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)挂载至主节点树时触发此回调。

> **说明：**  
>  
> 回调时机参考[onAttach](../arkts-components/arkts-arkui-common-commonmethod-c.md#onattach-1)。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onAttach?(): void--><!--Device-NodeController-onAttach?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBind

```TypeScript
onBind?(containerId: number): void
```

当NodeController与[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)绑定后触发此回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onBind?(containerId: number): void--><!--Device-NodeController-onBind?(containerId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | number | 是 | 回调该方法时，NodeController与NodeContainerId对应的[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)绑定完成。 |

## onDetach

```TypeScript
onDetach?(): void
```

当NodeController绑定的[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)从主节点树卸载时触发此回调。

> **说明：**  
>  
> 回调时机参考[onDetach](../arkts-components/arkts-arkui-common-commonmethod-c.md#ondetach-1)。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onDetach?(): void--><!--Device-NodeController-onDetach?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTouchEvent

```TypeScript
onTouchEvent?(event: TouchEvent): void
```

当NodeController绑定的[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)收到Touch事件时触发此回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onTouchEvent?(event: TouchEvent): void--><!--Device-NodeController-onTouchEvent?(event: TouchEvent): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [TouchEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-touchevent-touchevent-i.md) | 是 | 触摸事件。 |

## onUnbind

```TypeScript
onUnbind?(containerId: number): void
```

当NodeController与[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)解绑后触发此回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onUnbind?(containerId: number): void--><!--Device-NodeController-onUnbind?(containerId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | number | 是 | 回调该方法时，NodeController与NodeContainerId对应的[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)解绑完成。 |

## onWillBind

```TypeScript
onWillBind?(containerId: number): void
```

当NodeController与[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)即将绑定前触发此回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onWillBind?(containerId: number): void--><!--Device-NodeController-onWillBind?(containerId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | number | 是 | 回调该方法时，NodeController与NodeContainerId对应的[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)即将绑定。 |

## onWillUnbind

```TypeScript
onWillUnbind?(containerId: number): void
```

当NodeController与[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)即将解绑前触发此回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onWillUnbind?(containerId: number): void--><!--Device-NodeController-onWillUnbind?(containerId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | number | 是 | 回调该方法时，NodeController与NodeContainerId对应的[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)即将解绑。 |

## rebuild

```TypeScript
rebuild(): void
```

调用此接口通知[NodeContainer](../arkts-components/arkts-arkui-nodecontainer.md)组件重新回调[makeNode](arkts-arkui-nodecontroller-c.md#makenode-1)方法，更改子节点。

> **说明：**  
> > 由于rebuild方法为应用主动调用的方法，且该操作与UI相关。需要开发者自行保证调用该接口时UI上下文有效，即与绑定的NodeContainer保持UI上下文一致。  
>  
> 监听回调等[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)时，可以通过[UIContext](arkts-arkui-uicontext.md)的  
> [runScopedTask](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#runscopedtask)方法明确调用时的UI上下文。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-rebuild(): void--><!--Device-NodeController-rebuild(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

