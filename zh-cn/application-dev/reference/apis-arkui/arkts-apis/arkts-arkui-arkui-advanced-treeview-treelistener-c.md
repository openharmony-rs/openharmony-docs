# TreeListener

树视图组件的监听器，可以将此对象绑定至树视图组件，然后通过它监听树的节点的变化，同一个监听器不可以控制多个树视图组件。监听器内部维护事件类型与回调函数的映射关系，当用户在TreeView上进行节点操作时，TreeView会通知监听器触 发相应的回调函数，开发者可在回调中获取节点信息并进行业务处理。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## off

```TypeScript
off(type: TreeListenType, callback?: (callbackParam: CallbackParam) => void): void
```

取消监听。需要先注册监听后才能取消。同一监听器不可控制多个树视图组件。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [TreeListenType](arkts-arkui-arkui-advanced-treeview-treelistentype-e.md) | 是 | 监听事件类型，用于指定要取消的监听事件。 |
| callback | (callbackParam: CallbackParam) =&gt; void | 否 | Node information. |

## on

```TypeScript
on(type: TreeListenType, callback: (callbackParam: CallbackParam) => void): void
```

注册树视图节点事件的监听，监听成功后，当节点发生对应事件时会触发回调函数。同一监听器不可控制多个树视图组件。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [TreeListenType](arkts-arkui-arkui-advanced-treeview-treelistentype-e.md) | 是 | 监听事件类型，用于指定要注册的监听事件。 |
| callback | (callbackParam: CallbackParam) =&gt; void | 是 | 回调函数，在对应监听事件触发时调用。回调参数callbackParam包含currentNodeId、parentNodeId和childIndex等信息。 |

## once

```TypeScript
once(type: TreeListenType, callback: (callbackParam: CallbackParam) => void): void
```

注册树视图节点事件的监听，监听成功后，当节点发生对应事件时会触发回调函数。同一监听器不可控制多个树视图组件。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [TreeListenType](arkts-arkui-arkui-advanced-treeview-treelistentype-e.md) | 是 | 监听事件类型，用于指定要注册的监听事件。 |
| callback | (callbackParam: CallbackParam) =&gt; void | 是 | 回调函数，在对应监听事件触发时调用。回调参数callbackParam包含currentNodeId、parentNodeId和childIndex等信息。 |
