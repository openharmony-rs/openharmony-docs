# NodeContainer

基础组件，用于挂载自定义节点（如[FrameNode]{@link FrameNode}或[BuilderNode]{@link BuilderNode}），并通过
[NodeController]{@link NodeController:NodeController}动态控制节点的上树和下树。组件不支持尾随添加子节点，接受一个
[NodeController]{@link NodeController:NodeController}实例接口，需与NodeController组合使用。
> **说明：**
> - 该组件下仅支持挂载自定义节点[FrameNode]{@link FrameNode}或者是[BuilderNode]{@link BuilderNode}中获取的根节点FrameNode。
>
> - 不支持挂载查询获得的系统组件代理节点，请参见[isModifiable]{@link FrameNode:FrameNode#isModifiable}。
>
> - 当前不支持使用[动态属性设置]{@link common}。
>
> - 该组件下的节点树构建时会使用UI实例[UIContext]{@link @ohos.arkui.UIContext}，实例切换时可能会因实例不匹配，导致所绑定
> [NodeController]{@link NodeController:NodeController}的[makeNode]{@link NodeController:NodeController#makeNode}回调方法的
> 入参为undefined，因此该组件当前不支持跨实例的节点复用。
>
> - 该组件未销毁时，不会主动触发挂载节点的下树。


## NodeContainer

```TypeScript
NodeContainer(controller: import('../api/@ohos.arkui.node').NodeController)
```

创建一个**NodeContainer**组件。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NodeContainerInterface-(controller: import('../api/@ohos.arkui.node').NodeController): NodeContainerAttribute--><!--Device-NodeContainerInterface-(controller: import('../api/@ohos.arkui.node').NodeController): NodeContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | import('../api/@ohos.arkui.node').NodeController | 是 | NodeController用于控制NodeContainer中的节点的上树和下树，反映NodeContainer容器的生命周期。 |

## 汇总

