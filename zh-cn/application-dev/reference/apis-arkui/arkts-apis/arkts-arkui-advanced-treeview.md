# @ohos.arkui.advanced.TreeView

## 导入模块

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [TreeController](arkts-arkui-arkui-advanced-treeview-treecontroller-c.md) | 树视图组件的控制器，用于控制树的节点信息。同一控制器实例不能同时控制多个树视图组件。 |
| [TreeListener](arkts-arkui-arkui-advanced-treeview-treelistener-c.md) | 树视图组件的监听器，可以将此对象绑定至树视图组件，然后通过它监听树的节点的变化，同一个监听器不可以控制多个树视图组件。监听器内部维护事件类型与回调函数的映射关系，当用户在TreeView上进行节点操作时，TreeView会通知监听器触 发相应的回调函数，开发者可在回调中获取节点信息并进行业务处理。 |
| [TreeListenerManager](arkts-arkui-arkui-advanced-treeview-treelistenermanager-c.md) | 树视图组件的监听管理器，可以获取监听器实例并绑定至树视图组件，用于管理树的节点监听，同一个监听器不可以控制多个树视图组件。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [TreeView](arkts-arkui-arkui-advanced-treeview-treeview-s.md) | 树视图作为一种分层显示的列表，适合显示嵌套结构。树视图包含父节点和子节点，支持展开或折叠。树视图适用于效率型应用的侧边导航栏中，如备忘录、电子邮件、图库等。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CallbackParam](arkts-arkui-arkui-advanced-treeview-callbackparam-i.md) | Declare CallbackParam |
| [NodeParam](arkts-arkui-arkui-advanced-treeview-nodeparam-i.md) | Declare NodeParam |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TreeListenType](arkts-arkui-arkui-advanced-treeview-treelistentype-e.md) | 定义树视图节点的监听事件类型。 |
