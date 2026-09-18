# requestPublishFormCrossDevice (System API)

## Modules to Import

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## requestPublishFormCrossDevice

```TypeScript
function requestPublishFormCrossDevice(peerServiceInfo: formInfo.PeerFormHostServiceInfo, want: Want,
    formBindingData?: formBindingData.FormBindingData): Promise<formInfo.PublishFormCrossDeviceResult>
```

Requests to publish a form to the form host service of the remote device.

**Since:** 26.1.0

**Required permissions:** ohos.permission.AGENT_REQUIRE_FORM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| peerServiceInfo | [formInfo.PeerFormHostServiceInfo](arkts-form-forminfo-peerformhostserviceinfo-i-sys.md) | Yes | The peer form host service information. |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Publish request, which must contain the following fields:<br>**bundleName**: bundle name of the target form. <br>**abilityName**: ability of the target form. <br>parameters: <br>- **ohos.extra.param.key.form_dimension**: dimension of the target form. <br>- **ohos.extra.param.key.form_name**: name of the target form. <br>- **ohos.extra.param.key.module_name**: module name of the target form. |
| formBindingData | [formBindingData.FormBindingData](arkts-form-formbindingdata-formbindingdata-i.md) | No | Data to be used for the update. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[formInfo.PublishFormCrossDeviceResult](arkts-form-forminfo-publishformcrossdeviceresult-i-sys.md)&gt; | Promise used to return the result of publishing the form across device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16501020](../errorcode-form.md#16501020-remote-widget-service-unavailable) | Remote form service is unavailable. |
| [16501021](../errorcode-form.md#16501021-remote-widget-application-not-installed-or-version-too-low) | The peer form application is not installed or the version is too old. |
| [16501002](../errorcode-form.md#16501002-too-many-widgets) | The number of forms exceeds the maximum allowed. |
| [16501017](../errorcode-form.md#16501017-no-space-to-publish-the-widget) | There is no space to publish the form. |
| [16501018](../errorcode-form.md#16501018-widget-not-supported-for-publishing) | This form does not support publishing. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
| [16501008](../errorcode-form.md#16501008-adding-a-widget-to-the-home-screen-times-out) | Waiting for the form addition to the desktop timed out. |
