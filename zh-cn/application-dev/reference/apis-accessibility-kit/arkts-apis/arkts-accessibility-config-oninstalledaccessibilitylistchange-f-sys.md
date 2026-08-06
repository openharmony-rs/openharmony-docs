# onInstalledAccessibilityListChange（系统接口）

## onInstalledAccessibilityListChange

```TypeScript
function onInstalledAccessibilityListChange(callback: Callback<void>): void
```

Register the listener that watches for changes in the installed status of accessibility extensions.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.READ_ACCESSIBILITY_CONFIG

<!--Device-config-function onInstalledAccessibilityListChange(callback: Callback<void>): void--><!--Device-config-function onInstalledAccessibilityListChange(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | Indicates the listener. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: () => void = this.eventCallback;
  eventCallback(): void {
    console.info(`installed accessibility list change`);
  }

  aboutToAppear(): void {
    config.onInstalledAccessibilityListChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

