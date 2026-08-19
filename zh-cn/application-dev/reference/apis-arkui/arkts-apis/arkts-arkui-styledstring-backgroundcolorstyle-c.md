# BackgroundColorStyle

文本背景颜色对象说明。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class BackgroundColorStyle--><!--Device-unnamed-export declare class BackgroundColorStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(textBackgroundStyle: TextBackgroundStyle)
```

文本背景颜色的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundColorStyle-constructor(textBackgroundStyle: TextBackgroundStyle)--><!--Device-BackgroundColorStyle-constructor(textBackgroundStyle: TextBackgroundStyle)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textBackgroundStyle | [TextBackgroundStyle](../arkts-components/arkts-arkui-textbackgroundstyle-i.md) | 是 | 文本背景色设置项。&lt;br /&gt;默认值：&lt;br /&gt;{&lt;br /&gt; color: Color.Transparent,&lt; br /&gt; radius: 0&lt;br /&gt;} |

## textBackgroundStyle

```TypeScript
readonly textBackgroundStyle: TextBackgroundStyle
```

获取属性字符串的文本背景颜色。 默认值： { color: Color.Transparent, radius: 0 }

**类型：** [TextBackgroundStyle](../arkts-components/arkts-arkui-textbackgroundstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BackgroundColorStyle-readonly textBackgroundStyle: TextBackgroundStyle--><!--Device-BackgroundColorStyle-readonly textBackgroundStyle: TextBackgroundStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

