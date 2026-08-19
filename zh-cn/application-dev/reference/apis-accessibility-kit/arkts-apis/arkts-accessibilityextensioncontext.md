# AccessibilityExtensionContext

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AccessibilityExtensionContext](arkts-accessibility-accessibilityextensioncontext-c.md) | AccessibilityExtensionContext是AccessibilityExtensionAbility上下文环境，继承自ExtensionContext。 辅助功能扩展上下文模块提供辅助功能扩展的相关能力，包括配置关注信息类型、查询节点信息、手势注入等。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessibilityExtensionContext](arkts-accessibility-accessibilityextensioncontext-c-sys.md) | AccessibilityExtensionContext是AccessibilityExtensionAbility上下文环境，继承自ExtensionContext。 辅助功能扩展上下文模块提供辅助功能扩展的相关能力，包括配置关注信息类型、查询节点信息、手势注入等。 |
| [Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md) | 无障碍节点元素执行特定操作时，为操作提供具体设置的参数值。不同操作类型需设置不同的参数字段，各操作类型与参数字段的对应关系，详见 [AccessibilityAction](arkts-accessibility-accessibility-accessibilityaction-e-sys.md)（无障碍节点元素可执行的操作）。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md) | 无障碍节点元素，提供查询父/子元素、按内容或焦点方向查找元素、执行无障碍操作等能力，适用于无障碍辅助应用需要与界面节点交互和操作的场景。 调用AccessibilityElement的方法前，先通过 [AccessibilityExtensionContext.getFocusElement()](arkts-accessibility-accessibilityextensioncontext-c.md#getfocuselement) 或 [AccessibilityExtensionContext.getWindowRootElement()](arkts-accessibility-accessibilityextensioncontext-c.md#getwindowrootelement) 获取AccessibilityElement实例。 |
| [ElementAttributeValues](arkts-accessibility-accessibilityextensioncontext-elementattributevalues-i.md) | 节点元素具备的属性名称及属性值类型信息。 |
| [Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md) | 表示矩形区域。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i-sys.md) | 无障碍节点元素，提供查询父/子元素、按内容或焦点方向查找元素、执行无障碍操作等能力，适用于无障碍辅助应用需要与界面节点交互和操作的场景。 调用AccessibilityElement的方法前，先通过 [AccessibilityExtensionContext.getFocusElement()](arkts-accessibility-accessibilityextensioncontext-c.md#getfocuselement) 或 [AccessibilityExtensionContext.getWindowRootElement()](arkts-accessibility-accessibilityextensioncontext-c.md#getwindowrootelement) 获取AccessibilityElement实例。 |
| [AccessibilityGrid](arkts-accessibility-accessibilityextensioncontext-accessibilitygrid-i-sys.md) | 辅助功能网格信息。详见[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)中的属性currentItem。 |
| [AccessibilitySpan](arkts-accessibility-accessibilityextensioncontext-accessibilityspan-i-sys.md) | 辅助功能超链接文本信息。详见[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)中的属性spans。 |
| [AccessibilityVirtualNode](arkts-accessibility-accessibilityextensioncontext-accessibilityvirtualnode-i-sys.md) | 无障碍虚拟节点。 |
| [ElementAttributeValues](arkts-accessibility-accessibilityextensioncontext-elementattributevalues-i-sys.md) | 节点元素具备的属性名称及属性值类型信息。 |
| [FocusMoveResult](arkts-accessibility-accessibilityextensioncontext-focusmoveresult-i-sys.md) | 查询无障碍节点返回值类型。 |
| [TouchPosition](arkts-accessibility-accessibilityextensioncontext-touchposition-i-sys.md) | 触摸点击位置。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [FocusDirection](arkts-accessibility-focusdirection-t.md) | 表示查询下一焦点元素的方向。 |
| [FocusType](arkts-accessibility-focustype-t.md) | 表示查询焦点元素的类型。 |
| [WindowType](arkts-accessibility-windowtype-t.md) | 表示窗口的类型。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FocusCondition](arkts-accessibility-focuscondition-t-sys.md) | 表示查询可聚焦节点方式。 |
| [FocusRule](arkts-accessibility-focusrule-t-sys.md) | 表示查找可聚焦节点时，如何判断起始节点及其子节点的聚焦能力。 |
<!--DelEnd-->

