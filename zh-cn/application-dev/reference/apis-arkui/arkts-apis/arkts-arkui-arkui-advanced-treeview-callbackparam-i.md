# CallbackParam

Declare CallbackParam

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## childIndex

```TypeScript
childIndex?: number
```

返回子节点在父节点下的索引位置，用于标识子节点在父节点的子节点列表中的位置。取值范围：大于等于-1，-1表示无效索引或无子节点。默认值：-1

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentNodeId

```TypeScript
currentNodeId: number
```

返回当前子节点id。取值范围：大于等于0。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## parentNodeId

```TypeScript
parentNodeId?: number
```

返回当前父节点id。取值范围：大于等于-1。默认值：-1

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
