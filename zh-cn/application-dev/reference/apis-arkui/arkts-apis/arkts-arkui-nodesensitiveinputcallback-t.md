# NodeSensitiveInputCallback

```TypeScript
export declare type NodeSensitiveInputCallback = (info: NodeSensitiveInputInfo, node?: FrameNode) => void
```

定义监听指定节点输入事件的回调类型。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export declare type NodeSensitiveInputCallback = (info: NodeSensitiveInputInfo, node?: FrameNode) => void--><!--Device-unnamed-export declare type NodeSensitiveInputCallback = (info: NodeSensitiveInputInfo, node?: FrameNode) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [NodeSensitiveInputInfo](arkts-arkui-arkui-uicontext-nodesensitiveinputinfo-i.md) | 是 | 分发到节点的输入事件信息。 |
| node | [FrameNode](arkts-arkui-framenode-c.md) | 否 | 接收输入事件的组件；若组件已释放，则返回**null**。 |
