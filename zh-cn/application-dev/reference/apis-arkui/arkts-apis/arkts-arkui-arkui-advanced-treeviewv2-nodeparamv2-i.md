# NodeParamV2

节点参数接口，用于配置树节点的属性。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CallbackParamV2, NodeParamV2, TreeControllerV2, TreeListenerV2, TreeListenerManagerV2, TreeViewV2 } from '@kit.ArkUI';
```

## container

```TypeScript
container?: OnContainerCallback
```

绑定在节点上的右键子组件，子组件由@Builder修饰。默认值：() =&gt; void

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentNodeId

```TypeScript
currentNodeId?: number
```

当前子节点Id。取值范围：大于等于-1。不能为根节点id，不能为null，否则会抛出异常。且不能设置两个相同的currentNodeId。默认值：-1

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## editIcon

```TypeScript
editIcon?: ResourceStr
```

编辑图标。默认值：空字符串。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

图标。默认值：空字符串。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isFolder

```TypeScript
isFolder?: boolean
```

是否是目录。默认值：false true：是目录，false：不是目录。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## parentNodeId

```TypeScript
parentNodeId?: number
```

父节点Id。取值范围：大于等于-1。默认值：-1，根节点id值为-1。若设置数值小于-1，该节点无效，不显示在树视图上。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

主标题。默认值：空字符串。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

副标题。默认值：空字符串。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIcon

```TypeScript
selectedIcon?: ResourceStr
```

选中图标。默认值：空字符串。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolEditIconStyle

```TypeScript
symbolEditIconStyle?: SymbolGlyphModifier
```

Symbol编辑图标样式，优先级大于editIcon。默认值：undefined，编辑时显示与非编辑态一样

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolIconStyle

```TypeScript
symbolIconStyle?: SymbolGlyphModifier
```

Symbol图标样式，显示优先级大于icon，同时设置symbolIconStyle和icon，只显示Symbol图标。默认值：undefined，表示不显示Symbol图标。

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolSelectedIconStyle

```TypeScript
symbolSelectedIconStyle?: SymbolGlyphModifier
```

Symbol选中图标样式，优先级大于selectedIcon。默认值：undefined，选中时显示与未选中一样

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
