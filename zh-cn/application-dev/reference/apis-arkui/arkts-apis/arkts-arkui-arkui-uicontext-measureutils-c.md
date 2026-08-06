# MeasureUtils

class MeasureUtils

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class MeasureUtils--><!--Device-unnamed-export declare class MeasureUtils-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getParagraphs

```TypeScript
getParagraphs(styledString: StyledString, options?: TextLayoutOptions): Array<Paragraph>
```

获取属性字符串的布局信息。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureUtils-getParagraphs(styledString: StyledString, options?: TextLayoutOptions): Array<Paragraph>--><!--Device-MeasureUtils-getParagraphs(styledString: StyledString, options?: TextLayoutOptions): Array<Paragraph>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styledString | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 属性字符串值。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 布局选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | paragraph result |

## measureText

```TypeScript
measureText(options: MeasureOptions): double
```

获取单行文本的宽度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureUtils-measureText(options: MeasureOptions): double--><!--Device-MeasureUtils-measureText(options: MeasureOptions): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double |  |

## measureTextSize

```TypeScript
measureTextSize(options: MeasureOptions): SizeOptions
```

获取单行文本的宽度和高度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureUtils-measureTextSize(options: MeasureOptions): SizeOptions--><!--Device-MeasureUtils-measureTextSize(options: MeasureOptions): SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Options of measure area occupied by text. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | width and height for text to display |

