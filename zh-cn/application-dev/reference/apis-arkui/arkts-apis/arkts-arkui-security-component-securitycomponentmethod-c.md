# SecurityComponentMethod

安全控件通用属性模块，提供安全控件的布局、尺寸、文字、图标、颜色、边框和交互等通用属性的统一配置能力。  
- 为[PasteButton](./paste_button)、[SaveButton](./save_button)等安全控件统一设置布局、尺寸、文字、图标、颜色、边框和交互相关属性。  
- 在满足安全控件规范的前提下，调整安全控件显示效果和交互体验。具体约束请参见[约束与限制](../../../../security/AccessToken/security-component-overview.md#约束与限制)。  
- 通过链式调用方式复用安全控件通用属性能力。

## 核心枚举类型

- **[SecurityComponentLayoutDirection](arkts-arkui-security-component-securitycomponentlayoutdirection-e.md)：** 安全控件图标和文字排列方向枚举，用于指定横向或纵向布局。  
- **[ButtonType](@global:ButtonType)：** 安全控件按钮样式枚举，用于指定胶囊、圆形、圆角矩形或普通按钮样式。

## 核心接口类型

- **[SecurityComponentMethod](arkts-arkui-security-component-securitycomponentmethod-c.md)：** 安全控件通用属性方法集合，用于为具体安全控件配置布局、尺寸、文字、图标、颜色、边框和交互属性。

## 子组件

不支持

**起始版本：** 10

<!--Device-unnamed-declare class SecurityComponentMethod<T>--><!--Device-unnamed-declare class SecurityComponentMethod<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDefaultFocus

```TypeScript
accessibilityDefaultFocus(focus: boolean): T
```

设置页面的屏幕朗读初始焦点，用于指定页面加载后屏幕朗读首次播报的焦点组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-accessibilityDefaultFocus(focus: boolean): T--><!--Device-SecurityComponentMethod-accessibilityDefaultFocus(focus: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| focus | boolean | 是 | 为页面设置屏幕朗读初始焦点。值为true则表示该组件为当前页默认首焦点，值为false或其他值无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 当前对象。 |

## accessibilityDescription

```TypeScript
accessibilityDescription(description: string | Resource): T
```

该属性用于为控件提供无障碍描述。开发人员可通过设置详细的文字说明，帮助用户理解组件的功能及即将执行的操作。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-accessibilityDescription(description: string | Resource): T--><!--Device-SecurityComponentMethod-accessibilityDescription(description: string | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| description | string \| Resource | 是 | 控件的无障碍说明。用于补充组件的详细操作解释，帮助用户理解当前操作的具体内容及其潜在后果。控件被选中时，若组件同时包含文本属性和无障碍说明，优先播报文本内容，再播报无障碍说明。<br>该参数的默认值为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 当前对象。 |

## accessibilityNextFocusId

```TypeScript
accessibilityNextFocusId(nextId: string): T
```

支持在屏幕朗读过程中，指定朗读的下一个焦点组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-accessibilityNextFocusId(nextId: string): T--><!--Device-SecurityComponentMethod-accessibilityNextFocusId(nextId: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| nextId | string | 是 | 下一个被指定聚焦组件的 [唯一标识 ID](arkts-arkui-security-component-securitycomponentmethod-c.md#id-1)。若唯一标识id无对应组件，则设置无效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 当前对象。 |

## accessibilityRole

```TypeScript
accessibilityRole(role: SecurityComponentRoleType): T
```

设置无障碍组件类型，特定组件类型有特定的朗读方式，可以根据应用诉求，修改组件类型，用于控制无障碍模式下对组件的朗读方式和朗读内容。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-accessibilityRole(role: SecurityComponentRoleType): T--><!--Device-SecurityComponentMethod-accessibilityRole(role: SecurityComponentRoleType): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| role | [SecurityComponentRoleType](arkts-arkui-security-component-securitycomponentroletype-e.md) | 是 | 屏幕朗读播报的组件类型，如按钮、图表。具体类型可由开发者自定义。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 当前对象。 |

## align

```TypeScript
align(alignType: Alignment): T
```

设置安全控件图标文本的对齐方式。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-align(alignType: Alignment): T--><!--Device-SecurityComponentMethod-align(alignType: Alignment): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignType | [Alignment](arkts-arkui-enums-alignment-e.md) | 是 | 安全控件图标文本的对齐方式。图标文本作为整体在控件背景范围内进行对齐，显示效果受[padding](arkts-arkui-security-component-securitycomponentmethod-c.md#padding-1)影响，在padding生效的基础上按照alignType参数指定的对齐方式进行对齐。<br>默认值：Alignment.Center。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## alignRules

```TypeScript
alignRules(alignRule: AlignRuleOption): T
```

设置在相对容器中子组件的对齐规则，仅当父容器为[RelativeContainer](./relative_container)时生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-alignRules(alignRule: AlignRuleOption): T--><!--Device-SecurityComponentMethod-alignRules(alignRule: AlignRuleOption): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignRule | [AlignRuleOption](../arkts-components/arkts-arkui-common-alignruleoption-i.md) | 是 | 对齐规则配置对象，包含top、bottom、left、right、center等锚点对齐配置，用于指定安全控件在[RelativeContainer](./relative_container)中的对齐位置和方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## alignRules

```TypeScript
alignRules(alignRule: LocalizedAlignRuleOptions): T
```

设置在相对容器中子组件的对齐规则，仅当父容器为[RelativeContainer](./relative_container)时生效。该方法水平方向上以start和end分别替代上述[alignRules](arkts-arkui-security-component-securitycomponentmethod-c.md#alignrules-1)的left和right，以便在RTL模式下能镜像显示，建议优先使用该方法。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-alignRules(alignRule: LocalizedAlignRuleOptions): T--><!--Device-SecurityComponentMethod-alignRules(alignRule: LocalizedAlignRuleOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignRule | [LocalizedAlignRuleOptions](../arkts-components/arkts-arkui-common-localizedalignruleoptions-i.md) | 是 | 对齐规则配置对象，使用start和end替代left和right以支持RTL布局镜像。包含top、bottom、start、end、center等锚点对齐配置，用于指定安全控件在[RelativeContainer](./relative_container)中的对齐位置和方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## backgroundColor

```TypeScript
backgroundColor(value: ResourceColor): T
```

设置安全控件的背景颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-backgroundColor(value: ResourceColor): T--><!--Device-SecurityComponentMethod-backgroundColor(value: ResourceColor): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](arkts-arkui-resourcecolor-t.md) | 是 | 安全控件的背景颜色。<br>默认值：$r('sys.color.icon_emphasize')。<br>安全控件按钮背景色高八位的α值低于**0x1a**（例如**0x1800ff00**）时，会被系统强制调整为**0xff**。以确保安全控件具有足够的可见性，防止因控件过度透明导致用户在不知情的情况下触发授权。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## borderColor

```TypeScript
borderColor(value: ResourceColor): T
```

设置安全控件的边框颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-borderColor(value: ResourceColor): T--><!--Device-SecurityComponentMethod-borderColor(value: ResourceColor): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](arkts-arkui-resourcecolor-t.md) | 是 | 安全控件的边框颜色。<br>默认不设置边框颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## borderRadius

```TypeScript
borderRadius(value: Dimension): T
```

设置安全控件的边框圆角半径。

borderRadius的设置效果受ButtonType影响。当按钮类型为Capsule或Circle时，borderRadius设置不生效，按钮圆角半径由按钮类型自动确定；当按钮类型为Normal或ROUNDED_RECTANGLE时，borderRadius设置生效。具体影响请参见[ButtonType](@global:ButtonType)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-borderRadius(value: Dimension): T--><!--Device-SecurityComponentMethod-borderRadius(value: Dimension): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](arkts-arkui-dimension-t.md) | 是 | 安全控件的边框圆角半径。<br>默认值：**0vp**。<br>未显式指定单位时，单位为vp。<br/>不支持设置百分比字符串。圆角半径受组件尺寸限制，最小值为0，最大值为宽高中较小值的一半。设置异常值时该属性不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## borderRadius

```TypeScript
borderRadius(radius: Dimension | BorderRadiuses): T
```

设置安全控件的边框圆角半径，支持分别设置四个圆角的半径。

borderRadius的设置效果受ButtonType影响。当按钮类型为Capsule或Circle时，borderRadius设置不生效，按钮圆角半径由按钮类型自动确定；当按钮类型为Normal或ROUNDED_RECTANGLE时，borderRadius设置生效。具体影响请参见[ButtonType](@global:ButtonType)。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-borderRadius(radius: Dimension | BorderRadiuses): T--><!--Device-SecurityComponentMethod-borderRadius(radius: Dimension | BorderRadiuses): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | Dimension \| BorderRadiuses | 是 | 安全控件的边框圆角半径。<br>默认值：**0vp**。<br>未显式指定单位时，单位为vp。<br>Dimension类型不支持设置百分比字符串。圆角半径受组件尺寸限制，最小值为0，最大值为宽高中较小值的一半。设置异常值时该属性不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## borderStyle

```TypeScript
borderStyle(value: BorderStyle): T
```

设置安全控件边框的样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-borderStyle(value: BorderStyle): T--><!--Device-SecurityComponentMethod-borderStyle(value: BorderStyle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BorderStyle](arkts-arkui-enums-borderstyle-e.md) | 是 | 安全控件边框的样式。<br>默认不设置边框样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全组件的属性。 |

## borderWidth

```TypeScript
borderWidth(value: Dimension): T
```

设置安全控件的边框宽度。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-borderWidth(value: Dimension): T--><!--Device-SecurityComponentMethod-borderWidth(value: Dimension): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](arkts-arkui-dimension-t.md) | 是 | 安全控件的边框宽度。<br>默认值：**0vp**。<br>未显式指定单位时，单位为vp。<br/>不支持设置百分比字符串。设置异常值时该属性不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## chainMode

```TypeScript
chainMode(direction: Axis, style: ChainStyle): T
```

设置以该组件为链头所构成的链式布局的参数（包括链的方向和样式），仅当父容器为[RelativeContainer](./relative_container)时生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-chainMode(direction: Axis, style: ChainStyle): T--><!--Device-SecurityComponentMethod-chainMode(direction: Axis, style: ChainStyle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | [Axis](arkts-arkui-enums-axis-e.md) | 是 | 链式布局的方向，用于指定以该组件为链头的链在[RelativeContainer](./relative_container)中的排列方向。 |
| style | [ChainStyle](../arkts-components/arkts-arkui-common-chainstyle-e.md) | 是 | 链式布局的样式，用于控制链内子组件的分布方式，如均匀分布、两端对齐或紧凑排列等，具体取值及效果请参考[ChainStyle](../arkts-components/arkts-arkui-common-chainstyle-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## constraintSize

```TypeScript
constraintSize(value: ConstraintSizeOptions): T
```

设置约束尺寸，组件布局时限制尺寸范围。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-constraintSize(value: ConstraintSizeOptions): T--><!--Device-SecurityComponentMethod-constraintSize(value: ConstraintSizeOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ConstraintSizeOptions](arkts-arkui-units-constraintsizeoptions-i.md) | 是 | 约束尺寸，组件布局时进行尺寸范围限制。<br>未显式指定单位时，单位为vp。<br>constraintSize的优先级高于width和height。<br>使用自适应字号相关属性时，安全控件文本未完全显示将导致点击不授权。constraintSize的设置会影响文本是否能完整显示。<br>取值结果参考[constraintSize取值对width/height影响](arkts-arkui-security-component-securitycomponentmethod-c.md#constraintsize-1)。<br>默认值：<br>{<br>minWidth: 0,<br>maxWidth: Infinity,<br>minHeight: 0,<br>maxHeight: Infinity<br>}。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## enabled

```TypeScript
enabled(respond: boolean): T
```

设置安全控件是否可交互。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-enabled(respond: boolean): T--><!--Device-SecurityComponentMethod-enabled(respond: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| respond | boolean | 是 | 安全控件是否可交互的值。<br>默认值：true。<br>值为true表示组件可交互，响应点击等操作。<br>值为false表示组件不可交互，不响应点击等操作。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Attribute of the security component. |

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing(enabled: boolean): T
```

针对多行文字叠加，支持行高基于文字实际高度自适应。

fallbackLineSpacing属性和[RichEditorTextStyle](../arkts-components/arkts-arkui-rich-editor-richeditortextstyle-i.md)的lineHeight属性强相关。当设置的 lineHeight值小于文本在当前字号下的实际渲染高度时，将根据fallbackLineSpacing 属性值来确定行高是否要基于文字实际高度自适应。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-fallbackLineSpacing(enabled: boolean): T--><!--Device-SecurityComponentMethod-fallbackLineSpacing(enabled: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 行高是否基于文字实际高度自适应。<br/>true表示行高基于文字实际高度自适应；false表示行高不基于文字实际高度自适应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## focusBox

```TypeScript
focusBox(style: FocusBoxStyle): T
```

设置安全控件系统焦点框样式。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-focusBox(style: FocusBoxStyle): T--><!--Device-SecurityComponentMethod-focusBox(style: FocusBoxStyle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [FocusBoxStyle](arkts-arkui-focus-focusboxstyle-i.md) | 是 | 焦点框样式配置对象，包含margin（焦点框与控件的间距）和strokeColor（焦点框边框颜色）等属性，用于自定义系统焦点框的外观样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全组件的属性。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor): T
```

设置安全控件文字的颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-fontColor(value: ResourceColor): T--><!--Device-SecurityComponentMethod-fontColor(value: ResourceColor): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](arkts-arkui-resourcecolor-t.md) | 是 | 安全控件上文字的颜色。<br>默认值：$r('sys.color.font_on_primary')。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## fontFamily

```TypeScript
fontFamily(value: string | Resource): T
```

设置安全控件文字的字体。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-fontFamily(value: string | Resource): T--><!--Device-SecurityComponentMethod-fontFamily(value: string | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| Resource | 是 | 安全控件上文字的字体。<br>默认字体：'HarmonyOS Sans'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## fontSize

```TypeScript
fontSize(value: Dimension): T
```

设置安全控件文字的尺寸。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-fontSize(value: Dimension): T--><!--Device-SecurityComponentMethod-fontSize(value: Dimension): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](arkts-arkui-dimension-t.md) | 是 | 安全控件上文字的尺寸。<br>未显式指定单位时，单位为fp。<br>默认值：$r('sys.float.ohos_id_text_size_button1')。<br>该参数不支持百分比字符串。<br>设置异常值时该属性不生效。<br>**说明：** 安全控件文本未完全显示时，点击不授权。fontSize的设置会影响文本是否能完整显示，进而影响安全控件的授权行为。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## fontStyle

```TypeScript
fontStyle(value: FontStyle): T
```

设置安全控件文字的样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-fontStyle(value: FontStyle): T--><!--Device-SecurityComponentMethod-fontStyle(value: FontStyle): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FontStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontstyle-e.md) | 是 | 安全控件上文字的样式。<br>默认值：FontStyle.Normal。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string | Resource): T
```

设置安全控件文字的粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-fontWeight(value: number | FontWeight | string | Resource): T--><!--Device-SecurityComponentMethod-fontWeight(value: number | FontWeight | string | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| string \| Resource | 是 | 安全控件上文字粗细。<br>number类型取值[100, 900]，取值间隔为100，取值越大，字体越粗。<br>string类型支持使用数字字符串（如'400'），以及FontWeight中的枚举值对应的字符串（如'bold'、'bolder'、'lighter'、'regular'、'medium'）。<br>从API version 20开始，支持Resource类型。Resource类型仅支持'integer'和'string'。类型为'integer'时，取值参考前述number类型；类型为'string'时，取值参考前述string类型。<br>如果控件未设置fontWeight，文字粗细将默认设置为FontWeight.Medium。value入参为undefined、null，或number类型不在[100, 900]范围内，或string类型不符合FontWeight枚举值对应的字符串格式时，文字粗细将被设置为FontWeight.Normal。<br>**起始版本：** 20 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## height

```TypeScript
height(value: Length): T
```

设置安全控件自身的高度，缺省时将根据元素内容自适配高度。配合自适应字号相关属性使用时，height的设置会影响文本是否能完整显示。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-height(value: Length): T--><!--Device-SecurityComponentMethod-height(value: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](arkts-arkui-length-t.md) | 是 | 安全控件自身的高度，缺省时将根据元素内容自适配高度。<br>未显式指定单位时，单位为vp。<br>配合[minFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#minfontsize-1)、[maxFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#maxfontsize-1)、[maxLines](arkts-arkui-security-component-securitycomponentmethod-c.md#maxlines-1)以及[heightAdaptivePolicy](arkts-arkui-security-component-securitycomponentmethod-c.md#heightadaptivepolicy-1)使用实现自适应字号时，安全控件文本未完全显示将导致点击不授权。设置异常值时该属性不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## heightAdaptivePolicy

```TypeScript
heightAdaptivePolicy(policy: TextHeightAdaptivePolicy): T
```

设置文字自适应高度的方式。适用于安全控件在不同尺寸或不同语言环境下，需要动态调整文本显示以保证文本完整显示的场景。

安全控件文本以[maxFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#maxfontsize-1)的值进行布局，如果可以完整显示文本，则无需进行自适应调节，该接口设置不生效，否则按指定文本自适应高度的方式进行调节，具体自适应调节规格如下：

当设置为TextHeightAdaptivePolicy.MAX_LINES_FIRST时，优先使用[maxLines](arkts-arkui-security-component-securitycomponentmethod-c.md#maxlines-1)属性来调整文本高度。如果使用maxLines属性的布局大小超过了布局约束，则尝试在[minFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#minfontsize-1)和[maxFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#maxfontsize-1)的范围内缩小字体以显示更多文本，如果此时仍不能完整显示文本信息，安全控件会自适应调整高度以使得文本完整显示。

当设置为TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST时，优先使用[minFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#minfontsize-1)属性来调整文本高度。如果使用minFontSize属性可以将文本布局在一行中，则尝试在minFontSize和[maxFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#maxfontsize-1)的范围内增大字体并使用最大可能的字体大小；如果使用minFontSize属性无法将文本布局在一行中，则尝试使用[maxLines](arkts-arkui-security-component-securitycomponentmethod-c.md#maxlines-1)属性进行布局，如果此时仍不能完整显示文本信息，安全控件会自适应调整高度以使得文本完整显示。

当设置为TextHeightAdaptivePolicy.LAYOUT_CONSTRAINT_FIRST时，优先使用布局约束来调整文本高度。如果布局大小超过布局约束，则尝试在[minFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#minfontsize-1)和[maxFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#maxfontsize-1)的范围内缩小字体以满足布局约束。如果将字体大小缩小到minFontSize后，布局大小仍然超过布局约束，则删除超过布局约束的行；如果设置了[maxLines](arkts-arkui-security-component-securitycomponentmethod-c.md#maxlines-1)属性，布局后行数不超过maxLines值（可能存在横向截断）；如果未设置maxLines属性值，布局后的行数不限制。

安全控件文本未完全显示时，点击不授权。文本是否完全显示受heightAdaptivePolicy、minFontSize、maxFontSize、maxLines、width和height等属性影响。

具体效果请见[示例](../../../../reference/apis-arkui/arkui-ts/ts-securitycomponent-attributes.md#示例3)。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-heightAdaptivePolicy(policy: TextHeightAdaptivePolicy): T--><!--Device-SecurityComponentMethod-heightAdaptivePolicy(policy: TextHeightAdaptivePolicy): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | [TextHeightAdaptivePolicy](arkts-arkui-enums-textheightadaptivepolicy-e.md) | 是 | 文本自适应高度的方式。<br>默认值：TextHeightAdaptivePolicy.MAX_LINES_FIRST。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## iconColor

```TypeScript
iconColor(value: ResourceColor): T
```

设置安全控件图标的颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-iconColor(value: ResourceColor): T--><!--Device-SecurityComponentMethod-iconColor(value: ResourceColor): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](arkts-arkui-resourcecolor-t.md) | 是 | 安全控件上图标的颜色。<br>默认值：$r('sys.color.icon_on_primary')。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## iconSize

```TypeScript
iconSize(value: Dimension): T
```

设置安全控件图标的尺寸。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-iconSize(value: Dimension): T--><!--Device-SecurityComponentMethod-iconSize(value: Dimension): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](arkts-arkui-dimension-t.md) | 是 | 安全控件上图标的尺寸。未显式指定单位时，单位为vp。<br>默认值：**16vp**。<br>该参数不支持百分比字符串。<br/>若传入异常值或无效单位，属性不生效，控件按照默认值显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## id

```TypeScript
id(id: string): T
```

组件的唯一标识，唯一性由使用者保证。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-id(id: string): T--><!--Device-SecurityComponentMethod-id(id: string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 组件的唯一标识，唯一性由使用者保证。<br>默认值：''。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## layoutDirection

```TypeScript
layoutDirection(value: SecurityComponentLayoutDirection): T
```

设置安全控件图标和文字分布的方向。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-layoutDirection(value: SecurityComponentLayoutDirection): T--><!--Device-SecurityComponentMethod-layoutDirection(value: SecurityComponentLayoutDirection): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SecurityComponentLayoutDirection](arkts-arkui-security-component-securitycomponentlayoutdirection-e.md) | 是 | 安全控件上图标和文字分布的方向。<br>默认值：SecurityComponentLayoutDirection.HORIZONTAL。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## markAnchor

```TypeScript
markAnchor(value: Position): T
```

设置安全控件在位置定位时的锚点，以控件左上角作为基准点进行偏移。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-markAnchor(value: Position): T--><!--Device-SecurityComponentMethod-markAnchor(value: Position): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Position](arkts-arkui-display-position-i.md) | 是 | 安全控件在位置定位时的锚点，以控件左上角作为基准点进行偏移。通常与position()、offset()配合使用，用于更精细地设置控件展示位置。<br>未显式指定单位时，单位为vp。<br/>无默认值。<br/>传入异常值时该属性不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## maxFontScale

```TypeScript
maxFontScale(scale: number | Resource): T
```

设置文本最大的字体放大倍数。调用后，当系统字体缩放使文本放大时，文本放大倍数不会超过设定的最大放大倍数。

与[minFontScale](arkts-arkui-security-component-securitycomponentmethod-c.md#minfontscale-1)可配合使用，maxFontScale控制放大倍数的上限，minFontScale控制缩小倍数的下限。两者可独立设置，也可同时设置以精确控制字体缩放范围。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-maxFontScale(scale: number | Resource): T--><!--Device-SecurityComponentMethod-maxFontScale(scale: number | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number \| Resource | 是 | 文本最大的字体放大倍数。<br>取值应≥1。<br>**说明：** <br>设置的值小于1时，按值为1处理；设置的值为undefined或null等非法值时，属性不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## maxFontSize

```TypeScript
maxFontSize(maxSize: number | string | Resource): T
```

设置文本最大显示字号。

- 配合[minFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#minfontsize-1)以及[maxLines](arkts-arkui-security-component-securitycomponentmethod-c.md#maxlines-1)或布局大小限制使用，可实现自适应字号，单独设置不生效。  
- maxFontSize应大于minFontSize，若maxFontSize小于minFontSize，minFontSize将按maxFontSize处理。  
- 当自适应字号生效时，设置的fontSize将不生效。  
- 安全控件文本未完全显示时，点击不授权。maxFontSize的设置会影响文本是否能完整显示，进而影响安全控件的授权行为。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-maxFontSize(maxSize: number | string | Resource): T--><!--Device-SecurityComponentMethod-maxFontSize(maxSize: number | string | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxSize | number \| string \| Resource | 是 | 文本最大显示字号。<br>取值应&gt;0。<br>未显式指定单位时，单位为fp。<br>**说明：**<br>设置的值小于或等于0时，自适应字号不生效；设置异常值时该属性不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## maxLines

```TypeScript
maxLines(line: number | Resource): T
```

设置文本的最大行数。默认情况下，文本自动换行，指定此属性后，文本的最大显示行数不会超过指定值。可独立使用限制文本行数，也可配合[minFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#minfontsize-1)、[maxFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#maxfontsize-1)以及[heightAdaptivePolicy](arkts-arkui-security-component-securitycomponentmethod-c.md#heightadaptivepolicy-1)使用。配合自适应字号相关属性使用时，安全控件文本未完全显示将导致点击不授权。maxLines的设置会影响文本是否能完整显示，进而影响安全控件的授权行为。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-maxLines(line: number | Resource): T--><!--Device-SecurityComponentMethod-maxLines(line: number | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| line | number \| Resource | 是 | 文本的最大行数。<br>number类型入参的取值范围： [1, +∞)。从API version 20开始，支持Resource类型。Resource类型仅支持'integer'，取值范围为[1, +∞)。**说明：**<br>设置的值小于1时，按默认值1000000处理。<br>**起始版本：** 18 - 19 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## minFontScale

```TypeScript
minFontScale(scale: number | Resource): T
```

设置文本最小的字体缩小倍数。调用后，当系统字体缩放使文本缩小时，文本缩小倍数不会低于设定的最小缩小倍数。

与[maxFontScale](arkts-arkui-security-component-securitycomponentmethod-c.md#maxfontscale-1)可配合使用，minFontScale控制缩小倍数的下限，maxFontScale控制放大倍数的上限。两者可独立设置，也可同时设置以精确控制字体缩放范围。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-minFontScale(scale: number | Resource): T--><!--Device-SecurityComponentMethod-minFontScale(scale: number | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number \| Resource | 是 | 文本最小的字体缩小倍数。<br>取值范围：[0,1]。<br>**说明：**<br>设置的值小于0时，按值为0处理，即允许缩小到任意倍数；设置的值大于1时，按值为1处理，即不允许缩小字体；设置的值为undefined或null等非法值时，属性不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## minFontSize

```TypeScript
minFontSize(minSize: number | string | Resource): T
```

设置文本最小显示字号。

- 配合[maxFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#maxfontsize-1)以及[maxLines](arkts-arkui-security-component-securitycomponentmethod-c.md#maxlines-1)或布局大小限制使用，可实现自适应字号，单独设置不生效。  
- minFontSize应小于maxFontSize，若设置值大于maxFontSize，将按maxFontSize处理。  
- minFontSize小于或等于0时，自适应字号不生效。  
- 自适应字号生效时，fontSize设置不生效。  
- 安全控件文本未完全显示时，点击不授权。minFontSize的设置会影响文本是否能完整显示，进而影响安全控件的授权行为。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-minFontSize(minSize: number | string | Resource): T--><!--Device-SecurityComponentMethod-minFontSize(minSize: number | string | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minSize | number \| string \| Resource | 是 | 文本最小显示字号。<br>取值应&gt;0。<br>未显式指定单位时，单位为fp。<br> minFontSize应小于maxFontSize，若设置值大于maxFontSize，将按maxFontSize处理；小于或等于0时，自适应字号不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## offset

```TypeScript
offset(value: Position | Edges | LocalizedEdges): T
```

设置安全控件相对于自身布局位置的坐标偏移。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-offset(value: Position | Edges | LocalizedEdges): T--><!--Device-SecurityComponentMethod-offset(value: Position | Edges | LocalizedEdges): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Position \| Edges \| LocalizedEdges | 是 | 安全控件相对于自身布局位置的坐标偏移。设置后不会影响父容器布局，仅在绘制阶段调整控件显示位置。<br>未显式指定单位时，单位为vp。<br/>无默认值。<br>当入参异常时，该属性不生效。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## padding

```TypeScript
padding(value: Padding | Dimension): T
```

设置安全控件的内边距。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-padding(value: Padding | Dimension): T--><!--Device-SecurityComponentMethod-padding(value: Padding | Dimension): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Padding \| Dimension | 是 | 安全控件的内边距。<br>默认值：上下8vp，左右16vp。<br>未显式指定单位时，单位为vp。<br/>**说明：** 本参数不支持设置百分比字符串数据类型。若设置百分比字符串，则对应内边距显示为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## position

```TypeScript
position(value: Position): T
```

设置绝对定位，即安全控件的左上角相对于父容器左上角的偏移位置。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-position(value: Position): T--><!--Device-SecurityComponentMethod-position(value: Position): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Position](arkts-arkui-display-position-i.md) | 是 | 安全控件左上角相对于父容器左上角的偏移位置。适用于通过绝对定位将安全控件放置到页面固定区域的场景。<br>未显式指定单位时，单位为vp。<br/>x和y建议均传入数值型坐标。<br/>若参数为undefined、null，或x、y为非数字类型时，该属性不生效，异常坐标会按0处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## size

```TypeScript
size(value: SizeOptions): T
```

设置宽度和高度，缺省时将根据元素内容自适配宽高尺寸。size方法用于同时设置宽度和高度，如需单独设置宽度或高度，可使用[width](arkts-arkui-security-component-securitycomponentmethod-c.md#width-1)或[height](arkts-arkui-security-component-securitycomponentmethod-c.md#height-1)方法。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-size(value: SizeOptions): T--><!--Device-SecurityComponentMethod-size(value: SizeOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SizeOptions](arkts-arkui-units-sizeoptions-i.md) | 是 | 宽度和高度，缺省时将根据元素内容自适配宽高尺寸。<br>未显式指定单位时，单位为vp。<br>配合 [minFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#minfontsize-1)、[maxFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#maxfontsize-1)、[maxLines](arkts-arkui-security-component-securitycomponentmethod-c.md#maxlines-1)以及[heightAdaptivePolicy](arkts-arkui-security-component-securitycomponentmethod-c.md#heightadaptivepolicy-1)使用实现自适应字号时，安全控件文本未完全显示将导致点击不授权。size的设置会影响文本是否能完整显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## textIconSpace

```TypeScript
textIconSpace(value: Dimension): T
```

设置安全控件中图标和文字的间距。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-textIconSpace(value: Dimension): T--><!--Device-SecurityComponentMethod-textIconSpace(value: Dimension): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension](arkts-arkui-dimension-t.md) | 是 | 安全控件中图标和文字的间距。<br>默认值：**4vp**。<br/><br>未显式指定单位时，单位为vp。<br/>**说明：** 本参数不支持设置百分比字符串数据类型，若设置百分比字符串，则图标和文字的间距显示为0；从API version 14开始，若设置值为负值，则使用默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

## width

```TypeScript
width(value: Length): T
```

设置安全控件自身的宽度，缺省时将根据元素内容自适配宽度。配合自适应字号相关属性使用时，width的设置会影响文本是否能完整显示。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SecurityComponentMethod-width(value: Length): T--><!--Device-SecurityComponentMethod-width(value: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](arkts-arkui-length-t.md) | 是 | 安全控件自身的宽度，缺省时将根据元素内容自适配宽度。<br>未显式指定单位时，单位为vp。<br>配合 [minFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#minfontsize-1)、[maxFontSize](arkts-arkui-security-component-securitycomponentmethod-c.md#maxfontsize-1)、[maxLines](arkts-arkui-security-component-securitycomponentmethod-c.md#maxlines-1)以及[heightAdaptivePolicy](arkts-arkui-security-component-securitycomponentmethod-c.md#heightadaptivepolicy-1)使用实现自适应字号时，安全控件文本未完全显示将导致点击不授权。设置异常值时该属性不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |

