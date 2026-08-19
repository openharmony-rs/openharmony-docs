# ArcButtonProgressConfig

ArcButton内进度条的参数配置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ArcButtonProgressConfig--><!--Device-unnamed-export declare class ArcButtonProgressConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(value: double, total?: double, color?: ResourceColor)
```

进度条参数配置的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcButtonProgressConfig-constructor(value: double, total?: double, color?: ResourceColor)--><!--Device-ArcButtonProgressConfig-constructor(value: double, total?: double, color?: ResourceColor)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double | 是 | 设置进度条的进度值。<br/>取值范围：[0, total]，当设置小于0的值时，按0处理；当设置大于total的值时，按total处理。 |
| total | double | 否 | 设置进度条的总进度值。<br/>默认值：100<br/>取值范围：[0, 2147483647] |
| color | ResourceColor | 否 | 设置进度条的前景颜色。 |

## color

```TypeScript
@Trace
  public color?: ResourceColor
```

进度条前景色。如果组件设置了[ArcButtonOptions](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcbutton-arcbuttonoptions-c.md)的背景色（backgroundColor），进度条前景色默认值取组件背景色。进度条前景色不受按钮样式（ [ArcButtonStyleMode](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-arcbutton-arcbuttonstylemode-e.md)）设置影响。进度条背景色仅依赖进度条前景色设置，取进度条前景色的25%透明度。 默认值："#1F71FF"，显示为蓝色。

**类型：** ResourceColor

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcButtonProgressConfig-@Trace  public color?: ResourceColor--><!--Device-ArcButtonProgressConfig-@Trace  public color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## total

```TypeScript
@Trace
  public total?: double
```

进度的最大值。 默认值：100 取值范围：[0, 2147483647]，设置0或超出取值范围取默认值为100。

**类型：** double

**默认值：** 100

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcButtonProgressConfig-@Trace  public total?: double--><!--Device-ArcButtonProgressConfig-@Trace  public total?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## value

```TypeScript
@Trace
  public value: double
```

进度条当前值。设置小于0的数值时置为0，设置大于total的数值时置为total。 默认值：0 取值范围：[0, total]

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcButtonProgressConfig-@Trace  public value: double--><!--Device-ArcButtonProgressConfig-@Trace  public value: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

