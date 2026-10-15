# deleteInvalidForms (System API)

## Modules to Import

```TypeScript
```

<a id="deleteinvalidforms1"></a>

## deleteInvalidForms

```TypeScript
function deleteInvalidForms(formIds: Array<string>, callback: AsyncCallback<number>): void
```

Deletes invalid widgets from the list. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-f-sys.md)

**Required permissions:** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function deleteInvalidForms(formIds: Array<string>, callback: AsyncCallback<number>): void--><!--Device-formHost-function deleteInvalidForms(formIds: Array<string>, callback: AsyncCallback<number>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | List of valid widget IDs. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the invalid widgets are deleted, **error** is undefined and **data** is the number of widgets deleted; otherwise, **error** is an error object. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
formHost.deleteInvalidForms(formIds, (error: Base.BusinessError, data: number) => {
  if (error.code) {
    console.error(`formHost deleteInvalidForms, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`formHost deleteInvalidForms, data: ${JSON.stringify(data)}`);
  }
});
```

<!--DelEnd-->


<a id="deleteinvalidforms2"></a>

## deleteInvalidForms

```TypeScript
function deleteInvalidForms(formIds: Array<string>): Promise<number>
```

Deletes invalid widgets from the list. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-f-sys.md)

**Required permissions:** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function deleteInvalidForms(formIds: Array<string>): Promise<number>--><!--Device-formHost-function deleteInvalidForms(formIds: Array<string>): Promise<number>-End-->

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

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
formHost.deleteInvalidForms(formIds).then((data: number) => {
  console.info(`formHost deleteInvalidForms, data: ${JSON.stringify(data)}`);
}).catch((error: Base.BusinessError) => {
  console.error(`formHost deleteInvalidForms, error: ${JSON.stringify(error)}`);
});
```

<!--DelEnd-->
