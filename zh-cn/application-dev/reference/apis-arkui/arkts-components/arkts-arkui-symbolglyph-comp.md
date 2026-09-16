# SymbolGlyph

SymbolGlyph组件用于显示系统预置的图标小符号，支持设置颜色、大小、粗细、渲染策略、动效策略等样式属性，适用于需要在应用中展示系统图标的场景，如导航栏图标、按钮图标、状态指示图标等。相比使用图片资源，SymbolGlyph具有体积小、可动态着色、支持动效等优势。<!--RP1--><!--RP1End-->

## 子组件

不支持子组件。

## SymbolGlyph

```TypeScript
SymbolGlyph(value?: Resource)
```

定义SymbolGlyph组件构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Resource](../arkts-apis/arkts-arkui-resource-t.md) | 否 | SymbolGlyph组件的资源名，如 &#36;r('sys.symbol.ohos_wifi')。不传入时不显示图标。 |

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EffectDirection](arkts-arkui-effectdirection-e.md) | 符号动效方向的枚举值。 |
| [EffectFillStyle](arkts-arkui-effectfillstyle-e.md) | EffectFillStyle的枚举值。 |
| [EffectScope](arkts-arkui-effectscope-e.md) | EffectScope的枚举值。 |
| [ReplaceEffectType](arkts-arkui-replaceeffecttype-e.md) | 替换动效类型的枚举值。 |
| [SymbolEffectStrategy](arkts-arkui-symboleffectstrategy-e.md) | 动效类型的枚举值。设置动效后，动效启动即生效，无需触发。 |
| [SymbolRenderingStrategy](arkts-arkui-symbolrenderingstrategy-e.md) | 渲染模式的枚举值。 |

## 示例

```TypeScript
### 示例1（设置渲染和动效策略）

从API version 11开始，该示例通过[renderingStrategy](#renderingstrategy)、[effectStrategy](#effectstrategy)属性展示了不同的渲染和动效策略。


```

```TypeScript
### 示例2（设置动效和阴影）

从API version 12开始，该示例通过[symbolEffect](#symboleffect12)属性展示了各种动效的效果以及结合[symbolShadow](arkts-arkui-symbolglyph-comp-attribute.md#symbolshadow)（从API version 20开始）的阴影效果。其中禁用动效和快速替换动效需要API version 20及以上版本支持。


```

```TypeScript
### 示例3（设置颜色渐变）

从API version 20开始，该示例通过[shaderStyle](#shaderstyle20)接口实现了SymbolGlyph组件显示为渐变色的功能。


```

```TypeScript
### 示例4（设置SymbolGlyph颜色）

该示例通过[fontColor](#fontcolor-1)属性传入ColorMetrics类型参数，设置SymbolGlyph组件的颜色。

从API版本26.0.0开始，新增支持[fontColor](#fontcolor-1)。


```

```TypeScript
### 示例5（设置字体粗细）

该示例通过[fontWeight](#fontweight-1)属性展示SymbolGlyph不同粗细配置下的效果：第一行图标小符号展示启用可变字重后，分别设置字重值为220和660的效果；第二行图标小符号展示在将设备的系统字体粗细设置为粗体后，分别设置跟随和不跟随设备的字体粗细级别自动更新的效果。

从API版本26.0.0开始，新增[fontWeight](#fontweight-1)属性。
```
