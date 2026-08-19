# Line

## Line

```TypeScript
@ComponentBuilder
export declare function Line(
    options?: LineOptions
): LineAttribute
```

用于绘制直线的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Line(    options?: LineOptions): LineAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Line(    options?: LineOptions): LineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [LineOptions](arkts-arkui-line-lineoptions-i.md) | 否 | Line绘制区域。<br/>异常值undefined和null按照无效值处理，本次设置不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LineAttribute](arkts-arkui-line-lineattribute-i.md) | 直线的属性。 |


## Line

```TypeScript
@Builder
export declare function Line(
    style: CustomBuilderT<LineAttribute>
): LineAttribute
```

定义Line组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Line(    style: CustomBuilderT<LineAttribute>): LineAttribute--><!--Device-unnamed-@Builderexport declare function Line(    style: CustomBuilderT<LineAttribute>): LineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[LineAttribute](arkts-arkui-line-lineattribute-i.md)&gt; | 是 | 设置组件属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LineAttribute](arkts-arkui-line-lineattribute-i.md) |  |

