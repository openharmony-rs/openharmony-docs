# CallbackParamV2

节点回调参数接口，用于传递节点事件回调的参数信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export interface CallbackParamV2--><!--Device-unnamed-export interface CallbackParamV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## childIndex

```TypeScript
childIndex?: int
```

返回子索引。 取值范围：大于等于-1。 默认值：-1 仅在节点移动事件中有效，表示移动后的位置索引。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CallbackParamV2-childIndex?: int--><!--Device-CallbackParamV2-childIndex?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentNodeId

```TypeScript
currentNodeId: int
```

返回当前子节点id。 取值范围：大于等于0。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CallbackParamV2-currentNodeId: int--><!--Device-CallbackParamV2-currentNodeId: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## parentNodeId

```TypeScript
parentNodeId?: int
```

返回当前父节点id。 取值范围：大于等于-1。 默认值：-1

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CallbackParamV2-parentNodeId?: int--><!--Device-CallbackParamV2-parentNodeId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

