# offEnabledAccessibilityExtensionListChange（系统接口）

## offEnabledAccessibilityExtensionListChange

```TypeScript
function offEnabledAccessibilityExtensionListChange(callback?: Callback<void>): void
```

Unregister listener that watches for changes in the enabled status of accessibility extensions.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_ACCESSIBILITY_CONFIG

<!--Device-config-function offEnabledAccessibilityExtensionListChange(callback?: Callback<void>): void--><!--Device-config-function offEnabledAccessibilityExtensionListChange(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | Indicates the listener. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: () => void = this.eventCallback;
  eventCallback(): void {
    console.info(`enabled accessibility extension list change`);
  }

  aboutToAppear(): void {
    config.onEnabledAccessibilityExtensionListChange(this.callback);
  }

  aboutToDisappear(): void {
    config.offEnabledAccessibilityExtensionListChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

