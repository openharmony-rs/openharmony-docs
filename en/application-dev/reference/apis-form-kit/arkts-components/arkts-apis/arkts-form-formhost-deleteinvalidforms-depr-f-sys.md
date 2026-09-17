# deleteInvalidForms (System API)

## Modules to Import

```TypeScript
```

## deleteInvalidForms

```TypeScript
function deleteInvalidForms(formIds: Array<string>, callback: AsyncCallback<number>): void
```

Deletes invalid widgets from the list. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-f-sys.md)

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | List of valid widget IDs. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the invalid widgets are deleted, **error** is undefined and **data** is the number of widgets deleted; otherwise, **error** is an error object. |


## deleteInvalidForms

```TypeScript
function deleteInvalidForms(formIds: Array<string>): Promise<number>
```

Deletes invalid widgets from the list. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-f-sys.md)

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | List of valid widget IDs. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of widgets deleted. |
