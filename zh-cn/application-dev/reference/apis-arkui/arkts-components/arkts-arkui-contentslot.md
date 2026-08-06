# ContentSlot

用于渲染Native侧使用C-API创建的组件，并通过Content管理器管理这些组件。 支持混合模式开发，当容器是ArkTS组件，子组件在Native侧创建时，推荐使用ContentSlot占位组件。

## ContentSlot

```TypeScript
ContentSlot(content: Content)
```

创建ContentSlot占位组件，用于渲染Content管理器中Native侧创建的组件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ContentSlotInterface-(content: Content): ContentSlotAttribute--><!--Device-ContentSlotInterface-(content: Content): ContentSlotAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Content作为ContentSlot的管理器，通过Native侧提供的接口，可以注册并触发ContentSlot的上下树（即组件节点加入或移出组件渲染树）事件回调以及管 理ContentSlot的子组件。  |

## 汇总

