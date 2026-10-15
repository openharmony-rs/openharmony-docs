# notifyVisibleForms (System API)

## Modules to Import

```TypeScript
```

<a id="notifyvisibleforms1"></a>

## notifyVisibleForms

```TypeScript
function notifyVisibleForms(formIds: Array<string>, callback: AsyncCallback<void>): void
```

Instructs the widget framework to make a widget visible. After this API is called, **onVisibilityChange** is invoked to notify the widget provider. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md)

**Required permissions:** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function notifyVisibleForms(formIds: Array<string>, callback: AsyncCallback<void>): void--><!--Device-formHost-function notifyVisibleForms(formIds: Array<string>, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | List of widget IDs. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If a notification is sent to the widget framework to make the widget visible, **error** is undefined; otherwise, **error** is an error object. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let formIds: string[] = ['12400633174999288'];
formHost.notifyVisibleForms(formIds, (error: Base.BusinessError) => {
  if (error.code) {
    console.error(`formHost notifyVisibleForms, error: ${JSON.stringify(error)}`);
  }
});
```

<!--DelEnd-->


<a id="notifyvisibleforms2"></a>

## notifyVisibleForms

```TypeScript
function notifyVisibleForms(formIds: Array<string>): Promise<void>
```

Instructs the widget framework to make a widget visible. After this API is called, **onVisibilityChange** is invoked to notify the widget provider. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md)

**Required permissions:** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function notifyVisibleForms(formIds: Array<string>): Promise<void>--><!--Device-formHost-function notifyVisibleForms(formIds: Array<string>): Promise<void>-End-->

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
formHost.notifyVisibleForms(formIds).then(() => {
  console.info('formHost notifyVisibleForms success');
}).catch((error: Base.BusinessError) => {
  console.error(`formHost notifyVisibleForms, error: ${JSON.stringify(error)}`);
});
```

<!--DelEnd-->
