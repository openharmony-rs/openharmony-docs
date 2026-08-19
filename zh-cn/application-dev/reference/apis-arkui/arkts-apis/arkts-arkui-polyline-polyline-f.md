# Polyline

## Polyline

```TypeScript
@ComponentBuilder
export declare function Polyline(
    options?: PolylineOptions
): PolylineAttribute
```

用于绘制折线的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Polyline(    options?: PolylineOptions): PolylineAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Polyline(    options?: PolylineOptions): PolylineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PolylineOptions](arkts-arkui-polyline-polylineoptions-i.md) | 否 | Polyline绘制区域。<br/>异常值undefined和null按照无效值处理，本次设置不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PolylineAttribute](arkts-arkui-polyline-polylineattribute-i.md) | 折线的属性。 |


## Polyline

```TypeScript
@Builder
export declare function Polyline(
    style: CustomBuilderT<PolylineAttribute>,
): PolylineAttribute
```

定义Polyline组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Polyline(    style: CustomBuilderT<PolylineAttribute>,): PolylineAttribute--><!--Device-unnamed-@Builderexport declare function Polyline(    style: CustomBuilderT<PolylineAttribute>,): PolylineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[PolylineAttribute](arkts-arkui-polyline-polylineattribute-i.md)&gt; | 是 | 设置组件属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PolylineAttribute](arkts-arkui-polyline-polylineattribute-i.md) |  |

