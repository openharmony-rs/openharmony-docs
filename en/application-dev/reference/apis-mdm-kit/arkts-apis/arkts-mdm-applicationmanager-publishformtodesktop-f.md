# publishFormToDesktop

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## publishFormToDesktop

```TypeScript
function publishFormToDesktop(formInfo: FormInfo): string
```

Publishes the form to the desktop.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_REQUEST_PUBLISH_FORM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formInfo | [FormInfo](arkts-mdm-applicationmanager-forminfo-i.md) | Yes | formInfo indicates the information of the form. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the ID of form. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| 9201047 | Form count limit reached or insufficient home screen space to add forms. |
| 9201049 | The form does not exist. |
| 9201050 | The form type is not supported. |
| 9201051 | Failed to add the form to the desktop. |
