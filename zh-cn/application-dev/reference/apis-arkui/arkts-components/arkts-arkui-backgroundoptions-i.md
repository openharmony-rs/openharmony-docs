# BackgroundOptions

background配置选项。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## align

```TypeScript
align?: Alignment
```

自定义背景与组件的对齐方式。该属性仅对CustomBuilder类型的背景生效，对ResourceColor类型的背景设置align属性无效。如果设置了ignoresLayoutSafeAreaEdges，则背景的布局区域为包含了扩展安全区的范围。

默认值：Alignment.Center

**类型：** [Alignment](../arkts-apis/arkts-arkui-alignment-e.md)

**默认值：** 
- API版本20+：Alignment.Center

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ignoresLayoutSafeAreaEdges

```TypeScript
ignoresLayoutSafeAreaEdges?: Array<LayoutSafeAreaEdge>
```

配置背景要扩展到的安全区，包括：状态栏，导航栏和[safeAreaPadding](arkts-arkui-commonmethod-c.md#safeareapadding)。设置该属性后，背景的对齐布局区域将包含扩展安全区的范围。

默认值：

- CustomBuilder背景：[]，不扩展。  
- ResourceColor背景：[LayoutSafeAreaEdge.ALL]，扩展至所有方向。

**类型：** Array&lt;[LayoutSafeAreaEdge](arkts-arkui-layoutsafeareaedge-e.md)&gt;

**默认值：** The default value is LayoutSafeAreaEdge.ALL when background is ResourceColor, otherwise it is an empty array [].

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
