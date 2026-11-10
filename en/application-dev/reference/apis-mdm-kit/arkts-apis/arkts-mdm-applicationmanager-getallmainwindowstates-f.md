# getAllMainWindowStates

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getAllMainWindowStates

```TypeScript
function getAllMainWindowStates(): Array<MainWindowStates>
```

Obtains the states of all main windows.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

<!--Device-applicationManager-function getAllMainWindowStates(): Array<MainWindowStates>--><!--Device-applicationManager-function getAllMainWindowStates(): Array<MainWindowStates>-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[MainWindowStates](arkts-mdm-applicationmanager-mainwindowstates-i.md)&gt; | Return the main window states. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
