# offTouchModeChange

## offTouchModeChange

```TypeScript
function offTouchModeChange(callback?: Callback<string>): void
```

Unregister the observe of the touch mode changed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-accessibility-function offTouchModeChange(callback?: Callback<string>): void--><!--Device-accessibility-function offTouchModeChange(callback?: Callback<string>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;string&gt; | 否 | callback Asynchronous callback interface. |

## 示例

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (mode: string) => void = this.eventCallback;
  eventCallback(mode: string): void {
    console.info(`touch mode change, result: ${JSON.stringify(mode)}`);
  }

  aboutToAppear(): void {
    accessibility.onTouchModeChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offTouchModeChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

