# application/AccessibilityExtensionContext

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AccessibilityExtensionContext](accessibilityextensioncontext-accessibilityextensioncontext-c.md) | 辅助功能扩展的上下文环境，用来配置辅助应用关注信息类型、查询节点信息、手势注入等。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessibilityExtensionContext](accessibilityextensioncontext-accessibilityextensioncontext-c-sys.md) | 辅助功能扩展的上下文环境，用来配置辅助应用关注信息类型、查询节点信息、手势注入等。 |
| [Parameter](accessibilityextensioncontext-parameter-c-sys.md) | 无障碍节点元素执行特定操作时，为操作提供具体设置的参数值。详见[AccessibilityAction]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_（无障碍节点元素可执行的操 作）。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityElement](accessibilityextensioncontext-accessibilityelement-i.md) | 无障碍节点元素。在调用 **AccessibilityElement** 的 API 之前，应该调用 [AccessibilityExtensionContext.getAccessibilityFocusedElement()]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 或 [AccessibilityExtensionContext.getRootInActiveWindow()]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 来获取一个 **AccessibilityElement** 实例。 |
| [ElementAttributeValues](accessibilityextensioncontext-elementattributevalues-i.md) | 节点元素具备的属性名称及属性值类型信息。 |
| [Rect](accessibilityextensioncontext-rect-i.md) | 表示矩形区域。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessibilityElement](accessibilityextensioncontext-accessibilityelement-i-sys.md) | 无障碍节点元素。在调用 **AccessibilityElement** 的 API 之前，应该调用 [AccessibilityExtensionContext.getAccessibilityFocusedElement()]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 或 [AccessibilityExtensionContext.getRootInActiveWindow()]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 来获取一个 **AccessibilityElement** 实例。 |
| [AccessibilityGrid](accessibilityextensioncontext-accessibilitygrid-i-sys.md) | 辅助功能网格信息。详见[AccessibilityElement]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的属性currentItem。 |
| [AccessibilitySpan](accessibilityextensioncontext-accessibilityspan-i-sys.md) | 辅助功能超链接文本信息。详见[AccessibilityElement]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的属性spans。 |
| [ElementAttributeValues](accessibilityextensioncontext-elementattributevalues-i-sys.md) | 节点元素具备的属性名称及属性值类型信息。 |
| [FocusMoveResult](accessibilityextensioncontext-focusmoveresult-i-sys.md) | 查询无障碍节点返回值类型。 |
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

