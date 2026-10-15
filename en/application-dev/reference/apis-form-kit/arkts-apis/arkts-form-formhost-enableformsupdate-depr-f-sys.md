# enableFormsUpdate (System API)

## Modules to Import

```TypeScript
```

<a id="enableformsupdate1"></a>

## enableFormsUpdate

```TypeScript
function enableFormsUpdate(formIds: Array<string>, callback: AsyncCallback<void>): void
```

Instructs the widget framework to make a widget updatable. After this API is called, the widget is in the enabled state and can receive updates from the widget provider. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [enableFormsUpdate](arkts-form-formhost-enableformsupdate-f-sys.md)

**Required permissions:** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function enableFormsUpdate(formIds: Array<string>, callback: AsyncCallback<void>): void--><!--Device-formHost-function enableFormsUpdate(formIds: Array<string>, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | List of widget IDs. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If a notification is sent to the widget framework to make the widget updatable, **error** is undefined; otherwise, **error** is an error object. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let formIds: string[] = ['12400633174999288'];
formHost.enableFormsUpdate(formIds, (error: Base.BusinessError) => {
  if (error.code) {
    console.error(`formHost enableFormsUpdate, error: ${JSON.stringify(error)}`);
  }
});
```

<!--DelEnd-->


<a id="enableformsupdate2"></a>

## enableFormsUpdate

```TypeScript
function enableFormsUpdate(formIds: Array<string>): Promise<void>
```

Instructs the widget framework to make a widget updatable. After this API is called, the widget is in the enabled state and can receive updates from the widget provider. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [enableFormsUpdate](arkts-form-formhost-enableformsupdate-f-sys.md)

**Required permissions:** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function enableFormsUpdate(formIds: Array<string>): Promise<void>--><!--Device-formHost-function enableFormsUpdate(formIds: Array<string>): Promise<void>-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | List of widget IDs. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let formIds: string[] = ['12400633174999288'];
formHost.enableFormsUpdate(formIds).then(() => {
  console.info('formHost enableFormsUpdate success');
}).catch((error: Base.BusinessError) => {
  console.error(`formHost enableFormsUpdate, error: ${JSON.stringify(error)}`);
});
```

<!--DelEnd-->
