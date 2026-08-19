# onTouchGuideStateChange

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
import { GesturePath } from '@kit.AccessibilityKit';
import { GesturePoint } from '@kit.AccessibilityKit';
```

## onTouchGuideStateChange

```TypeScript
function onTouchGuideStateChange(callback: Callback<boolean>): void
```

Register the observe of the touchGuide state changed.

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-accessibility-function onTouchGuideStateChange(callback: Callback<boolean>): void--><!--Device-accessibility-function onTouchGuideStateChange(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Vision

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | Asynchronous callback interface. |

**示例**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`touch guide state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onTouchGuideStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

