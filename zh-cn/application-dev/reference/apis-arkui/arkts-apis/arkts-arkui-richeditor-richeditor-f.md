# RichEditor

## RichEditor

```TypeScript
@ComponentBuilder
export declare function RichEditor(
    options: RichEditorOptions | RichEditorStyledStringOptions, 
): RichEditorAttribute
```

创建富文本组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function RichEditor(    options: RichEditorOptions | RichEditorStyledStringOptions, ): RichEditorAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function RichEditor(    options: RichEditorOptions | RichEditorStyledStringOptions, ): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RichEditorOptions](arkts-arkui-richeditor-richeditoroptions-i.md) \| [RichEditorStyledStringOptions](arkts-arkui-richeditor-richeditorstyledstringoptions-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RichEditorAttribute |  |


## RichEditor

```TypeScript
@Builder
export declare function RichEditor(
    style: CustomBuilderT<RichEditorAttribute>,
): RichEditorAttribute
```

创建富文本组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function RichEditor(    style: CustomBuilderT<RichEditorAttribute>,): RichEditorAttribute--><!--Device-unnamed-@Builderexport declare function RichEditor(    style: CustomBuilderT<RichEditorAttribute>,): RichEditorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;RichEditorAttribute&gt; | 是 | RichEditor attribute instance |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RichEditorAttribute |  |

