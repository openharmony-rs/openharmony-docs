# updateContact

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## updateContact

```TypeScript
function updateContact(contact: Contact, callback: AsyncCallback<void>): void
```

Updates a contact. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [updateContact](#updatecontact-1)(context: Context, contact: Contact, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | Yes | Indicates the contact information. The ID is mandatory and can be obtained through [selectContacts](arkts-contacts-contact-selectcontacts-f.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Indicates the callback for getting the result of the call. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// Select a contact through the selectContacts API.
contact.selectContacts().then((data) => {
  // Obtain the context within the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.updateContact(context, {
    id: data[0].id, // ID of the selected contact.
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to update Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in updating Contact.');
  });
});
```


<a id="updatecontact-1"></a>

## updateContact

```TypeScript
function updateContact(context: Context, contact: Contact, callback: AsyncCallback<void>): void
```

Updates a contact. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Indicates the context of application or capability. |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | Yes | Indicates the contact information. The ID is mandatory and can be obtained through [selectContacts](arkts-contacts-contact-selectcontacts-f.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Indicates the callback for getting the result of the call. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait. 5.Internal error. Invalid contact rawId. |

**Examples**

> NOTE
> 
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Select a contact through the selectContacts API.
contact.selectContacts().then((data) => {
  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  contact.updateContact(context, {
    id: data[0].id, // ID of the selected contact.
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to update Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in updating Contact.');
  });
});
```


<a id="updatecontact-2"></a>

## updateContact

```TypeScript
function updateContact(contact: Contact, attrs: ContactAttributes, callback: AsyncCallback<void>): void
```

Updates a contact. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [updateContact](#updatecontact-3)(context: Context, contact: Contact, attrs: ContactAttributes, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | Yes | Indicates the contact information. The ID is mandatory and can be obtained through [selectContacts](arkts-contacts-contact-selectcontacts-f.md). |
| attrs | [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | Yes | Contact attribute list. If this parameter is left empty, all attribute fields of the contact are updated, including the name, phone number, and email address. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Indicates the callback for getting the result of the call. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';


// Select a contact through the selectContacts API.
contact.selectContacts().then((data) => {
  contact.updateContact({
    id: data[0].id, // ID of the selected contact.
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to update Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in updating Contact.');
  });
});
```


<a id="updatecontact-3"></a>

## updateContact

```TypeScript
function updateContact(context: Context, contact: Contact, attrs: ContactAttributes, callback: AsyncCallback<void>): void
```

Updates a contact. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Indicates the context of application or capability. |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | Yes | Indicates the contact information. The ID is mandatory and can be obtained through [selectContacts](arkts-contacts-contact-selectcontacts-f.md). |
| attrs | [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | Yes | Contact attribute list. If this parameter is left empty, all attribute fields of the contact are updated, including the name, phone number, and email address. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Indicates the callback for getting the result of the call. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | 1.Parameter error. Possible causes:Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait. 5.Internal error. Invalid contact rawId. |

**Examples**

> NOTE
> 
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in a page, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Select contacts through the selectContacts API.
contact.selectContacts().then((data) => {
  // Obtain the context within the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.updateContact(context, {
    id: data[0].id, // ID of the selected contact.
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to update Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in updating Contact.');
  });
});
```


<a id="updatecontact-4"></a>

## updateContact

```TypeScript
function updateContact(contact: Contact, attrs?: ContactAttributes): Promise<void>
```

Updates a contact. (The contact attribute list can be imported.) This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [updateContact](#updatecontact-5)(context: Context, contact: Contact, attrs?: ContactAttributes)

**Required permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | Yes | Indicates the contact information. The ID is mandatory and can be obtained through [selectContacts](arkts-contacts-contact-selectcontacts-f.md). |
| attrs | [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | No | Contact attribute list. If this parameter is left empty, all attribute fields of the contact are updated, including the name, phone number, and email address. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { contact } from '@kit.ContactsKit';

// Select a contact through the selectContacts API.
contact.selectContacts().then((data) => {
  let promise = contact.updateContact({
    id: data[0].id, // ID of the selected contact.
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then(() => {
    console.info('Succeeded in updating Contact.');
  });
});
```


<a id="updatecontact-5"></a>

## updateContact

```TypeScript
function updateContact(context: Context, contact: Contact, attrs?: ContactAttributes): Promise<void>
```

Updates a contact. (The contact attribute list can be imported.) This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Indicates the context of application or capability. |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | Yes | Indicates the contact information. The ID is mandatory and can be obtained through [selectContacts](arkts-contacts-contact-selectcontacts-f.md). |
| attrs | [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | No | Contact attribute list. If this parameter is left empty, all attribute fields of the contact are updated, including the name, phone number, and email address. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait. 5.Internal error. Invalid contact rawId. |

**Examples**

> NOTE
> 
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in a page, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Select a contact through the selectContacts API.
  contact.selectContacts().then((data) => {
    // Obtain the context within the component.
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let promise = contact.updateContact(context, {
      id: data[0].id, // ID of the selected contact.
      name: {
        fullName: 'xxx'
      },
      phoneNumbers: [{
        phoneNumber: '138xxxxxxxx'
      }]
    }, {
      attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
    });
    promise.then(() => {
      console.info('Succeeded in updating Contact.');
    });
  });
```
