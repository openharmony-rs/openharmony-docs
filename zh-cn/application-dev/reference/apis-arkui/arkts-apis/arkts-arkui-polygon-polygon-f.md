# Polygon

## Polygon

```TypeScript
@ComponentBuilder
export declare function Polygon(
    options?: PolygonOptions
): PolygonAttribute
```

用于绘制多边形的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Polygon(    options?: PolygonOptions): PolygonAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Polygon(    options?: PolygonOptions): PolygonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PolygonOptions](arkts-arkui-polygon-polygonoptions-i.md) | 否 | Polygon绘制区域。&lt;br/&gt;异常值undefined和null按照无效值处理，本次设置不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PolygonAttribute](arkts-arkui-polygon-polygonattribute-i.md) | 多边形的属性。 |


## Polygon

```TypeScript
@Builder
export declare function Polygon(
    style: CustomBuilderT<PolygonAttribute>,
): PolygonAttribute
```

定义Polygon组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Polygon(    style: CustomBuilderT<PolygonAttribute>,): PolygonAttribute--><!--Device-unnamed-@Builderexport declare function Polygon(    style: CustomBuilderT<PolygonAttribute>,): PolygonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[PolygonAttribute](arkts-arkui-polygon-polygonattribute-i.md)&gt; | 是 | 设置组件属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PolygonAttribute](arkts-arkui-polygon-polygonattribute-i.md) |  |

