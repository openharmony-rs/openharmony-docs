# LinearGradientStyle

显示为线性渐变。LinearGradientStyle继承自[ShaderStyle](arkts-arkui-shaderstyle-c.md)。

**继承/实现关系：** LinearGradientStyle extends [ShaderStyle](arkts-arkui-shaderstyle-c.md)

**起始版本：** 20

<!--Device-unnamed-declare class LinearGradientStyle extends ShaderStyle--><!--Device-unnamed-declare class LinearGradientStyle extends ShaderStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(options: LinearGradientOptions)
```

用于创建LinearGradientStyle对象的构造函数。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LinearGradientStyle-constructor(options: LinearGradientOptions)--><!--Device-LinearGradientStyle-constructor(options: LinearGradientOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [LinearGradientOptions](../arkts-components/arkts-arkui-lineargradientoptions-i.md) | 是 | 显示为线性渐变效果。<br/>[LinearGradientOptions](../arkts-components/arkts-arkui-lineargradientoptions-i.md)中的direction默认值按[GradientDirection](arkts-arkui-gradientdirection-e.md)中的NONE处理。 |

## options

```TypeScript
options: LinearGradientOptions
```

显示为线性渐变效果。

**类型：** LinearGradientOptions

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-LinearGradientStyle-options: LinearGradientOptions--><!--Device-LinearGradientStyle-options: LinearGradientOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

