# BackgroundColorStyle

文本背景颜色对象说明。

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(textBackgroundStyle: TextBackgroundStyle)
```

文本背景颜色的构造函数。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| textBackgroundStyle | TextBackgroundStyle | 是 | 文本背景色设置项。<br />默认值：<br />{<br /> color: Color.Transparent,<br/> radius: 0<br />} |

## textBackgroundStyle

```TypeScript
readonly textBackgroundStyle: TextBackgroundStyle
```

获取属性字符串的文本背景颜色。

默认值：

{

color: Color.Transparent,

radius: 0

}

**类型：** TextBackgroundStyle

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

