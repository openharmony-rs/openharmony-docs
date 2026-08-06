# NumericTextTransition

数字翻牌动效。仅限正整数，不支持小数和负数。不支持渐变色和Text跑马灯模式。不支持选中， \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_属性无效。当文本存在子组件时或通过属性字符串设置 时，数字翻牌失效。 NumericTextTransition继承自[ContentTransition]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**继承/实现关系：** NumericTextTransition extends [ContentTransition](textcommon-contenttransition-c.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export declare class NumericTextTransition extends ContentTransition--><!--Device-unnamed-export declare class NumericTextTransition extends ContentTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: NumericTextTransitionOptions)
```

用于创建NumericTextTransition对象的构造函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NumericTextTransition-constructor(options?: NumericTextTransitionOptions)--><!--Device-NumericTextTransition-constructor(options?: NumericTextTransitionOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 设置数字翻牌动效。 默认值继承[NumericTextTransitionOptions]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

## enableBlur

```TypeScript
enableBlur?: boolean
```

是否开启翻牌模糊效果。 默认值：false true：开启翻牌模糊效果。 false：不开启翻牌模糊效果。

**类型：** boolean

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NumericTextTransition-enableBlur?: boolean--><!--Device-NumericTextTransition-enableBlur?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## flipDirection

```TypeScript
flipDirection?: FlipDirection
```

翻牌方向。 默认值：FlipDirection.DOWN

**类型：** FlipDirection

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NumericTextTransition-flipDirection?: FlipDirection--><!--Device-NumericTextTransition-flipDirection?: FlipDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

