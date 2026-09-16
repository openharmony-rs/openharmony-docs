# RichEditorBuilderSpan

定义**RichEditor**的BuilderSpan对象，提供身份识别与生命周期感知能力。

> **说明：** 
> 
> 当**RichEditor**组件使用[RichEditorStyledStringOptions](arkts-arkui-richeditorstyledstringoptions-i.md)构造时，不支持此接口。

**起始版本：** 26.2.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilitySpanOptions

```TypeScript
accessibilitySpanOptions?: AccessibilitySpanOptions
```

无障碍朗读功能属性。缺省时，取[AccessibilitySpanOptions](../arkts-apis/arkts-arkui-accessibilityspanoptions-i.md)的默认值。

**类型：** [AccessibilitySpanOptions](../arkts-apis/arkts-arkui-accessibilityspanoptions-i.md)

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder: CustomBuilder
```

自定义组件构造器。

**类型：** [CustomBuilder](arkts-arkui-custombuilder-t.md)

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAttach

```TypeScript
onAttach?: Callback<BuilderSpanInfo>
```

BuilderSpan挂载到**RichEditor**时触发的回调。回调接收一个[BuilderSpanInfo](arkts-arkui-builderspaninfo-i.md)对象，包含id和offset。

**类型：** [Callback](arkts-arkui-callback-i.md)&lt;[BuilderSpanInfo](arkts-arkui-builderspaninfo-i.md)&gt;

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDetach

```TypeScript
onDetach?: Callback<BuilderSpanInfo>
```

BuilderSpan从**RichEditor**中被移除时触发的回调。包括通过deleteSpans API删除、IME键盘删除、剪切操作以及普通Undo降级等删除场景。回调接收一个[BuilderSpanInfo](arkts-arkui-builderspaninfo-i.md)对象，包含id和offset。

> **说明：** 
> 
> 在拖拽撤销（undoStyle=KEEP_STYLE）场景中，onDetach回调不会被触发，
> 因为BuilderSpan正在被恢复而非被删除。

**类型：** [Callback](arkts-arkui-callback-i.md)&lt;[BuilderSpanInfo](arkts-arkui-builderspaninfo-i.md)&gt;

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
