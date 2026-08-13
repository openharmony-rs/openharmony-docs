# NodeController

NodeController用于管理自定义节点的创建、显示、更新等操作，并负责将自定义节点挂载到NodeContainer上，适用于 需要在页面中动态创建、更新、复用自定义节点的场景。 > **说明：** > > - NodeController对象不支持使用JSON序列化。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-export abstract class NodeController--><!--Device-unnamed-export abstract class NodeController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
aboutToAppear?(): void
```

当NodeController绑定的NodeContainer挂载显示后触发此回调。 > **说明：** > > 回调时机参考onAppear。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToAppear?(): void--><!--Device-NodeController-aboutToAppear?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
aboutToDisappear?(): void
```

当NodeController绑定的NodeContainer销毁时触发此回调。 > **说明：** > > 回调时机参考onDisAppear。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToDisappear?(): void--><!--Device-NodeController-aboutToDisappear?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToResize

```TypeScript
aboutToResize?(size: Size): void
```

当NodeController绑定的NodeContainer布局时触发此回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-aboutToResize?(size: Size): void--><!--Device-NodeController-aboutToResize?(size: Size): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [Size](../../apis-na/arkts-apis/arkts-na-graphics-size-i.md) | 是 | 组件布局大小的宽和高，单位为vp。 |

## makeNode

```TypeScript
abstract makeNode(uiContext: UIContext): FrameNode | null
```

当NodeController绑定的NodeContainer创建时触发此回调。回调方法将返回一个节点，该节点将被挂载至 NodeContainer。 或者可以通过NodeController的rebuild()方法触发回调。 > **说明：** > > NodeContainer不支持跨实例复用。如果出现跨实例复用 > NodeContainer，传入 > NodeContainer的[NodeController](../../apis-na/arkts-apis/arkts-na-nodecontroller-c.md#NodeController)触发 > [makeNode](../../apis-na/arkts-apis/arkts-na-nodecontroller-c.md#makeNode)回调方法时，入参中的[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md#UIContext)对象可能为undefined，此时需要开发者 > 判断该对象是否为undefined，防止后续使用此入参时出现[UIContext无效的JS异常](../../../ui/arkts-wrong-uicontext-debug.md#定位uicontext错误问题)。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-abstract makeNode(uiContext: UIContext): FrameNode | null--><!--Device-NodeController-abstract makeNode(uiContext: UIContext): FrameNode | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | 回调该方法时，绑定NodeContainer的UI上下文。跨实 例复用NodeContainer时，该参数可能为undefined，需要开发者自行判断。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameNode](../../apis-na/arkts-apis/arkts-na-framenode-c.md) | 一个FrameNode对象，返回的节点将被挂载至 [NodeContainer]{ |

## onAttach

```TypeScript
onAttach?(): void
```

当NodeController绑定的NodeContainer挂载至主节点树时触发此回调。与 [aboutToAppear](../../apis-na/arkts-apis/arkts-na-nodecontroller-c.md#aboutToAppear)不同，aboutToAppear在NodeContainer挂载显示后触发，onAttach在NodeContainer挂载至主 节点树时触发，两者触发时机可能不同。 > **说明：** > > 回调时机参考onAttach。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onAttach?(): void--><!--Device-NodeController-onAttach?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBind

```TypeScript
onBind?(containerId: number): void
```

当NodeController与NodeContainer绑定后触发此回调。该回调后于 [onWillBind](../../apis-na/arkts-apis/arkts-na-nodecontroller-c.md#onWillBind)触发，两者均为可选回调，可根据需要在绑定前或绑定后执行相应逻辑。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onBind?(containerId: number): void--><!--Device-NodeController-onBind?(containerId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | number | 是 | 回调该方法时，已完成与NodeController绑定的 NodeContainer的标识。 |

## onDetach

```TypeScript
onDetach?(): void
```

当NodeController绑定的NodeContainer从主节点树卸载时触发此回调。与 [aboutToDisappear](../../apis-na/arkts-apis/arkts-na-nodecontroller-c.md#aboutToDisappear)不同，aboutToDisappear在NodeContainer销毁时触发，onDetach在 NodeContainer从主节点树卸载时触发，两者触发时机可能不同。 > **说明：** > > 回调时机参考onDetach。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onDetach?(): void--><!--Device-NodeController-onDetach?(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onTouchEvent

```TypeScript
onTouchEvent?(event: TouchEvent): void
```

当NodeController绑定的NodeContainer收到触摸事件时触发此回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onTouchEvent?(event: TouchEvent): void--><!--Device-NodeController-onTouchEvent?(event: TouchEvent): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | TouchEvent | 是 | 触摸事件，包含触摸点的坐标、触摸动作类型等信息，具体结构详见TouchEvent。 |

## onUnbind

```TypeScript
onUnbind?(containerId: number): void
```

当NodeController与NodeContainer解绑后触发此回调。该回调后于 [onWillUnbind](../../apis-na/arkts-apis/arkts-na-nodecontroller-c.md#onWillUnbind)触发，两者均为可选回调，可根据需要在解绑前或解绑后执行相应逻辑。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onUnbind?(containerId: number): void--><!--Device-NodeController-onUnbind?(containerId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | number | 是 | 回调该方法时，已完成与NodeController解绑的 NodeContainer的标识。 |

## onWillBind

```TypeScript
onWillBind?(containerId: number): void
```

当NodeController与NodeContainer即将绑定前触发此回调。该回调先于 [onBind](../../apis-na/arkts-apis/arkts-na-nodecontroller-c.md#onBind)触发，两者均为可选回调，可根据需要在绑定前或绑定后执行相应逻辑。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onWillBind?(containerId: number): void--><!--Device-NodeController-onWillBind?(containerId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | number | 是 | 回调该方法时，即将与NodeController绑定的 NodeContainer的标识。 |

## onWillUnbind

```TypeScript
onWillUnbind?(containerId: number): void
```

当NodeController与NodeContainer即将解绑前触发此回调。该回调先于 [onUnbind](../../apis-na/arkts-apis/arkts-na-nodecontroller-c.md#onUnbind)触发，两者均为可选回调，可根据需要在解绑前或解绑后执行相应逻辑。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-onWillUnbind?(containerId: number): void--><!--Device-NodeController-onWillUnbind?(containerId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| containerId | number | 是 | 回调该方法时，即将与NodeController解绑的 NodeContainer的标识。 |

## rebuild

```TypeScript
rebuild(): void
```

调用此接口通知NodeContainer组件重新回调 [makeNode](../../apis-na/arkts-apis/arkts-na-nodecontroller-c.md#makeNode)方法，更改子节点。例如，当NodeContainer展示的内容数据发生变化、需要更新显示的子节点时，可调用此方法触发重新构建。 > **说明：** > > 由于rebuild方法为应用主动调用的方法，且该操作与UI相关，需要开发者自行保证调用该接口时UI上下文有效，即与绑定的NodeContainer保持UI上下文一致。 > > 监听回调等[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)时，可以通过[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md#UIContext)的 > [runScopedTask](arkts-arkui-arkui-uicontext-uicontext-c.md#runScopedTask)方法明确调用时的UI上下文。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeController-rebuild(): void--><!--Device-NodeController-rebuild(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

