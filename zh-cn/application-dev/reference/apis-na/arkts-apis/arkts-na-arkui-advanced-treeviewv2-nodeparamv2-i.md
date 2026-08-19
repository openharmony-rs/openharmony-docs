# NodeParamV2

节点参数接口，用于配置树节点的属性。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export interface NodeParamV2--><!--Device-unnamed-export interface NodeParamV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## container

```TypeScript
container?: OnContainerCallback
```

绑定在节点上的右键子组件，子组件由@Builder修饰。 默认值：() => void

**类型：** [OnContainerCallback](arkts-na-oncontainercallback-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-container?: OnContainerCallback--><!--Device-NodeParamV2-container?: OnContainerCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentNodeId

```TypeScript
currentNodeId?: int
```

当前子节点Id。 取值范围：大于等于-1。 不能为根节点id，不能为null，否则会抛出异常。且不能设置两个相同的currentNodeId。 默认值：-1

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-currentNodeId?: int--><!--Device-NodeParamV2-currentNodeId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## editIcon

```TypeScript
editIcon?: ResourceStr
```

编辑图标。 默认值：空字符串。

**类型：** [ResourceStr](arkts-na-resourcestr-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-editIcon?: ResourceStr--><!--Device-NodeParamV2-editIcon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

图标。 默认值：空字符串。

**类型：** [ResourceStr](arkts-na-resourcestr-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-icon?: ResourceStr--><!--Device-NodeParamV2-icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isFolder

```TypeScript
isFolder?: boolean
```

是否是目录。 默认值：false true：是目录，false：不是目录。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-isFolder?: boolean--><!--Device-NodeParamV2-isFolder?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## parentNodeId

```TypeScript
parentNodeId?: int
```

父节点Id。 取值范围：大于等于-1。 默认值：-1，根节点id值为-1。若设置数值小于-1，该节点无效，不显示在树视图上。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-parentNodeId?: int--><!--Device-NodeParamV2-parentNodeId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

主标题。 默认值：空字符串。

**类型：** [ResourceStr](arkts-na-resourcestr-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-primaryTitle?: ResourceStr--><!--Device-NodeParamV2-primaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

副标题。 默认值：空字符串。

**类型：** [ResourceStr](arkts-na-resourcestr-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-secondaryTitle?: ResourceStr--><!--Device-NodeParamV2-secondaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIcon

```TypeScript
selectedIcon?: ResourceStr
```

选中图标。 默认值：空字符串。

**类型：** [ResourceStr](arkts-na-resourcestr-t.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-selectedIcon?: ResourceStr--><!--Device-NodeParamV2-selectedIcon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolEditIconStyle

```TypeScript
symbolEditIconStyle?: SymbolGlyphModifier
```

Symbol编辑图标样式，优先级大于editIcon。 默认值：undefined，编辑时显示与非编辑态一样

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-symbolEditIconStyle?: SymbolGlyphModifier--><!--Device-NodeParamV2-symbolEditIconStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolIconStyle

```TypeScript
symbolIconStyle?: SymbolGlyphModifier
```

Symbol图标样式，显示优先级大于icon，同时设置symbolIconStyle和icon，只显示Symbol图标。 默认值：undefined，表示不显示Symbol图标。

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-symbolIconStyle?: SymbolGlyphModifier--><!--Device-NodeParamV2-symbolIconStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolSelectedIconStyle

```TypeScript
symbolSelectedIconStyle?: SymbolGlyphModifier
```

Symbol选中图标样式，优先级大于selectedIcon。 默认值：undefined，选中时显示与未选中一样

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NodeParamV2-symbolSelectedIconStyle?: SymbolGlyphModifier--><!--Device-NodeParamV2-symbolSelectedIconStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

