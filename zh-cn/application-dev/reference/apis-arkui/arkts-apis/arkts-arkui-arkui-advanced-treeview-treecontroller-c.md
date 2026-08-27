# TreeController

树视图组件的控制器，用于控制树的节点信息。同一控制器实例不能同时控制多个树视图组件。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## addNode

```TypeScript
addNode(nodeParam?: NodeParam): TreeController
```

选中某个节点后，调用该方法新增子节点。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nodeParam | [NodeParam](arkts-arkui-arkui-advanced-treeview-nodeparam-i.md) | 否 | 节点信息，用于指定新增节点的属性。如果不传该参数，在当前选中的节点下添加一个标题为“新建文件夹”节点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TreeController](arkts-arkui-arkui-advanced-treeview-treecontroller-c.md) | 返回树视图组件的控制器实例，支持链式调用。 |

## buildDone

```TypeScript
buildDone(): void
```

节点增加完毕后，必须调用该方法保存树信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modifyNode

```TypeScript
modifyNode(): void
```

选中某个节点后，调用该方法修改该节点。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## refreshNode

```TypeScript
refreshNode(parentId: number, parentSubTitle: ResourceStr, currentSubtitle: ResourceStr): void
```

调用该方法，通过指定父节点Id、父节点副标题和当前节点副标题，更新当前节点的显示信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parentId | number | 是 | 父节点Id。取值范围：大于等于-1。根节点id值为-1。若设置数值小于-1，做不生效处理。 |
| parentSubTitle | [ResourceStr](arkts-arkui-resourcestr-t.md) | 是 | 父节点副标题。设置后将更新父节点的副标题显示内容。 |
| currentSubtitle | [ResourceStr](arkts-arkui-resourcestr-t.md) | 是 | 当前节点副标题。设置后将更新当前节点的副标题显示内容。 |

## removeNode

```TypeScript
removeNode(): void
```

选中某个节点后，调用该方法删除该节点。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
