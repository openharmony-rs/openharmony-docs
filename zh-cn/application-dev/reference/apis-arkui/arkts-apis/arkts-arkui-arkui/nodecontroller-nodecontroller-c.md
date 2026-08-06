# NodeController

NodeController用于实现自定义节点的创建、显示、更新等操作的管理，并负责将自定义节点挂载到[NodeContainer]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_上。 > **说明：** > > - NodeController对象不支持使用JSON序列化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare abstract class NodeController--><!--Device-unnamed-export declare abstract class NodeController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
aboutToAppear(): void
```

> **说明：** > > 回调时机参考[onAppear]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToAppear(): void--><!--Device-NodeController-aboutToAppear(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
aboutToDisappear(): void
```

> **说明：** > > 回调时机参考[onDisAppear]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToDisappear(): void--><!--Device-NodeController-aboutToDisappear(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToResize

```TypeScript
aboutToResize(size: Size): void
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToResize(size: Size): void--><!--Device-NodeController-aboutToResize(size: Size): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 用于返回组件布局大小的宽和高，单位为vp。 |

## makeNode

```TypeScript
abstract makeNode(uiContext: UIContext): FrameNode | null
```

当实例绑定的[NodeContainer]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_创建的时候进行回调。回调方法将返回一个节点，将该节点挂载至[NodeContainer]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_。 或者可以通过NodeController的rebuild()方法进行回调的触发。 > **说明：** > > [NodeContainer]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_不支持跨实例复用。如果出现跨实例复用[NodeContainer]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_，传入 > [NodeContainer]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_的[NodeController]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_触发 > [makeNode]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_回调方法时，入参中的[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_对象可能为undefined，此时需要开发者 > 判断入参中的[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_9\_\_\_对象是否为undefined，防止后续使用此入参时出现 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-abstract makeNode(uiContext: UIContext): FrameNode | null--><!--Device-NodeController-abstract makeNode(uiContext: UIContext): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调该方法的时候，绑定[NodeContainer]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的UI上下文。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | - Returns a FrameNode or null. |

## onAttach

```TypeScript
onAttach(): void
```

> **说明：** > > 回调时机参考[onAttach]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onAttach(): void--><!--Device-NodeController-onAttach(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBind

```TypeScript
onBind(containerId: long): void
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onBind(containerId: long): void--><!--Device-NodeController-onBind(containerId: long): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | long | 是 | 回调该方法时，NodeController与NodeContainerId对应的[NodeContainer]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_绑定完成。 |

## onDetach

```TypeScript
onDetach(): void
```

> **说明：** > > 回调时机参考[onDetach]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onDetach(): void--><!--Device-NodeController-onDetach(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTouchEvent

```TypeScript
onTouchEvent(event: TouchEvent): void
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onTouchEvent(event: TouchEvent): void--><!--Device-NodeController-onTouchEvent(event: TouchEvent): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 触摸事件。 |

## onUnbind

```TypeScript
onUnbind(containerId: long): void
```

OnUnbind方法。解除NodeController与NodeContainer的绑定时执行。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onUnbind(containerId: long): void--><!--Device-NodeController-onUnbind(containerId: long): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | long | 是 | 回调该方法时，NodeController与NodeContainerId对应的[NodeContainer]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_解绑完成。 |

## onWillBind

```TypeScript
onWillBind(containerId: long): void
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onWillBind(containerId: long): void--><!--Device-NodeController-onWillBind(containerId: long): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | long | 是 | 回调该方法时，NodeController与NodeContainerId对应的[NodeContainer]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_即将绑定。 |

## onWillUnbind

```TypeScript
onWillUnbind(containerId: long): void
```

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onWillUnbind(containerId: long): void--><!--Device-NodeController-onWillUnbind(containerId: long): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | long | 是 | 回调该方法时，NodeController与NodeContainerId对应的[NodeContainer]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_即将解绑。 |

## rebuild

```TypeScript
rebuild(): void
```

调用此接口通知[NodeContainer]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_组件重新回调[makeNode]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_方法，更改子节点。 > **说明：** > > 由于rebuild方法为应用主动调用的方法，且该操作与UI相关。需要开发者自行保证调用该接口时UI上下文有效，即与绑定的NodeContainer保持UI上下文一致。 > > 监听回调等\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_时，可以通过[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_的 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_方法明确调用时的UI上下文。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-rebuild(): void--><!--Device-NodeController-rebuild(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

