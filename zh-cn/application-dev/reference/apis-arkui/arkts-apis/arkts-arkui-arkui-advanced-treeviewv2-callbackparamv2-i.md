# CallbackParamV2

节点回调参数接口，用于传递节点事件回调的参数信息。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface CallbackParamV2--><!--Device-unnamed-export interface CallbackParamV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## childIndex

```TypeScript
childIndex?: number
```

返回子索引。 取值范围：大于等于-1。 默认值：-1 仅在节点移动事件中有效，表示移动后的位置索引。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CallbackParamV2-childIndex?: number--><!--Device-CallbackParamV2-childIndex?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentNodeId

```TypeScript
currentNodeId: number
```

返回当前子节点id。 取值范围：大于等于0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CallbackParamV2-currentNodeId: number--><!--Device-CallbackParamV2-currentNodeId: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## parentNodeId

```TypeScript
parentNodeId?: number
```

返回当前父节点id。 取值范围：大于等于-1。 默认值：-1

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CallbackParamV2-parentNodeId?: number--><!--Device-CallbackParamV2-parentNodeId?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

