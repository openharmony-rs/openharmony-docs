# @ohos.arkui.advanced.TreeViewV2

## 导入模块

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [TreeControllerV2](arkts-arkui-arkui-advanced-treeviewv2-treecontrollerv2-c.md) | 树视图组件的控制器，可以将此对象绑定至树视图组件，然后通过它控制树的节点信息，同一个控制器不可以控制多个树视图组件。 |
| [TreeListenerManagerV2](arkts-arkui-arkui-advanced-treeviewv2-treelistenermanagerv2-c.md) | 树视图组件的监听管理器，可以将此对象绑定至树视图组件，然后通过它管理树视图监听器的变化，同一个监听管理器不可以控制多个树视图组件。 |
| [TreeListenerV2](arkts-arkui-arkui-advanced-treeviewv2-treelistenerv2-c.md) | 树视图组件的监听器，可以将此对象绑定至树视图组件，然后通过它监听树视图的节点的变化，同一个树视图监听器不可以控制多个树视图组件。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [TreeViewV2](arkts-arkui-arkui-advanced-treeviewv2-treeviewv2-s.md) | 树视图V2组件。树视图作为一种分层显示的列表，适合显示嵌套结构。拥有父列表项和子列表项，可展开或折叠。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CallbackParamV2](arkts-arkui-arkui-advanced-treeviewv2-callbackparamv2-i.md) | 节点回调参数接口，用于传递节点事件回调的参数信息。 |
| [NodeParamV2](arkts-arkui-arkui-advanced-treeviewv2-nodeparamv2-i.md) | 节点参数接口，用于配置树节点的属性。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnChangedCallback](arkts-arkui-onchangedcallback-t.md) | 节点事件回调函数类型。 |
| [OnContainerCallback](arkts-arkui-oncontainercallback-t.md) | 容器回调函数类型，用于定义绑定在树节点上的子组件回调。 |

## 示例

```TypeScript
### 示例1（设置树视图）

从API版本26.0.0开始，支持以下示例通过树视图组件的控制器接口对树视图的节点进行新增、删除、重命名等功能。


```

```TypeScript
### 示例2（设置Symbol类型图标）

从API版本26.0.0开始，支持以下示例通过设置[NodeParamV2](arkts-arkui-arkui-advanced-treeviewv2-nodeparamv2-i.md)的symbolIconStyle、symbolEditIconStyle、symbolSelectedIconStyle等属性接口，实现树视图中自定义Symbol类型图标的功能。
```
