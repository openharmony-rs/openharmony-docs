# offSeniorModeStateChangeForApp (System API)

## Modules to Import

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## offSeniorModeStateChangeForApp

```TypeScript
function offSeniorModeStateChangeForApp(callback?: Callback<AppSeniorModeInfo>): void
```

Cancels the listener for senior mode state change events of all apps. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.READ_ACCESSIBILITY_CONFIG

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AppSeniorModeInfo](arkts-accessibility-config-appseniormodeinfo-i-sys.md)&gt; | No | Callback function used to cancel the event response of the specified callback object. The value must be the same as the value of **callback** in [config.onSeniorModeStateChangeForApp](arkts-accessibility-config-onseniormodestatechangeforapp-f-sys.md). If this parameter is not specified, all registered events will be unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.<br>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed.<br>A non-system application calls a system API. |

**Examples**

```TypeScript
import { config } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback = (data: config.AppSeniorModeInfo) => {
    console.info(`callback data, name: ${data.bundleName}, appIndex: ${data.appIndex}, seniorModeState: ${data.seniorModeState}`);
  }

  aboutToAppear(): void {
    config.onSeniorModeStateChangeForApp(this.callback);
  }

  aboutToDisappear(): void {
    config.offSeniorModeStateChangeForApp(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```
