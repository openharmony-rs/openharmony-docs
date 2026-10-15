# onUIAccessibilityFocusChanged

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType, UIRect, UIAccessibilityElement } from '@kit.AccessibilityKit';
```

## onUIAccessibilityFocusChanged

```TypeScript
function onUIAccessibilityFocusChanged(callback: Callback<UIAccessibilityFocusChangeInfo>): void
```

监听应用内无障碍焦点变化事件。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accessibility-function onUIAccessibilityFocusChanged(callback: Callback<UIAccessibilityFocusChangeInfo>): void--><!--Device-accessibility-function onUIAccessibilityFocusChanged(callback: Callback<UIAccessibilityFocusChangeInfo>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UIAccessibilityFocusChangeInfo](arkts-accessibility-accessibility-uiaccessibilityfocuschangeinfo-i.md)&gt; | 是 | 回调函数。在应用内焦点变化时将焦点变化信息通过此函数进行通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9300000](../errorcode-accessibility.md#9300000-无障碍系统服务工作异常) | System abnormality. Possible causes:<br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). |
