# Rect

## Rect

```TypeScript
export declare function Rect(
    options?: RectOptions | RoundedRectOptions
): RectAttribute
```

用于绘制矩形的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Rect(    options?: RectOptions | RoundedRectOptions): RectAttribute--><!--Device-unnamed-export declare function Rect(    options?: RectOptions | RoundedRectOptions): RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| RoundedRectOptions | 否 | Rect绘制属性。异常值undefined和null按照无效值处理，本次设置不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | The attribute of the Rect |


## Rect

```TypeScript
export declare function Rect(
    style: CustomBuilderT<RectAttribute>,
): RectAttribute
```

Defines Rect Component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Rect(    style: CustomBuilderT<RectAttribute>,): RectAttribute--><!--Device-unnamed-export declare function Rect(    style: CustomBuilderT<RectAttribute>,): RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | the callback to set up component's attributes. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

