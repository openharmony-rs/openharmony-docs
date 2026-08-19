# Shape

## Shape

```TypeScript
@ComponentBuilder
export declare function Shape(
    value?: PixelMap,
    content_?: CustomBuilder,
): ShapeAttribute
```

用于绘制Shape组件的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Shape(    value?: PixelMap,    content_?: CustomBuilder,): ShapeAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Shape(    value?: PixelMap,    content_?: CustomBuilder,): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PixelMap](../arkts-components/arkts-arkui-pixelmap-t.md) | 否 | 绘制目标，可将图形绘制在指定的PixelMap对象中，若未设置，则默认在当前绘制目标中进行绘制。异常值undefined和null按照无效值处理，本次设置不生效。 |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ShapeAttribute](arkts-arkui-shape-shapeattribute-i.md) | The attribute of the Shape. |


## Shape

```TypeScript
@Builder
export declare function Shape(
    style: CustomBuilderT<ShapeAttribute>,
    content_?: CustomBuilder,
): ShapeAttribute
```

Defines Shape Component.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Shape(    style: CustomBuilderT<ShapeAttribute>,    content_?: CustomBuilder,): ShapeAttribute--><!--Device-unnamed-@Builderexport declare function Shape(    style: CustomBuilderT<ShapeAttribute>,    content_?: CustomBuilder,): ShapeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[ShapeAttribute](arkts-arkui-shape-shapeattribute-i.md)&gt; | 是 | the callback to set up component's attributes. |
| content_ | CustomBuilder | 否 | container |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ShapeAttribute](arkts-arkui-shape-shapeattribute-i.md) |  |

