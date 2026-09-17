# selectContacts

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## selectContacts

```TypeScript
function selectContacts(callback: AsyncCallback<Array<Contact>>): void
```

Selects a contact. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.Contacts

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[Contact](arkts-contacts-contact-contact-c.md)&gt;&gt; | Yes | Indicates the callback for getting the result of the call. If the operation is successful, an array of selected contacts is returned. If the operation fails, an error code is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../errorcode-contacts.md#401-failed-to-open-the-contact-portrait-file) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// Open the contact selection UI.
contact.selectContacts((err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to select Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
});
```

```TypeScript
import { contact } from '@kit.ContactsKit';

// Open the contact selection UI.
let promise = contact.selectContacts();
promise.then((data) => {
  console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// Open the contact selection UI and select a contact.
contact.selectContacts({
  isMultiSelect:false
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to select Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
});
```

```TypeScript
import { contact } from '@kit.ContactsKit';

// Open the contact selection UI to select a contact.
let promise = contact.selectContacts({isMultiSelect:false});
promise.then((data) => {
  console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
});
```


## selectContacts

```TypeScript
function selectContacts(): Promise<Array<Contact>>
```

Selects a contact. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.Contacts

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Contact](arkts-contacts-contact-contact-c.md)&gt;&gt; | Promise used to return the result, which is an array of selected contacts. |

**Examples**

See [selectContacts](#selectcontacts)


## selectContacts

```TypeScript
function selectContacts(options: ContactSelectionOptions, callback: AsyncCallback<Array<Contact>>): void
```

Selects a contact. (Filter criteria can be transferred during contact selection.) This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.Contacts

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ContactSelectionOptions](arkts-contacts-contact-contactselectionoptions-i.md) | Yes | Contact selection options, which specifies whether one contact or multiple contacts can be selected. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[Contact](arkts-contacts-contact-contact-c.md)&gt;&gt; | Yes | Indicates the callback for getting the result of the call. If the operation is successful, an array of selected contacts is returned. If the operation fails, an error code is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../errorcode-contacts.md#401-failed-to-open-the-contact-portrait-file) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Examples**

See [selectContacts](#selectcontacts)


## selectContacts

```TypeScript
function selectContacts(options: ContactSelectionOptions): Promise<Array<Contact>>
```

Selects a contact. (Filter criteria can be transferred during contact selection.) This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.Contacts

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ContactSelectionOptions](arkts-contacts-contact-contactselectionoptions-i.md) | Yes | Contact selection options, which specifies whether one contact or multiple contacts can be selected. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Contact](arkts-contacts-contact-contact-c.md)&gt;&gt; | Promise used to return the result, which is an array of selected contacts. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../errorcode-contacts.md#401-failed-to-open-the-contact-portrait-file) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Examples**

See [selectContacts](#selectcontacts)
