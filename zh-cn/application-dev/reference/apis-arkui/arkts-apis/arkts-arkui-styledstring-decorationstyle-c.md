# DecorationStyle

文本装饰线样式对象说明。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class DecorationStyle--><!--Device-unnamed-export declare class DecorationStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: DecorationStyleInterface)
```

文本装饰线样式的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecorationStyle-constructor(value: DecorationStyleInterface)--><!--Device-DecorationStyle-constructor(value: DecorationStyleInterface)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DecorationStyleInterface](arkts-arkui-styledstring-decorationstyleinterface-i.md) | 是 | 文本装饰线设置项。<br/>默认值：<br/>{<br/> type: TextDecorationType.None,<br/> color: Color.Black,<br/> style: TextDecorationStyle.SOLID <br/>} |

## constructor

```TypeScript
constructor(value: DecorationStyleInterface, options?: DecorationOptions)
```

文本装饰线样式的构造函数，包含额外配置选项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecorationStyle-constructor(value: DecorationStyleInterface, options?: DecorationOptions)--><!--Device-DecorationStyle-constructor(value: DecorationStyleInterface, options?: DecorationOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DecorationStyleInterface](arkts-arkui-styledstring-decorationstyleinterface-i.md) | 是 | 文本装饰线设置项。<br/>默认值：<br/>{<br/> type: TextDecorationType.None,<br/> color: Color.Black,<br/> style: TextDecorationStyle.SOLID, <br/> thicknessScale: 1.0<br/>} |
| options | [DecorationOptions](arkts-arkui-styledstring-decorationoptions-i.md) | 否 | 文本装饰线额外配置选项。<br/>默认值：<br/>{<br/> enableMultiType: undefined<br/>} |

## color

```TypeScript
readonly color?: ResourceColor
```

获取属性字符串的文本装饰线颜色。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecorationStyle-readonly color?: ResourceColor--><!--Device-DecorationStyle-readonly color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
readonly options?: DecorationOptions
```

获取属性字符串的文本装饰线样式的额外配置选项。

**类型：** [DecorationOptions](arkts-arkui-styledstring-decorationoptions-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecorationStyle-readonly options?: DecorationOptions--><!--Device-DecorationStyle-readonly options?: DecorationOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
readonly style?: TextDecorationStyle
```

获取属性字符串的文本装饰线样式。

**类型：** [TextDecorationStyle](arkts-arkui-textdecorationstyle-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecorationStyle-readonly style?: TextDecorationStyle--><!--Device-DecorationStyle-readonly style?: TextDecorationStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## thicknessScale

```TypeScript
readonly thicknessScale?: double
```

获取属性字符串的文本装饰线粗细缩放值。

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecorationStyle-readonly thicknessScale?: double--><!--Device-DecorationStyle-readonly thicknessScale?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
readonly type: TextDecorationType
```

获取属性字符串的文本装饰线类型。

**类型：** [TextDecorationType](arkts-arkui-textdecorationtype-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecorationStyle-readonly type: TextDecorationType--><!--Device-DecorationStyle-readonly type: TextDecorationType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

