# Rect

## Rect

```TypeScript
@ComponentBuilder
export declare function Rect(
    options?: RectOptions | RoundedRectOptions
): RectAttribute
```

用于绘制矩形的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Rect(    options?: RectOptions | RoundedRectOptions): RectAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Rect(    options?: RectOptions | RoundedRectOptions): RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rect-rectoptions-i.md) \| [RoundedRectOptions](arkts-arkui-rect-roundedrectoptions-i.md) | 否 | Rect绘制属性。异常值undefined和null按照无效值处理，本次设置不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectAttribute](arkts-arkui-rect-rectattribute-i.md) | The attribute of the Rect |


## Rect

```TypeScript
@Builder
export declare function Rect(
    style: CustomBuilderT<RectAttribute>,
): RectAttribute
```

Defines Rect Component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Rect(    style: CustomBuilderT<RectAttribute>,): RectAttribute--><!--Device-unnamed-@Builderexport declare function Rect(    style: CustomBuilderT<RectAttribute>,): RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[RectAttribute](arkts-arkui-rect-rectattribute-i.md)&gt; | 是 | the callback to set up component's attributes. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectAttribute](arkts-arkui-rect-rectattribute-i.md) |  |

