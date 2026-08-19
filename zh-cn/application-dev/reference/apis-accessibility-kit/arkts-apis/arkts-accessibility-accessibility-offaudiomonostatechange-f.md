# offAudioMonoStateChange

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
import { GesturePath } from '@kit.AccessibilityKit';
import { GesturePoint } from '@kit.AccessibilityKit';
```

## offAudioMonoStateChange

```TypeScript
function offAudioMonoStateChange(callback?: Callback<boolean>): void
```

取消监听单声道音频模式变化事件。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accessibility-function offAudioMonoStateChange(callback?: Callback<boolean>): void--><!--Device-accessibility-function offAudioMonoStateChange(callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 否 | 回调函数。取消指定callback对象的事件响应。需与 [accessibility.onAudioMonoStateChange](arkts-accessibility-accessibility-onaudiomonostatechange-f.md)的callback一致。缺省时，表示注销所有已注册事件。 |

**示例**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe audioMono state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAudioMonoStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offAudioMonoStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

