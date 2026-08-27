# SymbolGlyphModifier

Defines SymbolGlyph Modifier

**继承/实现关系：** SymbolGlyphModifier extends [SymbolGlyphAttribute](../arkts-components/arkts-arkui-symbolglyph-attribute.md) implements AttributeModifier<SymbolGlyphAttribute>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## applyNormalAttribute

```TypeScript
applyNormalAttribute?(instance: SymbolGlyphAttribute): void
```

组件在普通状态（即未被按下、未获得焦点等默认交互状态）下的样式设置。该方法为回调方法，在组件处于普通状态时由框架自动调用，开发者可在方法体内通过修改instance对象的属性来动态设置SymbolGlyph组件的样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| instance | [SymbolGlyphAttribute](../arkts-components/arkts-arkui-symbolglyph-attribute.md) | 是 |  |

## constructor

```TypeScript
constructor(src?: Resource)
```

SymbolGlyphModifier的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Resource | 否 |  |
