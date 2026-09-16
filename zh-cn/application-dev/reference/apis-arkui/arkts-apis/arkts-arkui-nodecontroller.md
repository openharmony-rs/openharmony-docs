# NodeController

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [NodeController](arkts-arkui-nodecontroller-c.md) | NodeController用于管理自定义节点的创建、显示、更新等操作，并负责将自定义节点挂载到NodeContainer上，适用于需要在页面中动态创建、更新、复用自定义节点的场景。 |

## 示例

```TypeScript
### 示例1（添加节点布局、Touch、挂载和卸载时的生命周期回调）

该示例通过aboutToResize、onTouchEvent，实现了NodeContainer节点布局、收到Touch事件时的生命周期回调功能。

并通过aboutToAppear、aboutToDisappear接口，实现了NodeContainer节点挂载至主节点树、从主节点树卸载时的生命周期回调功能。

该示例还通过NodeController挂载BuilderNode节点。


```

```TypeScript
### 示例2（添加节点上下树和绑定解绑前后的生命周期回调）

该示例通过onAttach、onDetach接口，实现了NodeContainer节点上下主节点树的生命周期回调功能。

并通过onWillBind、onWillUnbind、onBind、onUnbind接口，实现了NodeContainer节点绑定和解绑前后的生命周期回调功能。
```
