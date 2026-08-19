# @ohos.arkui.advanced.TreeViewV2

## 导入模块

```TypeScript
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [TreeControllerV2](arkts-na-arkui-advanced-treeviewv2-treecontrollerv2-c.md) | 树视图组件的控制器，可以将此对象绑定至树视图组件，然后通过它控制树的节点信息，同一个控制器不可以控制多个树视图组件。 |
| [TreeListenerManagerV2](arkts-na-arkui-advanced-treeviewv2-treelistenermanagerv2-c.md) | 树视图组件的监听管理器，可以将此对象绑定至树视图组件，然后通过它管理树视图监听器的变化，同一个监听管理器不可以控制多个树视图组件。 |
| [TreeListenerV2](arkts-na-arkui-advanced-treeviewv2-treelistenerv2-c.md) | 树视图组件的监听器，可以将此对象绑定至树视图组件，然后通过它监听树视图的节点的变化，同一个树视图监听器不可以控制多个树视图组件。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [TreeViewV2](arkts-na-arkui-advanced-treeviewv2-treeviewv2-s.md) | 树视图V2组件。树视图作为一种分层显示的列表，适合显示嵌套结构。拥有父列表项和子列表项，可展开或折叠。 用于效率型应用，如备忘录、电子邮件、图库中的侧边导航栏。 该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于 [状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制树视图的数据和状态，实现更高效的用户界面刷新。 @internal/component/ets/common}和通用事件，编译工具链 > 会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到TreeViewV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议TreeViewV2设置通用 > 属性和通用事件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CallbackParamV2](arkts-na-arkui-advanced-treeviewv2-callbackparamv2-i.md) | 节点回调参数接口，用于传递节点事件回调的参数信息。 |
| [NodeParamV2](arkts-na-arkui-advanced-treeviewv2-nodeparamv2-i.md) | 节点参数接口，用于配置树节点的属性。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnChangedCallback](arkts-na-onchangedcallback-t.md) | 节点事件回调函数类型。 |
| [OnContainerCallback](arkts-na-oncontainercallback-t.md) | 容器回调函数类型，用于定义绑定在树节点上的子组件回调。 |

