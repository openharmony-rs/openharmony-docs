# SymbolGlyph

SymbolGlyph组件用于显示系统预置的图标小符号，支持设置颜色、大小、粗细、渲染策略、动效策略等样式属性，适用于需要在应用中展示系统图标的场景，如导航栏图标、按钮图标、状态指示图标等。相比使用图片资源，SymbolGlyph具有 体积小、可动态着色、支持动效等优势。<!--RP1--><!--RP1End-->

## 子组件 不支持子组件。

## SymbolGlyph

```TypeScript
SymbolGlyph(value?: Resource)
```

定义SymbolGlyph组件构造函数。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-SymbolGlyphInterface-(value?: Resource): SymbolGlyphAttribute--><!--Device-SymbolGlyphInterface-(value?: Resource): SymbolGlyphAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | SymbolGlyph组件的资源名，如 \$r('sys.symbol.ohos\_wifi')。不传入时不显示图标。  |

## 汇总

