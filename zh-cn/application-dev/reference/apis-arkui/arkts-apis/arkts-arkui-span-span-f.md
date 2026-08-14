# Span

## Span

```TypeScript
@ComponentBuilder
export declare function Span(
    value: string | Resource
): SpanAttribute
```

定义Span组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Span(    value: string | Resource): SpanAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Span(    value: string | Resource): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SpanAttribute |  |


## Span

```TypeScript
@Builder
export declare function Span(
    style: CustomBuilderT<SpanAttribute>,
): SpanAttribute
```

定义Span组件。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.1.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Span(    style: CustomBuilderT<SpanAttribute>,): SpanAttribute--><!--Device-unnamed-@Builderexport declare function Span(    style: CustomBuilderT<SpanAttribute>,): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;SpanAttribute&gt; | 是 | Span属性实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SpanAttribute |  |

