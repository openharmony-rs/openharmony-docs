# requestPublishForm (System API)

## Modules to Import

```TypeScript
import { formProvider } from '@kit.FormKit';
```

<a id="requestpublishform1"></a>

## requestPublishForm

```TypeScript
function requestPublishForm(
    want: Want,
    formBindingData: formBindingData.FormBindingData,
    callback: AsyncCallback<string>
  ): void
```

Requests to publish a widget to the widget host (usually the home screen). This API uses an asynchronous callback to return the result.

**Since:** 9

<!--Device-formProvider-function requestPublishForm(    want: Want,    formBindingData: formBindingData.FormBindingData,    callback: AsyncCallback<string>  ): void--><!--Device-formProvider-function requestPublishForm(    want: Want,    formBindingData: formBindingData.FormBindingData,    callback: AsyncCallback<string>  ): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Publish request, which must contain the following fields:<br>Information about the target widget. <br>**abilityName**: ability of the target widget.<br>**parameters**:<br>'ohos.extra.param.key.form_dimension'<br>'ohos.extra.param.key.form_name'<br>'ohos.extra.param.key.module_name' |
| formBindingData | [formBindingData.FormBindingData](arkts-form-formbindingdata-formbindingdata-i.md) | Yes | Data used for creating the widget. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the widget ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
| [16501002](../errorcode-form.md#16501002-too-many-widgets) | The number of forms exceeds the maximum allowed.<br>**Applicable version:** 26.0.1 and later |
| [16501008](../errorcode-form.md#16501008-adding-a-widget-to-the-home-screen-times-out) | Waiting for the form addition to the desktop timed out.<br>**Applicable version:** 26.0.1 and later |
| [16501017](../errorcode-form.md#16501017-no-space-to-publish-the-widget) | There is no space to publish the form.<br>**Applicable version:** 26.0.1 and later |
| [16501018](../errorcode-form.md#16501018-widget-not-supported-for-publishing) | This form does not support publishing.<br>**Applicable version:** 26.0.1 and later |

<!--Del-->
**Examples**

```TypeScript
import { formBindingData, formProvider } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  abilityName: 'FormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  }
};
try {
  let param: Record<string, string> = {
    'temperature': '22c',
    'time': '22:00'
  }
  let obj: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
  formProvider.requestPublishForm(want, obj, (error: BusinessError, data: string) => {
    if (error) {
      console.error(`callback error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
      return;
    }
    console.info(`formProvider requestPublishForm, form ID is: ${data}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->


<a id="requestpublishform2"></a>

## requestPublishForm

```TypeScript
function requestPublishForm(want: Want, callback: AsyncCallback<string>): void
```

Requests to publish a widget to the widget host (usually the home screen). This API uses an asynchronous callback to return the result.

**Since:** 9

<!--Device-formProvider-function requestPublishForm(want: Want, callback: AsyncCallback<string>): void--><!--Device-formProvider-function requestPublishForm(want: Want, callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Publish request, which must contain the following fields:<br>Information about the target widget. <br>**abilityName**: ability of the target widget.<br>**parameters**:<br>'ohos.extra.param.key.form_dimension'<br>'ohos.extra.param.key.form_name'<br>'ohos.extra.param.key.module_name' |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the widget ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
| [16501002](../errorcode-form.md#16501002-too-many-widgets) | The number of forms exceeds the maximum allowed.<br>**Applicable version:** 26.0.1 and later |
| [16501008](../errorcode-form.md#16501008-adding-a-widget-to-the-home-screen-times-out) | Waiting for the form addition to the desktop timed out.<br>**Applicable version:** 26.0.1 and later |
| [16501017](../errorcode-form.md#16501017-no-space-to-publish-the-widget) | There is no space to publish the form.<br>**Applicable version:** 26.0.1 and later |
| [16501018](../errorcode-form.md#16501018-widget-not-supported-for-publishing) | This form does not support publishing.<br>**Applicable version:** 26.0.1 and later |

<!--Del-->
**Examples**

```TypeScript
import { formProvider } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  abilityName: 'FormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  }
};
try {
  formProvider.requestPublishForm(want, (error: BusinessError, data: string) => {
    if (error) {
      console.error(`callback error, code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`formProvider requestPublishForm, form ID is: ${data}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->


<a id="requestpublishform3"></a>

## requestPublishForm

```TypeScript
function requestPublishForm(want: Want, formBindingData?: formBindingData.FormBindingData): Promise<string>
```

Requests to publish a widget to the widget host (usually the home screen). This API uses a promise to return the result.

**Since:** 9

<!--Device-formProvider-function requestPublishForm(want: Want, formBindingData?: formBindingData.FormBindingData): Promise<string>--><!--Device-formProvider-function requestPublishForm(want: Want, formBindingData?: formBindingData.FormBindingData): Promise<string>-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Publish request, which must contain the following fields:<br>Information about the target widget. <br>**abilityName**: ability of the target widget.<br>**parameters**:<br>'ohos.extra.param.key.form_dimension'<br>'ohos.extra.param.key.form_name'<br>'ohos.extra.param.key.module_name' |
| formBindingData | [formBindingData.FormBindingData](arkts-form-formbindingdata-formbindingdata-i.md) | No | Data used for creating the widget. By default, no value is passed, indicating that no data is provided. |

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
| [16501008](../errorcode-form.md#16501008-adding-a-widget-to-the-home-screen-times-out) | Waiting for the form addition to the desktop timed out.<br>**Applicable version:** 26.0.1 and later |
| [16501017](../errorcode-form.md#16501017-no-space-to-publish-the-widget) | There is no space to publish the form.<br>**Applicable version:** 26.0.1 and later |
| [16501018](../errorcode-form.md#16501018-widget-not-supported-for-publishing) | This form does not support publishing.<br>**Applicable version:** 26.0.1 and later |

<!--Del-->
**Examples**

```TypeScript
import { formProvider } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  abilityName: 'FormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  }
};
try {
  formProvider.requestPublishForm(want).then((data: string) => {
    console.info(`formProvider requestPublishForm success, form ID is : ${data}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->
