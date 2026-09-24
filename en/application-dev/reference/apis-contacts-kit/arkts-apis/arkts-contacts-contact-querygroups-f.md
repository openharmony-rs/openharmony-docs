# queryGroups

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## queryGroups

```TypeScript
function queryGroups(callback: AsyncCallback<Array<Group>>): void
```

Queries all groups of a contact. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [queryGroups](#querygroups-1)(context: Context, callback: AsyncCallback&lt;Array&lt;Group&gt;&gt;)

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[Group](arkts-contacts-contact-group-c.md)&gt;&gt; | Yes | Indicates the callback for getting the result of the call. If the operation is successful, an array of queried groups is returned. If the operation fails, an error code is returned. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryGroups((err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Groups. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Groups.. data->${JSON.stringify(data)}`);
});
```


<a id="querygroups-1"></a>

## queryGroups

```TypeScript
function queryGroups(context: Context, callback: AsyncCallback<Array<Group>>): void
```

Queries all groups of a contact. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Indicates the context of application or capability. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[Group](arkts-contacts-contact-group-c.md)&gt;&gt; | Yes | Indicates the callback for getting the result of the call. If the operation is successful, an array of queried groups is returned. If the operation fails, an error code is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Examples**

> NOTE
> 
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance that inherits from UIAbility. To use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
contact.queryGroups(context, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Groups. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Groups. data->${JSON.stringify(data)}`);
});
```


<a id="querygroups-2"></a>

## queryGroups

```TypeScript
function queryGroups(holder: Holder, callback: AsyncCallback<Array<Group>>): void
```

Queries all groups of a contact based on the specified holder. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [queryGroups](#querygroups-3)(context: Context, holder: Holder, callback: AsyncCallback&lt;Array&lt;Group&gt;&gt;)

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| holder | [Holder](arkts-contacts-contact-holder-c.md) | Yes | Application that creates the contacts.If the passed parameter is empty, the system contact application is used by default. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[Group](arkts-contacts-contact-group-c.md)&gt;&gt; | Yes | Indicates the callback for getting the result of the call. If the operation is successful, an array of queried groups is returned. If the operation fails, an error code is returned. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryGroups({
  holderId: 1,
  bundleName: '',
  displayName: ''
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Groups. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Groups. data->${JSON.stringify(data)}`);
});
```


<a id="querygroups-3"></a>

## queryGroups

```TypeScript
function queryGroups(context: Context, holder: Holder, callback: AsyncCallback<Array<Group>>): void
```

Queries all groups of a contact based on the specified holder. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Indicates the context of application or capability. |
| holder | [Holder](arkts-contacts-contact-holder-c.md) | Yes | Application that creates the contacts.If the passed parameter is empty, the system contact application is used by default. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[Group](arkts-contacts-contact-group-c.md)&gt;&gt; | Yes | Indicates the callback for getting the result of the call. If the operation is successful, an array of queried groups is returned. If the operation fails, an error code is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Examples**

> NOTE
> 
> In the examples of this document, UIAbilityContext is obtained through this.context, where this represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
contact.queryGroups(context, {
  holderId: 1,
  bundleName: '',
  displayName: ''
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Groups. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Groups. data->${JSON.stringify(data)}`);
});
```


<a id="querygroups-4"></a>

## queryGroups

```TypeScript
function queryGroups(holder?: Holder): Promise<Array<Group>>
```

Queries all groups of a contact based on the specified holder. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [queryGroups](#querygroups-5)(context: Context, holder?: Holder)

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| holder | [Holder](arkts-contacts-contact-holder-c.md) | No | Application information for a contact. If this parameter is not specified, the system contact application is used by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Group](arkts-contacts-contact-group-c.md)&gt;&gt; | Promise used to return the result, which is an array of groups. |

**Examples**

```TypeScript
import { contact } from '@kit.ContactsKit';

let promise = contact.queryGroups({
  holderId: 1,
  bundleName: '',
  displayName: ''
});
promise.then((data) => {
  console.info(`Succeeded in querying Groups. data->${JSON.stringify(data)}`);
});
```


<a id="querygroups-5"></a>

## queryGroups

```TypeScript
function queryGroups(context: Context, holder?: Holder): Promise<Array<Group>>
```

Queries all groups of a contact based on the specified holder. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Indicates the context of application or capability. |
| holder | [Holder](arkts-contacts-contact-holder-c.md) | No | Application information for a contact. If this parameter is not specified, the system contact application is used by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Group](arkts-contacts-contact-group-c.md)&gt;&gt; | Promise used to return the result, which is an array of groups. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Examples**

> NOTE
> 
> In the examples in this document, this.context is used to obtain UIAbilityContext, where this refers to a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// Obtain the context in the component.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.queryGroups(context, {
  holderId: 1,
  bundleName: '',
  displayName: ''
});
promise.then((data) => {
  console.info(`Succeeded in querying Groups. data->${JSON.stringify(data)}`);
});
```
