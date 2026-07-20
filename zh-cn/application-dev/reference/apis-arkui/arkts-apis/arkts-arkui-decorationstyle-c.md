# DecorationStyle

文本装饰线样式对象说明。

**起始版本：** 12

<!--Device-unnamed-declare class DecorationStyle--><!--Device-unnamed-declare class DecorationStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(value: DecorationStyleInterface)
```

文本装饰线样式的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecorationStyle-constructor(value: DecorationStyleInterface)--><!--Device-DecorationStyle-constructor(value: DecorationStyleInterface)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DecorationStyleInterface](arkts-arkui-decorationstyleinterface-i.md) | 是 | 文本装饰线设置项。<br/>默认值：<br/>{<br/> type: TextDecorationType.None,<br/> color: Color.Black,<br/> style: TextDecorationStyle.SOLID <br/>} |

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(value: DecorationStyleInterface, options?: DecorationOptions)
```

文本装饰线样式的构造函数，包含额外配置选项。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DecorationStyle-constructor(value: DecorationStyleInterface, options?: DecorationOptions)--><!--Device-DecorationStyle-constructor(value: DecorationStyleInterface, options?: DecorationOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DecorationStyleInterface](arkts-arkui-decorationstyleinterface-i.md) | 是 | 文本装饰线设置项。<br/>默认值：<br/>{<br/> type: TextDecorationType.None,<br/> color: Color.Black,<br/> style: TextDecorationStyle.SOLID, <br/> thicknessScale: 1.0<br/>} |
| options | [DecorationOptions](arkts-arkui-decorationoptions-i.md) | 否 | 文本装饰线额外配置选项。<br/>默认值：<br/>{<br/> enableMultiType: undefined<br/>} |

## color

```TypeScript
readonly color?: ResourceColor
```

获取属性字符串的文本装饰线颜色。

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecorationStyle-readonly color?: ResourceColor--><!--Device-DecorationStyle-readonly color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
readonly options?: DecorationOptions
```

获取属性字符串的文本装饰线样式的额外配置选项。

**类型：** DecorationOptions

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DecorationStyle-readonly options?: DecorationOptions--><!--Device-DecorationStyle-readonly options?: DecorationOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
readonly style?: TextDecorationStyle
```

获取属性字符串的文本装饰线样式。

**类型：** TextDecorationStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecorationStyle-readonly style?: TextDecorationStyle--><!--Device-DecorationStyle-readonly style?: TextDecorationStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## thicknessScale

```TypeScript
readonly thicknessScale?: number
```

获取属性字符串的文本装饰线粗细缩放值。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DecorationStyle-readonly thicknessScale?: number--><!--Device-DecorationStyle-readonly thicknessScale?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
readonly type: TextDecorationType
```

获取属性字符串的文本装饰线类型。

**类型：** TextDecorationType

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DecorationStyle-readonly type: TextDecorationType--><!--Device-DecorationStyle-readonly type: TextDecorationType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

