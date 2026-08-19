# NodeController

NodeController用于实现自定义节点的创建、显示、更新等操作的管理，并负责将自定义节点挂载到NodeContainer上。 > **说明：** > > - NodeController对象不支持使用JSON序列化。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare abstract class NodeController--><!--Device-unnamed-export declare abstract class NodeController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
aboutToAppear(): void
```

> **说明：** > > 回调时机参考onAppear。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToAppear(): void--><!--Device-NodeController-aboutToAppear(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
aboutToDisappear(): void
```

> **说明：** > > 回调时机参考onDisAppear。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToDisappear(): void--><!--Device-NodeController-aboutToDisappear(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToResize

```TypeScript
aboutToResize(size: Size): void
```

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToResize(size: Size): void--><!--Device-NodeController-aboutToResize(size: Size): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [Size](../../apis-arkui/arkts-apis/arkts-arkui-graphics-size-i.md) | 是 | 用于返回组件布局大小的宽和高，单位为vp。 |

## makeNode

```TypeScript
abstract makeNode(uiContext: UIContext): FrameNode | null
```

当实例绑定的NodeContainer创建的时候进行回调。回调方法将返回一个节点，将该节点挂载至NodeContainer。 或者可以通过NodeController的rebuild()方法进行回调的触发。 > **说明：** > > NodeContainer不支持跨实例复用。如果出现跨实例复用NodeContainer，传入 > NodeContainer的[NodeController](#nodecontroller)触发 > [makeNode](#makenode)回调方法时，入参中的[UIContext](arkts-na-arkui-uicontext-uicontext-c.md)对象可能为undefined，此时需要开发者 > 判断入参中的[UIContext](arkts-na-arkui-uicontext-uicontext-c.md)对象是否为undefined，防止后续使用此入参时出现 > [UIContext无效的JS异常](../../../ui/arkts-wrong-uicontext-debug.md#定位uicontext错误问题)。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-abstract makeNode(uiContext: UIContext): FrameNode | null--><!--Device-NodeController-abstract makeNode(uiContext: UIContext): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-na-arkui-uicontext-uicontext-c.md) | 是 | 回调该方法的时候，绑定NodeContainer的UI上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md) | Returns a FrameNode or null. |

## onAttach

```TypeScript
onAttach(): void
```

> **说明：** > > 回调时机参考onAttach。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onAttach(): void--><!--Device-NodeController-onAttach(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBind

```TypeScript
onBind(containerId: long): void
```

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onBind(containerId: long): void--><!--Device-NodeController-onBind(containerId: long): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | long | 是 | 回调该方法时，NodeController与NodeContainerId对应的NodeContainer绑定完成。 |

## onDetach

```TypeScript
onDetach(): void
```

> **说明：** > > 回调时机参考onDetach。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onDetach(): void--><!--Device-NodeController-onDetach(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTouchEvent

```TypeScript
onTouchEvent(event: TouchEvent): void
```

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onTouchEvent(event: TouchEvent): void--><!--Device-NodeController-onTouchEvent(event: TouchEvent): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | TouchEvent | 是 | 触摸事件。 |

## onUnbind

```TypeScript
onUnbind(containerId: long): void
```

OnUnbind方法。解除NodeController与NodeContainer的绑定时执行。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onUnbind(containerId: long): void--><!--Device-NodeController-onUnbind(containerId: long): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | long | 是 | 回调该方法时，NodeController与NodeContainerId对应的NodeContainer解绑完成。 |

## onWillBind

```TypeScript
onWillBind(containerId: long): void
```

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onWillBind(containerId: long): void--><!--Device-NodeController-onWillBind(containerId: long): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | long | 是 | 回调该方法时，NodeController与NodeContainerId对应的NodeContainer即将绑定。 |

## onWillUnbind

```TypeScript
onWillUnbind(containerId: long): void
```

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onWillUnbind(containerId: long): void--><!--Device-NodeController-onWillUnbind(containerId: long): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | long | 是 | 回调该方法时，NodeController与NodeContainerId对应的NodeContainer即将解绑。 |

## rebuild

```TypeScript
rebuild(): void
```

调用此接口通知NodeContainer组件重新回调[makeNode](#makenode)方法，更改子节点。 > **说明：** > > 由于rebuild方法为应用主动调用的方法，且该操作与UI相关。需要开发者自行保证调用该接口时UI上下文有效，即与绑定的NodeContainer保持UI上下文一致。 > > 监听回调等[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)时，可以通过[UIContext](arkts-na-arkui-uicontext-uicontext-c.md)的 > [runScopedTask](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#runscopedtask)方法明确调用时的UI上下文。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-rebuild(): void--><!--Device-NodeController-rebuild(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

