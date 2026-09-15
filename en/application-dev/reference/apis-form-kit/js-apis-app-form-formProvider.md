# @ohos.app.form.formProvider (formProvider)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=37d639b1fd701402e23a0dda5aa6090d613d1923 translatedAt=2026-09-15T01:53:02.220Z pushedAt=2026-09-15T08:28:34.685Z -->

The formProvider module provides capabilities such as obtaining widget information, updating widgets, and setting the widget refresh time. As a bridge between the widget provider and the widget management service, this module communicates with FormExtension through the IPC mechanism to update widgets and obtain information. It applies to scenarios where the widget provider needs to proactively update widget content, manage the widget lifecycle, and obtain the widget running status, helping you implement dynamic widget updates and status management.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { formProvider } from '@kit.FormKit';
```

## formProvider.setFormNextRefreshTime

setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback&lt;void&gt;): void

Sets the next refresh time of the specified widget. This API uses an asynchronous callback to return the result. It applies to scenarios where the widget refresh timing needs to be precisely controlled, such as scheduled tasks.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description                                  |
| ------ | ------ | ---- | ------------------------------------- |
| formId | string | Yes  | Widget ID.                              |
| minute | number | Yes | Interval after which the specified widget is refreshed. The value must be greater than or equal to 5, in minutes. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, error is undefined. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501002 | The number of forms exceeds the maximum allowed. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // formId of the widget. Use the actual form ID.
try {
  formProvider.setFormNextRefreshTime(formId, 5, (error: BusinessError) => {
    if (error) {
      console.error(`callback error, code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`formProvider setFormNextRefreshTime success`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.setFormNextRefreshTime

setFormNextRefreshTime(formId: string, minute: number): Promise&lt;void&gt;

Sets the next refresh time of the specified widget. This API uses a promise to return the result. It applies to scenarios where the widget refresh timing needs to be precisely controlled, such as scheduled tasks.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description                                  |
| ------ | ------ | ---- | ------------------------------------- |
| formId | string | Yes  | Widget ID.                              |
| minute | number | Yes | Time interval after which the specified widget is refreshed. Value range: greater than or equal to 5, in minutes. |

**Return value**

