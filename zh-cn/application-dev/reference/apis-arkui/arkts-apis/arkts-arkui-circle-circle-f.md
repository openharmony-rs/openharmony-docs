# Circle

## Circle

```TypeScript
@ComponentBuilder
export declare function Circle(
    options?: CircleOptions
): CircleAttribute
```

用于绘制圆形的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Circle(    options?: CircleOptions): CircleAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Circle(    options?: CircleOptions): CircleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CircleOptions](arkts-arkui-circle-circleoptions-i.md) | 否 | 设置圆形尺寸。<br/>异常值undefined和null按照无效值处理，本次设置不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CircleAttribute](arkts-arkui-circle-circleattribute-i.md) | Circle的属性。 |


## Circle

```TypeScript
@Builder
export declare function Circle(
    style: CustomBuilderT<CircleAttribute>
): CircleAttribute
```

定义Circle组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Circle(    style: CustomBuilderT<CircleAttribute>): CircleAttribute--><!--Device-unnamed-@Builderexport declare function Circle(    style: CustomBuilderT<CircleAttribute>): CircleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[CircleAttribute](arkts-arkui-circle-circleattribute-i.md)&gt; | 是 | Circle选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CircleAttribute](arkts-arkui-circle-circleattribute-i.md) |  |

