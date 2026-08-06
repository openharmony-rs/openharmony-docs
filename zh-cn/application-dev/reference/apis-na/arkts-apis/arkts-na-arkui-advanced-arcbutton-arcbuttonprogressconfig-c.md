# ArcButtonProgressConfig

ArcButton内进度条的参数配置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class ArcButtonProgressConfig--><!--Device-unnamed-export declare class ArcButtonProgressConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## constructor

```TypeScript
constructor(value: double, total?: double, color?: ResourceColor)
```

进度条参数配置的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcButtonProgressConfig-constructor(value: double, total?: double, color?: ResourceColor)--><!--Device-ArcButtonProgressConfig-constructor(value: double, total?: double, color?: ResourceColor)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double | 是 | 设置进度条的进度值。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值范围：[0, total]，当设置小于0的值时，按0处理；当设置大于total的值时，按total处理。 |
| total | double | 否 | 设置进度条的总进度值。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：100\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值范围：[0, 2147483647] |
| color | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 设置进度条的前景颜色。 |

## color

```TypeScript
public color?: ResourceColor
```

进度条前景色。如果组件设置了[ArcButtonOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的背景色（backgroundColor），进度条前景色默认值取组件背景色。进度条前景色不受按钮样式（ [ArcButtonStyleMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_）设置影响。进度条背景色仅依赖进度条前景色设置，取进度条前景色的25%透明度。 默认值："#1F71FF"，显示为蓝色。

**类型：** ResourceColor

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcButtonProgressConfig-public color?: ResourceColor--><!--Device-ArcButtonProgressConfig-public color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## total

```TypeScript
public total?: double
```

进度的最大值。 默认值：100 取值范围：[0, 2147483647]，设置0或超出取值范围取默认值为100。

**类型：** double

**默认值：** 100

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcButtonProgressConfig-public total?: double--><!--Device-ArcButtonProgressConfig-public total?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## value

```TypeScript
public value: double
```

进度条当前值。设置小于0的数值时置为0，设置大于total的数值时置为total。 默认值：0 取值范围：[0, total]

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcButtonProgressConfig-public value: double--><!--Device-ArcButtonProgressConfig-public value: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