| Type         | Description                             |
| ------------- | ---------------------------------- |
| Promise\<void> | Promise that returns no value.     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501002 | The number of forms exceeds the maximum allowed. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // formId of the widget. Use the actual form ID.
try {
  formProvider.setFormNextRefreshTime(formId, 5).then(() => {
    console.info(`formProvider setFormNextRefreshTime success`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.updateForm

updateForm(formId: string, formBindingData: formBindingData.FormBindingData, callback: AsyncCallback&lt;void&gt;): void

Updates the specified widget. This API uses an asynchronous callback to return the result. It applies to scenarios where the widget content is proactively updated when widget data changes, such as weather data changes, stock price updates, and task progress updates.
> **NOTE**
>
> Since API version 20, if the widget update data is updated through shared memory, the total size of the update data must not exceed 10 MB, and the number of images to update must not exceed 20. In API version 19 and earlier, the maximum number of image files is 5, each limited to 2 MB of memory. Images exceeding the limit may be displayed abnormally.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type                                                                   | Mandatory| Description            |
| ------ | ---------------------------------------------------------------------- | ---- | ---------------- |
| formId | string                                                                 | Yes  | ID of the widget to update.|
| formBindingData | [formBindingData.FormBindingData](js-apis-app-form-formBindingData.md#formbindingdata) | Yes | Data used for the update. For details about the restrictions, see the description above. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the update result. If the operation is successful, error is undefined. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formBindingData, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // formId of the widget. Use the actual form ID.
try {
  let param: Record<string, string> = {
    'temperature': '22c',
    'time': '22:00'
  }
  let obj: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
  formProvider.updateForm(formId, obj, (error: BusinessError) => {
    if (error) {
      console.error(`callback error, code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`formProvider updateForm success`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.updateForm

updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise&lt;void&gt;

Updates the specified widget. This API uses a promise to return the result. It applies to scenarios where the widget content is proactively updated when widget data changes, such as weather data changes, stock price updates, and task progress updates.
> **NOTE**
>
> Since API version 20, if the widget update data is updated through shared memory, the total size of the update data must not exceed 10 MB, and the number of images to update must not exceed 20. In API version 19 and earlier, the maximum number of image files is 5, each limited to 2 MB of memory. Images exceeding the limit may be displayed abnormally.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type                                                                   | Mandatory| Description            |
| ------ | ---------------------------------------------------------------------- | ---- | ---------------- |
| formId | string                                                                 | Yes  | ID of the widget to update.|
| formBindingData | [formBindingData.FormBindingData](js-apis-app-form-formBindingData.md#formbindingdata) | Yes | Data used for the update. For details about the restrictions, see the description above. |

**Return value**

| Type          | Description                               |
| -------------- | ----------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formBindingData, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // formId of the widget. Use the actual form ID.
let param: Record<string, string> = {
  'temperature': '22c',
  'time': '22:00'
}
let obj: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
try {
  formProvider.updateForm(formId, obj).then(() => {
    console.info(`formProvider updateForm success`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.getFormsInfo

getFormsInfo(callback: AsyncCallback&lt;Array&lt;formInfo.FormInfo&gt;&gt;): void

Obtains the widget information of the current application on the device. This API uses an asynchronous callback to return the result. It applies to scenarios such as widget management, debugging, and statistics, for example, viewing the configuration information of all widgets of an application and counting the number of widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description   |
| ------ | ------ | ---- | ------- |
| callback | AsyncCallback&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-app-formInfo.md#forminfo)&gt;&gt; | Yes | Callback used to return the obtained widget information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formProvider.getFormsInfo((error, data) => {
    if (error) {
      console.error(`callback error, code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`formProvider getFormsInfo, data: ${JSON.stringify(data)}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
## formProvider.getFormsInfo

getFormsInfo(filter: formInfo.FormInfoFilter, callback: AsyncCallback&lt;Array&lt;formInfo.FormInfo&gt;&gt;): void

Obtains the application's widget information that meets a filter criterion on the device. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description   |
| ------ | ------ | ---- | ------- |
| filter | [formInfo.FormInfoFilter](js-apis-app-form-formInfo.md#forminfofilter) | Yes| Filter criterion.|
| callback | AsyncCallback&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md)&gt;&gt; | Yes| Callback used to return the information obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

const filter: formInfo.FormInfoFilter = {
  // Obtain widget information of the specified module.
  moduleName: 'entry'
};
try {
  formProvider.getFormsInfo(filter, (error, data) => {
    if (error) {
      console.error(`callback error, code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`formProvider getFormsInfo, data: ${JSON.stringify(data)}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.getFormsInfo

getFormsInfo(filter?: formInfo.FormInfoFilter): Promise&lt;Array&lt;formInfo.FormInfo&gt;&gt;

Obtains information about widgets that meet the criteria of the current application. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description   |
| ------ | ------ | ---- | ------- |
| filter | [formInfo.FormInfoFilter](js-apis-app-form-formInfo.md#forminfofilter) | No | Filter used to filter widget information that meets specified conditions. Pass this parameter to filter widgets of a specific module or a specific name. You can omit this parameter to obtain all widget information. If this parameter is not passed, it is empty by default and all widget information is returned. |

**Return value**

| Type         | Description                               |
| :------------ | :---------------------------------- |
| Promise&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md)&gt;&gt; | Promise used to return the information obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

const filter: formInfo.FormInfoFilter = {
  // Obtain widget information of the specified module.
  moduleName: 'entry'
};
try {
  formProvider.getFormsInfo(filter).then((data: formInfo.FormInfo[]) => {
    console.info(`formProvider getFormsInfo, data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.openFormEditAbility<sup>18+</sup>

openFormEditAbility(abilityName: string, formId: string, isMainPage?: boolean): void

Opens the widget editing page. It applies to scenarios where users need to configure widget parameters, for example, setting the widget display content, selecting a data source, and configuring the update frequency.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description                                                |
| ------ | ------ |----|----------------------------------------------------|
| abilityName | string | Yes | Ability name on the editing page.                                    |
| formId | string | Yes | Widget ID.                                             |
| isMainPage | boolean | No  | Whether this is the main editing page.<br>-&nbsp;true: indicates that this is the main editing page, suitable for configuring the basic information of a widget for the first time.<br>-&nbsp;false: indicates that this is not the main editing page, suitable for adjusting widget details or performing advanced configuration.<br>Default value: true (the default value is usually sufficient when editing a widget for the first time). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID   | Error Message|
|----------| -------- |
| 801      | Capability not supported. Function openFormEditAbility cannot work correctly due to limited device capabilities. |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |
| 16501003 | The form cannot be operated by the current application. |
| 16501007 | Form is not trust. |

**Example**

```ts
import { formProvider } from '@kit.FormKit';

const TAG: string = 'FormEditDemo-Page] -->';

@Entry
@Component
struct Page {
  @State message: string = 'Hello World';

  aboutToAppear(): void {
    console.info(`${TAG} aboutToAppear.....`);
  }

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('PageHelloWorld')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Top },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          console.info(`${TAG} onClick.....`);
          formProvider.openFormEditAbility('ability://EntryFormEditAbility', '1386529921');
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## formProvider.closeFormEditAbility<sup>23+</sup>

closeFormEditAbility(isMainPage?: boolean): void

Closes the widget editing page. It applies to scenarios where widget editing is completed or canceled, for example, closing the editing page after the user completes parameter configuration or canceling the editing operation.

**System capability**: SystemCapability.Ability.Form

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type   | Mandatory| Description                                                |
| ------ | ------ |----|----------------------------------------------------|
| isMainPage | boolean | No  | Whether to close the main editing page.<br>-&nbsp;true: closes the main editing page, suitable for the scenario where the main editing page is closed after configuration is complete.<br>-&nbsp;false: closes a non-main editing page, suitable for the scenario where the current non-main editing page is closed in a multi-level editing page scenario.<br>Default value: true (the default value is usually used when closing the current editing page). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID   | Error Message|
|----------| -------- |
| 801      | Capability not supported due to limited device capabilities. |
| 16500050 | IPC connection error. |
| 16501015 | Cannot close the widget editing page opened by other apps. |

**Example**

```ts
import { formProvider } from '@kit.FormKit';

const TAG: string = 'FormEditDemo-Page] -->';

@Entry
@Component
struct Page {
  @State message: string = 'Hello World';

  aboutToAppear(): void {
    console.info(`${TAG} aboutToAppear.....`);
  }

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('PageHelloWorld')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Top },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          console.info(`${TAG} onClick.....`);
          try {
            formProvider.closeFormEditAbility();
            console.info(`${TAG} close FormEditAbility success.`);
          } catch (error) {
            console.error(`${TAG} close FormEditAbility failed, code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## formProvider.openFormManager<sup>18+</sup>

openFormManager(want: Want): void

Opens the widget management page of the current application. It applies to widget management scenarios, for example, previewing all widgets of the current application that can be added to the home screen, and adding widgets to the Assistant·TODAY screen or the home screen.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Ability.Form

**Device behavior difference:** When this API is called on a wearable, error code [16501000](./errorcode-form.md#16501000-internal-function-error) is returned.

**Parameters**

| Name | Type   | Mandatory| Description                                                                                                                                                                                                                                                                                                     |
|------| ------ | ---- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| want     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | Parameter that must contain the following fields:<br>**bundleName**: bundle name of widget.<br>**abilityName**: ability name of the widget.<br>**parameters**:<br>- **ohos.extra.param.key.form_dimension**: [Widget dimension](js-apis-app-form-formInfo.md#formdimension).<br>- **ohos.extra.param.key.form_name**: Widget name.<br>- **ohos.extra.param.key.module_name**: module name of the widget.|
> **NOTE**
>
> If the parameter is not set or the specified widget does not exist, the default widget configured in [form_config.json](../../form/arkts-ui-widget-configuration.md#widget-configuration) is displayed by default.

**Error codes**

For details about the error codes, see [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';

const want: Want = {
  bundleName: 'com.example.formbutton',
  abilityName: 'EntryFormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  },
};
try {
  formProvider.openFormManager(want);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.getPublishedFormInfoById<sup>(deprecated)</sup>

getPublishedFormInfoById(formId: string): Promise&lt;formInfo.FormInfo&gt;

Obtains the information of the specified widget that has been added to the home screen by the current application on the device. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 18.

> **NOTE**
>
> This API is supported since API version 18 and deprecated since API version 20. You are advised to use [getPublishedRunningFormInfoById](#formprovidergetpublishedrunningforminfobyid20) instead.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description   |
| ------ | ------ |----| ------- |
| formId | string | Yes| Widget ID.|

**Return value**

| Type                                                               | Description                               |
|-------------------------------------------------------------------| ---------------------------------- |
| Promise&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md#forminfo)&gt; | Promise used to return the information obtained.|

**Error codes**

For details about the error codes, see [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

const formId: string = '388344236';
try {
  formProvider.getPublishedFormInfoById(formId).then((data: formInfo.FormInfo) => {
    console.info(`formProvider getPublishedFormInfoById, data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.getPublishedFormInfos<sup>(deprecated)</sup>

getPublishedFormInfos(): Promise&lt;Array&lt;formInfo.FormInfo&gt;&gt;

Obtains the information of all widgets that have been added to the home screen by the current application on the device. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 18.

> **NOTE**
>
> This API is supported since API version 18 and deprecated since API version 20. You are advised to use [getPublishedRunningFormInfos](#formprovidergetpublishedrunningforminfos20) instead.

**System capability**: SystemCapability.Ability.Form

**Return value**

| Type         | Description                               |
| ------------ | ---------------------------------- |
| Promise&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md)&gt;&gt; | Promise used to return the information obtained.|

**Error codes**

For details about the error codes, see [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formProvider.getPublishedFormInfos().then((data: formInfo.FormInfo[]) => {
    console.info(`formProvider getPublishedFormInfos, data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.requestOverflow<sup>20+</sup>

requestOverflow(formId: string, overflowInfo: formInfo.OverflowInfo): Promise&lt;void&gt;

Requests a scene-based widget animation effect by the widget provider. This API takes effect only for [scene-based widgets](../../form/arkts-ui-widget-configuration.md#sceneanimationparams-field). This API uses a promise to return the result.

**Related APIs:**
- [cancelOverflow()](#formprovidercanceloverflow20): Cancels the scene-based widget animation request to cancel an animation that has been initiated.

> **NOTE**
>
> 1. This API cannot be used in power saving mode. If it is used, error code 16501000 is reported.
> 2. When the device thermal level enters the HOT state and no click event occurs, this API reports error code 16501000. When the thermal level enters OVERHEATED, error code 16501000 is reported in any case. For details about the thermal level, see [ThermalLevel](../../reference/apis-basic-services-kit/js-apis-thermal.md#thermallevel).

**Atomic service API**: This API can be used in atomic services since API version 20.

**Device behavior differences:** This API is supported on certain phone models. On unsupported devices, it returns error code [801](../errorcode-universal.md#801-api-not-supported).

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type                                                                | Mandatory| Description       |
| ------ |--------------------------------------------------------------------| ---- |-----------|
| formId | string                                                             | Yes | Widget ID. |
| overflowInfo | [formInfo.OverflowInfo](js-apis-app-form-formInfo.md#overflowinfo20) | Yes| Animation request parameter information.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 801 |   Capability not supported. Function requestOverflow can not work correctly due to limited device capabilities. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |
| 16501011 | The form cannot support this operation. |

**Example**

```ts
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // formId of the widget. Use the actual form ID.
let overflowInfo: formInfo.OverflowInfo = {
  area: {
    left: -10,
    top: -10,
    width: 180,
    height: 180
  },
  duration: 1000,
  useDefaultAnimation: false,
};

try {
  formProvider.requestOverflow(formId, overflowInfo).then(() => {
    console.info('requestOverflow succeed.');
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.cancelOverflow<sup>20+</sup>

cancelOverflow(formId: string): Promise&lt;void&gt;

Cancels an animation. This API takes effect only for [scene-based widgets](../../form/arkts-ui-widget-configuration.md#sceneanimationparams-field). This API uses a promise to return the result.

> **NOTE**
>
> 1. This API cannot be used in power saving mode. If it is used, error code 16501000 is reported.
> 2. When the device thermal level enters the HOT state and no click event occurs, this API reports error code 16501000. When the thermal level enters OVERHEATED, error code 16501000 is reported in any case. For details about the thermal level, see [ThermalLevel](../../reference/apis-basic-services-kit/js-apis-thermal.md#thermallevel).

**Atomic service API**: This API can be used in atomic services since API version 20.

**Device behavior differences:** This API is supported on certain phone models. On unsupported devices, it returns error code [801](../errorcode-universal.md#801-api-not-supported).

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description   |
| ------ | ------ | ---- |-------|
| formId | string | Yes | Widget ID. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 801 | Capability not supported. Function cancelOverflow can not work correctly due to limited device capabilities. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |
| 16501011 | The form cannot support this operation. |

**Example**

```ts
import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // formId of the widget. Use the actual form ID.

try {
  formProvider.cancelOverflow(formId).then(() => {
    console.info('cancelOverflow succeed.');
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.getFormRect<sup>20+</sup>

getFormRect(formId: string): Promise&lt;formInfo.Rect&gt;

Queries the position and dimensions of a widget. This API uses a promise to return the result. It applies to scenarios where the position and dimensions of a widget on the screen are required, such as widget animation effects, position calibration, and layout calculation.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type        | Mandatory| Description       |
| ------ |-------------| ---- |-----------|
| formId | string      | Yes | Widget ID. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[formInfo.Rect](js-apis-app-form-formInfo.md#rect20)&gt; | Promise used to return the position and dimension of the widget relative to the upper-left corner of the screen, in vp.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 801 |   Capability not supported. Function getFormRect cannot work correctly due to limited device capabilities. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // formId of the widget. Use the actual form ID.

try {
  formProvider.getFormRect(formId).then((data: formInfo.Rect) => {
    console.info(`getFormRect succeed, data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.getPublishedRunningFormInfoById<sup>20+</sup>

getPublishedRunningFormInfoById(formId: string): Promise&lt;formInfo.RunningFormInfo&gt;

Obtains the information of the specified widget added to the home screen of the current application. This API uses a promise to return the result. It is applicable to scenarios such as widget management and debugging, for example, viewing the position and dimension information of a specified widget.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description   |
| ------ | ------ |----| ------- |
| formId | string | Yes| Widget ID.|

**Return value**

| Type                                                               | Description                               |
|-------------------------------------------------------------------| ---------------------------------- |
| Promise&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo.md#runningforminfo20)&gt; | Promise used to return the information about the widgets that meet the requirements, including the widget name and dimension.|

**Error codes**

For details about the error codes, see [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |
| 16501001  | The ID of the form to be operated does not exist. |
| 16501003  | The form cannot be operated by the current application. |

**Example**

```ts
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

const formId: string = '388344236';

try {
  formProvider.getPublishedRunningFormInfoById(formId).then((data: formInfo.RunningFormInfo) => {
    console.info(`formProvider getPublishedRunningFormInfoById, data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.getPublishedRunningFormInfos<sup>20+</sup>

getPublishedRunningFormInfos(): Promise&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt;

Obtains the information of all widgets added to the home screen. This API uses a promise to return the result. It is applicable to scenarios such as widget management, batch operations, and statistics, for example, viewing the information of all widgets added to the home screen of the application and updating the widget status in batches.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Ability.Form

**Return value**

| Type         | Description                               |
| ------------ | ---------------------------------- |
| Promise&lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo.md#runningforminfo20)&gt;&gt; | Promise used to return the information about widgets that meet the requirements.|

**Error codes**

For details about the error codes, see [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formProvider.getPublishedRunningFormInfos().then((data: formInfo.RunningFormInfo[]) => {
    console.info(`formProvider getPublishedRunningFormInfos, data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.reloadForms<sup>22+</sup>

reloadForms(context: UIAbilityContext, moduleName: string, abilityName: string, formName: string): Promise&lt;number&gt;

For widgets with the same moduleName, abilityName, and formName in the current application, a different widget ID is assigned each time the widget is added to the home screen. The widget provider can use this API to update these widgets in batches. Compared with reloadAllForms, this API can precisely specify the widgets with a specific configuration to update, and is suitable for scenarios where only specific widgets need to be updated. reloadAllForms updates all widgets added to the home screen of the current application, and is suitable for global update scenarios. This API is called in the main process of the application to notify the FormExtension process to perform batch updates. It can be used only in [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md), and uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------  |
| context | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes | Context of [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md), used to verify the application identity. |
| moduleName | string | Yes | Module name of the specified widget, which must be consistent with the module name configured in [form_config.json](../../form/arkts-ui-widget-configuration.md#fields-in-configuration-file). It must be used together with abilityName and formName; all three must match to locate the corresponding widget. |
| abilityName | string | Yes | Ability name of the specified widget, which must be consistent with the ability name configured in [form_config.json](../../form/arkts-ui-widget-configuration.md#fields-in-configuration-file). |
| formName | string | Yes| Name of the widget configured in [form_config.json](../../form/arkts-ui-widget-configuration.md#fields-in-configuration-file).|

**Return value**

| Type         | Description                               |
| ------------ | ---------------------------------- |
| Promise&lt;number&gt; | Promise used to return the number of widgets requested for update.|

**Error codes**

For details about the error codes, see [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { formProvider } from '@kit.FormKit';

try {
  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  // Replace the information with the actual widget information to be updated.
  let moduleName: string = 'entry';
  let abilityName: string = 'EntryFormAbility';
  let formName: string = 'formName';
  formProvider.reloadForms(context, moduleName, abilityName, formName).then((reloadNum: number) => {
    console.info(`reloadForms success, reload number: ${reloadNum}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formProvider.reloadAllForms<sup>22+</sup>

reloadAllForms(context: UIAbilityContext): Promise&lt;number&gt;

Notifies the FormExtension process, in the current application's main process, to batch update all widgets of the application that have been added to the home screen. It can be called only in [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md), and uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Ability.Form

**Parameters**

| Name| Type   | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------  |
| context | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes   | Context of [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md), used to verify the application identity.     |

**Return value**

| Type         | Description                               |
| ------------ | ---------------------------------- |
| Promise&lt;number&gt; | Promise used to return the number of widgets requested for update.|

**Error codes**

For details about the error codes, see [Widget Error Codes](errorcode-form.md).

| Error Code ID| Error Message|
| -------- | -------- |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { formProvider } from '@kit.FormKit';

try {
  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  formProvider.reloadAllForms(context).then((reloadNum: number) => {
    console.info(`reloadAllForms success, reload number: ${reloadNum}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```