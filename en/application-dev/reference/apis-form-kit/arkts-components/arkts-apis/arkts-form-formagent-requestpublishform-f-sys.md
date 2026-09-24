# requestPublishForm (System API)

## Modules to Import

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## requestPublishForm

```TypeScript
function requestPublishForm(want: Want, callback: AsyncCallback<string>): void
```

Requests to publish a widget to the widget host. This API uses an asynchronous callback to return the result. The widget host is usually the home screen.

**Since:** 11

**Required permissions:** ohos.permission.AGENT_REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Publish request, which must contain the following fields:<br>**bundleName**: bundle name of the target widget. <br>**abilityName**: ability of the target widget. <br>parameters: <br>- **ohos.extra.param.key.form_dimension**: dimension of the target widget. <br>- **ohos.extra.param.key.form_name**: name of the target widget. <br>- **ohos.extra.param.key.module_name**: module name of the target widget. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the widget ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
| [16501002](../errorcode-form.md#16501002-too-many-widgets) | The number of forms exceeds the maximum allowed.<br>**Applicable version:** 26.0.1 and later |
| [16501008](../errorcode-form.md#16501008-adding-a-widget-to-the-home-screen-times-out) | Waiting for the form addition to the desktop timed out.<br>**Applicable version:** 12 and later |
| [16501017](../errorcode-form.md#16501017-no-space-to-publish-the-widget) | There is no space to publish the form.<br>**Applicable version:** 26.0.1 and later |
| [16501018](../errorcode-form.md#16501018-widget-not-supported-for-publishing) | This form does not support publishing.<br>**Applicable version:** 26.0.1 and later |


<a id="requestpublishform-1"></a>

## requestPublishForm

```TypeScript
function requestPublishForm(want: Want): Promise<string>
```

Requests to publish a widget to the widget host. This API uses a promise to return the result. The widget host is usually the home screen.

**Since:** 11

**Required permissions:** ohos.permission.AGENT_REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Publish request, which must contain the following fields:<br>**bundleName**: bundle name of the target widget. <br>**abilityName**: ability of the target widget. <br>parameters: <br>- **ohos.extra.param.key.form_dimension**: dimension of the target widget. <br>- **ohos.extra.param.key.form_name**: name of the target widget. <br>- **ohos.extra.param.key.module_name**: module name of the target widget. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the widget ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
| [16501002](../errorcode-form.md#16501002-too-many-widgets) | The number of forms exceeds the maximum allowed.<br>**Applicable version:** 26.0.1 and later |
| [16501008](../errorcode-form.md#16501008-adding-a-widget-to-the-home-screen-times-out) | Waiting for the form addition to the desktop timed out.<br>**Applicable version:** 12 and later |
| [16501017](../errorcode-form.md#16501017-no-space-to-publish-the-widget) | There is no space to publish the form.<br>**Applicable version:** 26.0.1 and later |
| [16501018](../errorcode-form.md#16501018-widget-not-supported-for-publishing) | This form does not support publishing.<br>**Applicable version:** 26.0.1 and later |
