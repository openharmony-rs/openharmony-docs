# TreeListenerV2

树视图组件的监听器，可以将此对象绑定至树视图组件，然后通过它监听树视图的节点的变化，同一个树视图监听器不可以控制多个树视图组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class TreeListenerV2--><!--Device-unnamed-export declare class TreeListenerV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offNodeAdd

```TypeScript
offNodeAdd(callback?: OnChangedCallback): void
```

取消节点添加事件监听。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-offNodeAdd(callback?: OnChangedCallback): void--><!--Device-TreeListenerV2-offNodeAdd(callback?: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 否 |  |

## offNodeClick

```TypeScript
offNodeClick(callback?: OnChangedCallback): void
```

取消节点点击事件监听。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-offNodeClick(callback?: OnChangedCallback): void--><!--Device-TreeListenerV2-offNodeClick(callback?: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 否 |  |

## offNodeDelete

```TypeScript
offNodeDelete(callback?: OnChangedCallback): void
```

取消节点删除事件监听。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-offNodeDelete(callback?: OnChangedCallback): void--><!--Device-TreeListenerV2-offNodeDelete(callback?: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 否 |  |

## offNodeModify

```TypeScript
offNodeModify(callback?: OnChangedCallback): void
```

取消节点修改事件监听。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-offNodeModify(callback?: OnChangedCallback): void--><!--Device-TreeListenerV2-offNodeModify(callback?: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 否 |  |

## offNodeMove

```TypeScript
offNodeMove(callback?: OnChangedCallback): void
```

取消节点移动事件监听。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-offNodeMove(callback?: OnChangedCallback): void--><!--Device-TreeListenerV2-offNodeMove(callback?: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 否 |  |

## onNodeAdd

```TypeScript
onNodeAdd(callback: OnChangedCallback): void
```

注册节点添加事件监听，持续监听节点添加事件。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-onNodeAdd(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onNodeAdd(callback: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 是 |  |

## onNodeClick

```TypeScript
onNodeClick(callback: OnChangedCallback): void
```

注册节点点击事件监听，持续监听节点点击事件。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-onNodeClick(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onNodeClick(callback: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 是 |  |

## onNodeDelete

```TypeScript
onNodeDelete(callback: OnChangedCallback): void
```

注册节点删除事件监听，持续监听节点删除事件。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-onNodeDelete(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onNodeDelete(callback: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 是 |  |

## onNodeModify

```TypeScript
onNodeModify(callback: OnChangedCallback): void
```

注册节点修改事件监听，持续监听节点修改事件。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-onNodeModify(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onNodeModify(callback: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 是 |  |

## onNodeMove

```TypeScript
onNodeMove(callback: OnChangedCallback): void
```

注册节点移动事件监听，持续监听节点移动事件。节点移动通过拖拽操作触发。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-onNodeMove(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onNodeMove(callback: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 是 |  |

## onceNodeAdd

```TypeScript
onceNodeAdd(callback: OnChangedCallback): void
```

注册节点添加事件监听，监听一次后自动销毁。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-onceNodeAdd(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onceNodeAdd(callback: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 是 |  |

## onceNodeClick

```TypeScript
onceNodeClick(callback: OnChangedCallback): void
```

注册节点点击事件监听，监听一次后自动销毁。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-onceNodeClick(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onceNodeClick(callback: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 是 |  |

## onceNodeDelete

```TypeScript
onceNodeDelete(callback: OnChangedCallback): void
```

注册节点删除事件监听，监听一次后自动销毁。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-onceNodeDelete(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onceNodeDelete(callback: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 是 |  |

## onceNodeModify

```TypeScript
onceNodeModify(callback: OnChangedCallback): void
```

注册节点修改事件监听，监听一次后自动销毁。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-onceNodeModify(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onceNodeModify(callback: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 是 |  |

## onceNodeMove

```TypeScript
onceNodeMove(callback: OnChangedCallback): void
```

注册节点移动事件监听，监听一次后自动销毁。使用callback回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TreeListenerV2-onceNodeMove(callback: OnChangedCallback): void--><!--Device-TreeListenerV2-onceNodeMove(callback: OnChangedCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnChangedCallback](../../apis-na/arkts-apis/arkts-na-onchangedcallback-t.md) | 是 |  |

