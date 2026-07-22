# TextShadowStyle

文本阴影对象说明。

**起始版本：** 12

<!--Device-unnamed-declare class TextShadowStyle--><!--Device-unnamed-declare class TextShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: ShadowOptions | Array<ShadowOptions>)
```

文本阴影对象的构造函数。

ShadowOptions对象中不支持fill字段。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextShadowStyle-constructor(value: ShadowOptions | Array<ShadowOptions>)--><!--Device-TextShadowStyle-constructor(value: ShadowOptions | Array<ShadowOptions>)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ShadowOptions](../arkts-components/arkts-arkui-shadowoptions-i.md) \| Array&lt;ShadowOptions&gt; | 是 | 文本阴影设置项。 |

## textShadow

```TypeScript
readonly textShadow: Array<ShadowOptions>
```

获取属性字符串的文本阴影。

**类型：** Array&lt;ShadowOptions&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextShadowStyle-readonly textShadow: Array<ShadowOptions>--><!--Device-TextShadowStyle-readonly textShadow: Array<ShadowOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

