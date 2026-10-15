# getFocusedUIAccessibilityElement

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType, UIRect, UIAccessibilityElement } from '@kit.AccessibilityKit';
```

## getFocusedUIAccessibilityElement

```TypeScript
function getFocusedUIAccessibilityElement(): Promise<UIAccessibilityElement | undefined>
```

获取应用内的无障碍焦点元素。使用Promise异步回调。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accessibility-function getFocusedUIAccessibilityElement(): Promise<UIAccessibilityElement | undefined>--><!--Device-accessibility-function getFocusedUIAccessibilityElement(): Promise<UIAccessibilityElement | undefined>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[UIAccessibilityElement](arkts-accessibility-accessibility-uiaccessibilityelement-i.md) &#124; undefined&gt; | Promise对象。返回当前应用内的无障碍焦点元素；如果没有无障碍焦点，则返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9300000](../errorcode-accessibility.md#9300000-无障碍系统服务工作异常) | System abnormality. Possible causes:<br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). |
