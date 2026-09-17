# setSeniorModeStateForApp (System API)

## Modules to Import

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## setSeniorModeStateForApp

```TypeScript
function setSeniorModeStateForApp(appSeniorModeInfos: Array<AppSeniorModeInfo>): Promise<void>
```

Sets the senior mode state for an app. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appSeniorModeInfos | Array&lt;[AppSeniorModeInfo](arkts-accessibility-config-appseniormodeinfo-i-sys.md)&gt; | Yes | Senior mode state information of the app to modify. Each object in the array contains three properties: bundleName, appIndex, and seniorModeState. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed.<br>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed.<br>A non-system application calls a system API. |
| [9300000](../errorcode-accessibility.md#9300000-accessibility-system-service-abnormal) | System abnormality. |
| [9300008](../errorcode-accessibility.md#9300008-app-clone-index-invalid) | The appIndex is invalid. Possible causes:<br>1.The appIndex is out of the valid range. <br>2.The application corresponding to the appIndex does not exist. |

**Examples**

```TypeScript
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let infos: config.AppSeniorModeInfo[] = [{
  bundleName: 'com.example.myapplication',
  appIndex: 0,
  seniorModeState: true
}];

config.setSeniorModeStateForApp(infos).then(() => {
  console.info(`Succeeded in setting seniorModeState for App.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set seniorModeState for app. Code: ${err.code}, message: ${err.message}`);
});
```
