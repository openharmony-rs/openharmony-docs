# @ohos.application.AccessibilityExtensionAbility

## 导入模块

```TypeScript
import { AccessibilityExtensionAbility, AccessibilityElement, AccessibilityExtensionContext, ElementAttributeKeys, ElementAttributeValues, FocusDirection, FocusType, Rect, WindowType, AccessibilityEvent, AccessibilityEventInfo, Parameter, FocusRule, FocusCondition, FocusMoveResult, AccessibilityVirtualNode, TouchPosition } from '@kit.AccessibilityKit';
import { AccessibilityExtensionAbility, AccessibilityElement, AccessibilityExtensionContext, FocusDirection, Rect, WindowType, AccessibilityEventInfo, Parameter, FocusRule, FocusCondition, FocusMoveResult, AccessibilityVirtualNode, TouchPosition } from '@kit.AccessibilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AccessibilityExtensionAbility](arkts-accessibility-application-accessibilityextensionability-accessibilityextensionability-c.md) | AccessibilityExtensionAbility基于ExtensionAbility框架，提供辅助功能扩展业务的能力。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessibilityExtensionAbility](arkts-accessibility-application-accessibilityextensionability-accessibilityextensionability-c-sys.md) | AccessibilityExtensionAbility基于ExtensionAbility框架，提供辅助功能扩展业务的能力。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityEvent](arkts-accessibility-application-accessibilityextensionability-accessibilityevent-i.md) | 无障碍事件信息。无障碍事件由系统无障碍服务在用户操作或界面变化时生成，通过eventType标识事件类别（包括无障碍事件类型、窗口变化类型、触摸浏览事件类型、手势事件类型、页面更新类型），辅助功能扩展可通过 onAccessibilityEvent回调接收并处理这些事件。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessibilityEventInfo](arkts-accessibility-application-accessibilityextensionability-accessibilityeventinfo-i-sys.md) | 无障碍事件信息。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AccessibilityElement](arkts-accessibility-accessibilityelement-t.md) | 表示无障碍节点元素，请参考[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)。 |
| [AccessibilityExtensionContext](arkts-accessibility-accessibilityextensioncontext-t.md) | 表示辅助功能扩展的上下文环境，请参考 [AccessibilityExtensionContext](arkts-accessibility-accessibilityextensioncontext-c.md)。 |
| [ElementAttributeKeys](arkts-accessibility-elementattributekeys-t.md) | 表示[ElementAttributeValues](arkts-accessibility-accessibilityextensioncontext-elementattributevalues-i.md)的属性名称。 |
| [ElementAttributeValues](arkts-accessibility-elementattributevalues-t.md) | 表示节点元素具备的属性名称及属性值类型信息，请参考 [ElementAttributeValues](arkts-accessibility-accessibilityextensioncontext-elementattributevalues-i.md)。 |
| [FocusDirection](arkts-accessibility-focusdirection-t.md) | 表示查询下一焦点元素的方向，请参考[FocusDirection](arkts-accessibility-focusdirection-t.md)。 |
| [FocusType](arkts-accessibility-focustype-t.md) | 表示查询焦点元素的类型，请参考[FocusType](arkts-accessibility-focustype-t.md)。 |
| [GestureType](arkts-accessibility-gesturetype-t.md) | 手势事件类型。手势事件在用户执行特定手势操作时由无障碍服务触发，辅助功能扩展可通过onAccessibilityEvent回调接收并处理对应的手势事件。 |
| [PageUpdateType](arkts-accessibility-pageupdatetype-t.md) | 页面更新类型。页面更新事件在页面内容或状态发生变化时由无障碍服务触发，辅助功能扩展可通过onAccessibilityEvent回调接收并处理对应的页面更新事件。 |
| [Rect](arkts-accessibility-rect-t.md) | 表示矩形区域，请参考[Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)。 |
| [TouchGuideType](arkts-accessibility-touchguidetype-t.md) | 触摸浏览事件类型。触摸浏览是无障碍辅助功能中的一种交互模式，用户在该模式下通过触摸探索界面元素而非直接激活。 |
| [WindowType](arkts-accessibility-windowtype-t.md) | 表示窗口的类型，请参考[WindowType](arkts-accessibility-windowtype-t.md)。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessibilityVirtualNode](arkts-accessibility-accessibilityvirtualnode-t-sys.md) | Indicates the accessibility virtual node. |
| [FocusCondition](arkts-accessibility-focuscondition-t-sys.md) | Indicates the condition of the search focus. |
| [FocusMoveResult](arkts-accessibility-focusmoveresult-t-sys.md) | Indicates focus move result. |
| [FocusRule](arkts-accessibility-focusrule-t-sys.md) | Indicates the rule of the search focus. |
| [Parameter](arkts-accessibility-parameter-t-sys.md) | Indicates executeAction parameter. |
| [TouchPosition](arkts-accessibility-touchposition-t-sys.md) | The touch position of an accessibility virtual node. |
<!--DelEnd-->

