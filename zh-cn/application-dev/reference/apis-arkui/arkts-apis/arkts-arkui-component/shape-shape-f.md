# Shape

## Shape

```TypeScript
export declare function Shape(
    value?: PixelMap,
    content_?: CustomBuilder,
): ShapeAttribute
```

用于绘制Shape组件的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Shape(    value?: PixelMap,    content_?: CustomBuilder,): ShapeAttribute--><!--Device-unnamed-export declare function Shape(    value?: PixelMap,    content_?: CustomBuilder,): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 绘制目标，可将图形绘制在指定的PixelMap对象中，若未设置，则默认在当前绘制目标中进行绘制。异常值undefined和null按照无效值处理，本次设置不生效。 |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | The attribute of the Shape. |


## Shape

```TypeScript
export declare function Shape(
    style: CustomBuilderT<ShapeAttribute>,
    content_?: CustomBuilder,
): ShapeAttribute
```

Defines Shape Component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Shape(    style: CustomBuilderT<ShapeAttribute>,    content_?: CustomBuilder,): ShapeAttribute--><!--Device-unnamed-export declare function Shape(    style: CustomBuilderT<ShapeAttribute>,    content_?: CustomBuilder,): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | the callback to set up component's attributes. |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

