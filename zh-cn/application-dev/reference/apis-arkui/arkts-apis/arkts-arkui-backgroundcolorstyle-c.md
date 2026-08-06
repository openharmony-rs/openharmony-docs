# BackgroundColorStyle

文本背景颜色对象说明。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

<!--Device-unnamed-declare class BackgroundColorStyle--><!--Device-unnamed-declare class BackgroundColorStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(textBackgroundStyle: TextBackgroundStyle)
```

文本背景颜色的构造函数。未通过该接口设置时，默认背景颜色为Color.Transparent，圆角为0。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundColorStyle-constructor(textBackgroundStyle: TextBackgroundStyle)--><!--Device-BackgroundColorStyle-constructor(textBackgroundStyle: TextBackgroundStyle)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textBackgroundStyle | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 文本背景色设置项。 |

## textBackgroundStyle

```TypeScript
readonly textBackgroundStyle: TextBackgroundStyle
```

获取属性字符串的文本背景颜色。 默认值： { color: Color.Transparent, radius: 0 }

**类型：** TextBackgroundStyle

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-BackgroundColorStyle-readonly textBackgroundStyle: TextBackgroundStyle--><!--Device-BackgroundColorStyle-readonly textBackgroundStyle: TextBackgroundStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

