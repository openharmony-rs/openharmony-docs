# ArcScrollBar

## ArcScrollBar

```TypeScript
@ComponentBuilder
export declare function ArcScrollBar(
    options: ArcScrollBarOptions, 
    content_?: CustomBuilder,
): ArcScrollBarAttribute
```

定义ArcScrollBar组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-@ComponentBuilderexport declare function ArcScrollBar(    options: ArcScrollBarOptions,     content_?: CustomBuilder,): ArcScrollBarAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function ArcScrollBar(    options: ArcScrollBarOptions,     content_?: CustomBuilder,): ArcScrollBarAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ArcScrollBarOptions](arkts-na-arkui-arcscrollbar-arcscrollbaroptions-i.md) | 是 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcScrollBarAttribute |  |


## ArcScrollBar

```TypeScript
@Builder
export declare function ArcScrollBar(
    style_: CustomBuilderT<ArcScrollBarAttribute>,
    content_?: CustomBuilder
): ArcScrollBarAttribute
```

定义ArcScrollBar组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function ArcScrollBar(    style_: CustomBuilderT<ArcScrollBarAttribute>,    content_?: CustomBuilder): ArcScrollBarAttribute--><!--Device-unnamed-@Builderexport declare function ArcScrollBar(    style_: CustomBuilderT<ArcScrollBarAttribute>,    content_?: CustomBuilder): ArcScrollBarAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;ArcScrollBarAttribute&gt; | 是 | 用于创建ArcScrollBar的样式 |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcScrollBarAttribute | ArcScrollBar的属性。 |

