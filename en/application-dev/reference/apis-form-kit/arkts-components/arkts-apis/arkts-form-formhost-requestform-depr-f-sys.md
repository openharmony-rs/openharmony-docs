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

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Widget ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the widget is updated, **error** is undefined; otherwise, **error** is an error object. |


## requestForm

```TypeScript
function requestForm(formId: string): Promise<void>
```

Requests a widget update. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [requestForm](arkts-form-formhost-requestform-f-sys.md)

**Required permissions:** ohos.permission.REQUIRE_FORM

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
