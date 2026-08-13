# offTouchGuideStateChange

## offTouchGuideStateChange

```TypeScript
function offTouchGuideStateChange(callback?: Callback<boolean>): void
```

Unregister the observe of the touchGuide state changed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-accessibility-function offTouchGuideStateChange(callback?: Callback<boolean>): void--><!--Device-accessibility-function offTouchGuideStateChange(callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 否 | Asynchronous callback interface. |

## 示例

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

  aboutToDisappear(): void {
    accessibility.offTouchGuideStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

