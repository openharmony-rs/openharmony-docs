# isFlashReminderEnabledSync

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
import { GesturePath } from '@kit.AccessibilityKit';
import { GesturePoint } from '@kit.AccessibilityKit';
```

## isFlashReminderEnabledSync

```TypeScript
function isFlashReminderEnabledSync(): boolean
```

查询闪烁提醒模式是否开启。 本接口为同步版本，与[accessibility.isFlashReminderEnabled](arkts-accessibility-accessibility-isflashreminderenabled-f.md)（异步版本）功能相同，如需立即获取结果可使用本 接口，如需在非阻塞场景下查询建议使用异步版本。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-accessibility-function isFlashReminderEnabledSync(): boolean--><!--Device-accessibility-function isFlashReminderEnabledSync(): boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否开启闪烁提醒模式。true表示开启闪烁提醒模式，false表示未开启闪烁提醒模式。 |

**示例**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let status: boolean = accessibility.isFlashReminderEnabledSync();
    console.info(`status: ${JSON.stringify(status)}`);
  }

  build() {
    Column() {
    }
  }
}
```

