# @ohos.application.AccessibilityExtensionAbility(辅助功能扩展能力)

AccessibilityExtensionAbility基于ExtensionAbility框架，提供辅助功能扩展业务的能力。


## 导入模块

```TypeScript
import { AccessibilityExtensionAbility, AccessibilityElement, AccessibilityExtensionContext, ElementAttributeKeys, ElementAttributeValues, FocusDirection, FocusType, Rect, WindowType, AccessibilityEvent, AccessibilityEventInfo, Parameter, FocusRule, FocusCondition, FocusMoveResult, AccessibilityVirtualNode, TouchPosition } from '@kit.AccessibilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AccessibilityExtensionAbility(辅助功能扩展能力)](arkts-accessibility-application-accessibilityextensionability-accessibilityextensionability-c.md) | AccessibilityExtensionAbility基于ExtensionAbility框架，提供无障碍扩展业务的能力，包括连接无障碍服务、断开无障碍服务、处理无障碍事件和处理无障碍按键事件等。  **生命周期流程：** onAccessibilityConnect（连接回调，用于初始化）→ onAccessibilityEventInfo/onAccessibilityKeyEvent（处理无障碍事件和按键事件）→ onAccessibilityDisconnect（断开回调，用于资源回收）。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessibilityExtensionAbility(辅助功能扩展能力)](arkts-accessibility-application-accessibilityextensionability-accessibilityextensionability-c-sys.md) | AccessibilityExtensionAbility基于ExtensionAbility框架，提供无障碍扩展业务的能力，包括连接无障碍服务、断开无障碍服务、处理无障碍事件和处理无障碍按键事件等。  **生命周期流程：** onAccessibilityConnect（连接回调，用于初始化）→ onAccessibilityEventInfo/onAccessibilityKeyEvent（处理无障碍事件和按键事件）→ onAccessibilityDisconnect（断开回调，用于资源回收）。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AccessibilityEvent(辅助功能扩展能力)](arkts-accessibility-application-accessibilityextensionability-accessibilityevent-i.md) | 无障碍事件信息。无障碍事件由系统无障碍服务在用户操作或界面变化时生成，通过eventType标识事件类别（包括无障碍事件类型、窗口变化类型、触摸浏览事件类型、手势事件类型、页面更新类型），辅助功能扩展可通过 onAccessibilityEvent回调接收并处理这些事件。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessibilityEventInfo(辅助功能扩展能力)](arkts-accessibility-application-accessibilityextensionability-accessibilityeventinfo-i-sys.md) | 无障碍事件信息。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AccessibilityElement(辅助功能扩展能力)](arkts-accessibility-accessibilityelement-t.md) | 表示无障碍节点元素，请参考[AccessibilityElement](arkts-accessibility-accessibilityextensioncontext-accessibilityelement-i.md)。 |
| [AccessibilityExtensionContext(辅助功能扩展能力)](arkts-accessibility-accessibilityextensioncontext-t.md) | 表示辅助功能扩展的上下文环境，请参考 [AccessibilityExtensionContext](arkts-accessibility-accessibilityextensioncontext-c.md)。 |
| [ElementAttributeKeys(辅助功能扩展能力)](arkts-accessibility-elementattributekeys-t.md) | 表示[ElementAttributeValues](arkts-accessibility-accessibilityextensioncontext-elementattributevalues-i.md)的属性名称。 |
| [ElementAttributeValues(辅助功能扩展能力)](arkts-accessibility-elementattributevalues-t.md) | 表示节点元素具备的属性名称及属性值类型信息，请参考 [ElementAttributeValues](arkts-accessibility-accessibilityextensioncontext-elementattributevalues-i.md)。 |
| [FocusDirection(辅助功能扩展能力)](arkts-accessibility-focusdirection-t.md) | 表示查询下一焦点元素的方向，请参考[FocusDirection](arkts-accessibility-focusdirection-t.md)。 |
| [FocusType(辅助功能扩展能力)](arkts-accessibility-focustype-t.md) | 表示查询焦点元素的类型，请参考[FocusType](arkts-accessibility-focustype-t.md)。 |
| [GestureType(辅助功能扩展能力)](arkts-accessibility-gesturetype-t.md) | 手势事件类型。手势事件在用户执行特定手势操作时由无障碍服务触发，辅助功能扩展可通过onAccessibilityEvent回调接收并处理对应的手势事件。 |
| [PageUpdateType(辅助功能扩展能力)](arkts-accessibility-pageupdatetype-t.md) | 页面更新类型。页面更新事件在页面内容或状态发生变化时由无障碍服务触发，辅助功能扩展可通过onAccessibilityEvent回调接收并处理对应的页面更新事件。 |
| [Rect(辅助功能扩展能力)](arkts-accessibility-rect-t.md) | 表示矩形区域，请参考[Rect](arkts-accessibility-accessibilityextensioncontext-rect-i.md)。 |
| [TouchGuideType(辅助功能扩展能力)](arkts-accessibility-touchguidetype-t.md) | 触摸浏览事件类型。触摸浏览是无障碍辅助功能中的一种交互模式，用户在该模式下通过触摸探索界面元素而非直接激活。 |
| [WindowType(辅助功能扩展能力)](arkts-accessibility-windowtype-t.md) | 表示窗口的类型，请参考[WindowType](arkts-accessibility-windowtype-t.md)。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AccessibilityVirtualNode(辅助功能扩展能力)](arkts-accessibility-accessibilityvirtualnode-t-sys.md) | 无障碍虚拟节点，请参考[AccessibilityVirtualNode](arkts-accessibility-accessibilityextensioncontext-accessibilityvirtualnode-i-sys.md)。 |
| [FocusCondition(辅助功能扩展能力)](arkts-accessibility-focuscondition-t-sys.md) | 表示查询可聚焦节点方式，请参考[FocusCondition](arkts-accessibility-focuscondition-t-sys.md)。 |
| [FocusMoveResult(辅助功能扩展能力)](arkts-accessibility-focusmoveresult-t-sys.md) | 查询无障碍节点返回值类型，请参考[FocusMoveResult](arkts-accessibility-accessibilityextensioncontext-focusmoveresult-i-sys.md)。 |
| [FocusRule(辅助功能扩展能力)](arkts-accessibility-focusrule-t-sys.md) | 表示查找可聚焦节点时，如何判断起始节点及其子节点的聚焦能力，请参考[FocusRule](arkts-accessibility-focusrule-t-sys.md)。 |
| [Parameter(辅助功能扩展能力)](arkts-accessibility-parameter-t-sys.md) | 无障碍节点元素执行特定操作时，为操作提供具体设置的参数值，请参考[Parameter](arkts-accessibility-accessibilityextensioncontext-parameter-c-sys.md)。 |
| [TouchPosition(辅助功能扩展能力)](arkts-accessibility-touchposition-t-sys.md) | 触摸点击位置，请参考[TouchPosition](arkts-accessibility-accessibilityextensioncontext-touchposition-i-sys.md)。 |
<!--DelEnd-->
