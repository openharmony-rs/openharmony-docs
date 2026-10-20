# requestForm (System API)

## Modules to Import

```TypeScript
```

## requestForm

```TypeScript
function requestForm(formId: string, callback: AsyncCallback<void>): void
```

Requests a widget update. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [requestForm](arkts-form-formhost-requestform-f-sys.md)

**Required permissions:** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function requestForm(formId: string, callback: AsyncCallback<void>): void--><!--Device-formHost-function requestForm(formId: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Widget ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the widget is updated, **error** is undefined; otherwise, **error** is an error object. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let formId: string = '12400633174999288';
formHost.requestForm(formId, (error: Base.BusinessError) => {
  if (error.code) {
    console.error(`formHost requestForm, error: ${JSON.stringify(error)}`);
  }
});
```

<!--DelEnd-->


## requestForm

```TypeScript
function requestForm(formId: string): Promise<void>
```

Requests a widget update. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [requestForm](arkts-form-formhost-requestform-f-sys.md)

**Required permissions:** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function requestForm(formId: string): Promise<void>--><!--Device-formHost-function requestForm(formId: string): Promise<void>-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Widget ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let formId: string = '12400633174999288';
formHost.requestForm(formId).then(() => {
  console.info('formHost requestForm success');
}).catch((error: Base.BusinessError) => {
  console.error(`formHost requestForm, error: ${JSON.stringify(error)}`);
});
```

<!--DelEnd-->
