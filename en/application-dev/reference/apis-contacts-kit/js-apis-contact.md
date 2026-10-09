# @ohos.contact (Contact)

<!--Kit: Contacts Kit-->
<!--Subsystem: Applications-->
<!--Owner: @librahCode-->
<!--Designer: @jiayanhong-hw-->
<!--Tester: @shangzhijie-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=3937f95844564676855b902f3b539685111fdaaa translatedAt=2026-07-29T01:42:24.207Z pushedAt=2026-07-30T03:36:35.621Z -->

This module provides contact management capabilities, including adding, deleting, and updating contacts.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { contact } from '@kit.ContactsKit';
```

## contact.addContact<sup>10+</sup>

addContact(context: Context, contact: Contact, callback: AsyncCallback&lt;number&gt;): void

Adds a contact. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Required Permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                        | Mandatory | Description                                                         |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                     | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| contact  | [Contact](#contact)         | Yes   | Contact information.                                                 |
| callback | AsyncCallback&lt;number&gt; | Yes   | Callback used to return the result. If the contact is added successfully, **err** is **undefined** and **data** is the ID of the added contact. Otherwise, **err** is an error object.     |

**Error codes**

For details about the following error codes, see [General Error Code Description](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait.|

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents the **UIAbility** instance that inherits from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';
  import { contact } from '@kit.ContactsKit';

  // Obtain the context within the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.addContact(context, {
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to add Contact. Code:${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  });
```

## contact.addContact<sup>(deprecated)</sup>

addContact(contact: Contact, callback: AsyncCallback&lt;number&gt;): void

Adds a contact. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [addContact](#contactaddcontact10) instead.

**Required Permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                        | Mandatory | Description                                                     |
| ------ | --------------------------- | --------- | --------------------------------------------------------------- |
| contact  | [Contact](#contact)         | Yes   | Contact information.                                             |
| callback | AsyncCallback&lt;number&gt; | Yes   | Callback used to return the result. If the contact is added successfully, **err** is **undefined** and **data** is the ID of the added contact; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';
  import { contact } from '@kit.ContactsKit';
  
  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.addContact(context, {
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to add Contact. Code:${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  });
  ```

## contact.addContact<sup>10+</sup>

addContact(context: Context, contact: Contact): Promise&lt;number&gt;

Adds a contact. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Required Permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes | Application context. For the definition of the application context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| contact | [Contact](#contact) | Yes | Contact information. |

**Return value**

| Type | Description |
| --------------------- | --------------------------------- |
| Promise&lt;number&gt; | Promise used to return the ID of the added contact. |

**Error codes**

For details about the following error codes, see [General Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message |
| -------- | ------------------ |
| 201 | Permission denied. |
| 401 | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in a UI page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.addContact(context, {
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  });
  promise.then((data) => {
    console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  });
```

## contact.addContact<sup>(deprecated)</sup>

addContact(contact: Contact): Promise&lt;number&gt;

Adds a contact. This API uses a promise to return the result.

> **NOTE**
>
> Supported since API version 7 and deprecated since API version 10. You are advised to use [addContact](#contactaddcontact10-1) instead.

**Required permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------------------- | ---- | ------------ |
| contact | [Contact](#contact) | Yes | Contact information. |

**Return value**

| Type | Description |
| --------------------- | --------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result. The value is the ID of the added contact. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Returns the data after the contact is added successfully.
  let promise = contact.addContact({
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  });
  // Callback invoked when the promise is resolved.
  promise.then((data) => {
    console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  });
  ```

## contact.deleteContact<sup>10+</sup>

deleteContact(context: Context, key: string, callback: AsyncCallback&lt;void&gt;): void

Deletes a contact. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                      | Mandatory | Description                                                         |
| ------ | ------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                   | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) for the stage model. |
| key      | string                    | Yes   | Unique query key of the contact. Each contact has a unique key, which can be obtained through [queryKey](#contactquerykey10).            |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the contact is deleted successfully, **err** is undefined; otherwise, it is an error object.     |

**Error codes**

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the UIAbilityContext, where **this** represents a UIAbility instance that inherits from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

 // Select a contact through the selectContacts API.
  contact.selectContacts().then((data) => {
    // Obtain the context within the component.
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    // Pass the key of the selected contact as the second parameter.
    contact.deleteContact(context, data[0].key, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to delete Contact. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('Succeeded in deleting Contact.');
    });
  });
```

## contact.deleteContact<sup>(deprecated)</sup>

deleteContact(key: string, callback: AsyncCallback&lt;void&gt;): void

Deletes a contact. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [deleteContact](#contactdeletecontact10) instead.

**Required Permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                      | Mandatory | Description                                 |
| -------- | ------------------------- | --------- | ------------------------------------------- |
| key      | string                    | Yes       | Unique query key of the contact. Each contact has a unique key, which can be obtained through [queryKey](#contactquerykey10). |
| callback | AsyncCallback&lt;void&gt; | Yes       | Callback used to return the result. If the contact is deleted successfully, **err** is **undefined**; otherwise, it is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Select a contact through the selectContacts API.
  contact.selectContacts().then((data) => {
    // Obtain the context within the component.
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    // Pass the key of the selected contact as the first parameter.
    contact.deleteContact(data[0].key, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to delete Contact. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info('Succeeded in deleting Contact.');
    });
  });
  ```

## contact.deleteContact<sup>10+</sup>

deleteContact(context: Context,  key: string): Promise&lt;void&gt;

Deletes a contact. This API uses a promise to return the result.

**Required permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) for the stage model. |
| key | string | Yes | Unique query key of the contact. One key corresponds to one contact. You can obtain the key through [queryKey](#contactquerykey10). |

**Return value**

| Type | Description |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise used to return the result. No value is returned. |

**Error codes**

| ID | Error Message |
| -------- | ------------------ |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the UIAbilityContext, where **this** represents the UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { common } from '@kit.AbilityKit';
  import { contact } from '@kit.ContactsKit';

  // Select a contact through the selectContacts API.
  contact.selectContacts().then((data) => {
    // Obtain the context in the component.
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    // Pass the key of the selected contact as the second parameter.
    let promise = contact.deleteContact(context, data[0].key);
    promise.then(() => {
      console.info(`Succeeded in deleting Contact.`);
    });
  });
  ```

## contact.deleteContact<sup>(deprecated)</sup>

deleteContact(key: string): Promise&lt;void&gt;

Deletes a contact. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [deleteContact](#contactdeletecontact10-1) instead.

**Required Permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type   | Mandatory | Description                                   |
| ---- | ------ | --------- | --------------------------------------------- |
| key  | string | Yes       | Unique query key of the contact. Each contact has one key, which can be obtained via [queryKey](#contactquerykey10). |

**Return value**

| Type               | Description                                   |
| ------------------ | --------------------------------------------- |
| Promise&lt;void&gt; | Promise used to return the result. A Promise that returns no value. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Select a contact via the selectContacts API.
  contact.selectContacts().then((data) => {
    // Pass the key of the selected contact as the first parameter.
    let promise = contact.deleteContact(data[0].key);
    promise.then(() => {
      console.info(`Succeeded in deleting Contact.`);
    });
  });
  ```

## contact.updateContact<sup>10+</sup>

updateContact(context: Context, contact: Contact, callback: AsyncCallback&lt;void&gt;): void

Updates a contact. This API uses an asynchronous callback to return the result.

**Required Permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                      | Mandatory | Description                                                         |
| ------ | ------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                   | Yes   | Application context. For the definition of the app context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| contact  | [Contact](#contact)       | Yes   | Contact information. The ID is mandatory and can be obtained through the [selectContacts](#contactselectcontacts10-1) API.                                         |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the contact is updated successfully, **err** is **undefined**; otherwise, **err** is an error object.     |

**Error codes**

For details about the following error codes, see [General Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait. 5.Internal error. Invalid contact rawId.  |

**Example**

>**NOTE**
>
>In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents a **UIAbility** instance inherited from **UIAbility**. If you need to use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
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

## contact.updateContact<sup>(deprecated)</sup>

updateContact(contact: Contact, callback: AsyncCallback&lt;void&gt;): void

Updates a contact. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [updateContact](#contactupdatecontact10) instead.

**Required Permissions:** ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                      | Mandatory | Description                                 |
| ------ | ------------------------- | --------- | ------------------------------------ |
| contact  | [Contact](#contact)       | Yes   | Contact information. The **id** is mandatory and can be obtained through the [selectContacts](#contactselectcontacts10-1) API.                         |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the contact is updated successfully, **err** is **undefined**; otherwise, **err** is an error object. |

**Example**

  ```js
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

## contact.updateContact<sup>10+</sup>

updateContact(context: Context,  contact: Contact, attrs: ContactAttributes, callback: AsyncCallback&lt;void&gt;): void

Updates a contact (with support for passing in a list of contact attributes). This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                    | Mandatory | Description                                                         |
| ------ | --------------------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                                 | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) of the stage model. |
| contact  | [Contact](#contact)                     | Yes   | Contact information. The ID is mandatory and can be obtained through [selectContacts](#contactselectcontacts10-1).                                         |
| attrs    | [ContactAttributes](#contactattributes) | Yes   | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, and email) are queried.                         |
| callback | AsyncCallback&lt;void&gt;               | Yes   | Callback used to return the result. If the contact is updated successfully, **err** is **undefined**; otherwise, **err** is an error object.     |

**Error codes**

For details about the following error codes, see [General Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait. 5.Internal error. Invalid contact rawId. |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents a **UIAbility** instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
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

## contact.updateContact<sup>(deprecated)</sup>

updateContact(contact: Contact, attrs: ContactAttributes, callback: AsyncCallback&lt;void&gt;): void

Updates a contact with the specified attribute list. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [updateContact](#contactupdatecontact10-1) instead.

**Required Permissions:** ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                    | Mandatory | Description                                                         |
| -------- | --------------------------------------- | --------- | ------------------------------------------------------------------- |
| contact  | [Contact](#contact)                     | Yes       | Contact information. The **id** field is mandatory and can be obtained through the [selectContacts](#contactselectcontacts10-1) API. |
| attrs    | [ContactAttributes](#contactattributes) | Yes       | List of contact attributes. If this parameter is left empty, all attributes (including name, phone number, and email) of the contact are queried. |
| callback | AsyncCallback&lt;void&gt;               | Yes       | Callback used to return the result. If the contact is updated successfully, **err** is undefined; otherwise, **err** is an error object. |

**Example**

  ```js
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

## contact.updateContact<sup>10+</sup>

updateContact(context: Context,  contact: Contact, attrs?: ContactAttributes): Promise&lt;void&gt;

Updates a contact (with the attribute list of the contact supported). This API uses a promise to return the result.

**Required Permissions:** ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                    | Mandatory | Description                                                         |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context, that is, the context of the app. For the definition of Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| contact | [Contact](#contact)                     | Yes  | Contact information. The id field is mandatory and can be obtained through the [selectContacts](#contactselectcontacts10-1) API.                                                 |
| attrs   | [ContactAttributes](#contactattributes) | No   | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, and email) are queried.                       |

**Return value**

| Type                | Description                                   |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise used to return the result. The promise returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait. 5.Internal error. Invalid contact rawId. |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the UIAbilityContext, where **this** represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
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

## contact.updateContact<sup>(deprecated)</sup>

updateContact(contact: Contact, attrs?: ContactAttributes): Promise&lt;void&gt;

Updates a contact with the specified attribute list. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [updateContact](#contactupdatecontact10-2) instead.

**Required Permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory | Description               |
| ------- | --------------------------------------- | ---- | ------------------ |
| contact | [Contact](#contact)                     | Yes   | Contact information. The id field is mandatory and can be obtained through the [selectContacts](#contactselectcontacts10-1) API.       |
| attrs   | [ContactAttributes](#contactattributes) | No   | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, email, etc.) are queried. |

**Return value**

| Type                | Description                                   |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise used to return the result. A promise that returns no value. |

**Example**

  ```js
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

## contact.isLocalContact<sup>10+</sup>

isLocalContact(context: Context,  id: number, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the current contact ID is in the phone book. This API uses an asynchronous callback to return the result.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                         | Mandatory | Description                                                        |
| ------ | ---------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                      | Yes   | Application context. For the definition of the application context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| id       | number                       | Yes   | ID attribute of the contact object. Each contact has a unique ID. |
| callback | AsyncCallback&lt;boolean&gt; | Yes   | Callback used to return the result. The value **true** indicates that the contact ID exists in the local phone book, and **false** indicates that the contact ID does not exist in the local phone book. If the operation fails, an error code is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents a **UIAbility** instance that inherits from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.isLocalContact(context, 1, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to isLocalContact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.isLocalContact<sup>(deprecated)</sup>

isLocalContact(id: number, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the current contact ID exists in the phone book. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [isLocalContact](#contactislocalcontact10) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                         | Mandatory | Description                                                        |
| -------- | ---------------------------- | --------- | ------------------------------------------------------------------ |
| id       | number                       | Yes       | ID attribute of the contact object. Each contact has a unique ID.  |
| callback | AsyncCallback&lt;boolean&gt; | Yes       | Callback used to return the result. The value **true** indicates that the contact ID is in the local phone book, and **false** indicates that the contact ID is not in the local phone book. If the operation fails, an error code is returned. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Check whether the contact with ID 1 is in the local phone book.
  contact.isLocalContact(1, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to isLocalContact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.isLocalContact<sup>10+</sup>

isLocalContact(context: Context, id: number): Promise&lt;boolean&gt;

Checks whether the current contact ID exists in the phone book. This API uses a promise to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes | Application context. For the definition of the Context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| id | number | Yes | ID attribute of a contact object. Each contact has a unique ID. |

**Return value**

| Type | Description |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the contact ID is in the local phone book, and **false** indicates that the contact ID is not in the local phone book. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ------------------ |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Parameter verification failed. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.isLocalContact(context, 1);
  promise.then((data) => {
    console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
  });
```

## contact.isLocalContact<sup>(deprecated)</sup>

isLocalContact(id: number): Promise&lt;boolean&gt;

Checks whether the current contact ID exists in the phone book. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [isLocalContact](#contactislocalcontact10-1) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type   | Mandatory | Description                                    |
| ---- | ------ | --------- | ---------------------------------------------- |
| id   | number | Yes       | ID attribute of the contact object. Each contact has a unique ID. |

**Return value**

| Type                   | Description                                                        |
| ---------------------- | ------------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the contact ID is in the local phone book, and **false** indicates that the contact ID is not in the local phone book. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Check whether the contact with ID 1 is in the local phone book.
  let promise = contact.isLocalContact(1);
  promise.then((data) => {
    console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.isMyCard<sup>10+</sup>

isMyCard(context: Context,  id: number, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the contact is "My Card". This API uses an asynchronous callback to return the result.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes | Application context Context. For the definition of Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| id | number | Yes | ID attribute of the contact card object. |
| callback | AsyncCallback&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that it is "my card", and **false** indicates the opposite. If the operation fails, an error code is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ------------------ |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Example**

> **NOTE**
>
> In the examples in this document, the UIAbilityContext is obtained through this.context, where this represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.isMyCard(context, 1, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to isMyCard. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  });
```

## contact.isMyCard<sup>(deprecated)</sup>

isMyCard(id: number, callback: AsyncCallback&lt;boolean&gt;): void

Determines whether it is "my card". This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [isMyCard](#contactismycard10) instead.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| id | number | Yes | ID attribute of the contact object. |
| callback | AsyncCallback&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the contact is 'my card', and **false** indicates the opposite. If the operation fails, an error code is returned. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Check whether the contact with ID 1 is 'my card'.
  contact.isMyCard(1, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to isMyCard. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  });
  ```

## contact.isMyCard<sup>10+</sup>

isMyCard(context: Context, id: number): Promise&lt;boolean&gt;

Checks whether a contact is "my card". This API uses a promise to return the result.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System Capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes | Application context. For the definition of the application context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| id | number | Yes | ID attribute of the name card object. |

**Return value**

| Type | Description |
| ---------------------- | ---------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that it is "my card", and **false** indicates the opposite. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ------------------ |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.isMyCard(context, 1);
  promise.then((data) => {
    console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  });
```

## contact.isMyCard<sup>(deprecated)</sup>

isMyCard(id: number): Promise&lt;boolean&gt;

Determines whether it is "My Card". This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [isMyCard](#contactismycard10-1) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type   | Mandatory | Description                 |
| ------ | ------ | ---- | -------------------- |
| id     | number | Yes   | ID attribute of the contact object. |

**Return value**

| Type                   | Description                                                       |
| ---------------------- | ---------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that it is "my card", and **false** indicates the opposite. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Check whether the contact with ID 1 is "my card".
  let promise = contact.isMyCard(1);
  promise.then((data) => {
    console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryMyCard<sup>10+</sup>

queryMyCard(context: Context,  callback: AsyncCallback&lt;Contact&gt;): void

Queries "my card". This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                     | Mandatory | Description                                                        |
| ------ | ---------------------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                                  | Yes   | Application context. For the definition of the Context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes   | Callback used to return the result. If the query of "my card" is successful, **err** is **undefined** and **data** is the obtained "my card"; otherwise, **err** is an error object.     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents the **UIAbility** instance inherited from **UIAbility**. If you need to use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryMyCard(context, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });
```

## contact.queryMyCard<sup>(deprecated)</sup>

queryMyCard(callback: AsyncCallback&lt;Contact&gt;): void

Queries "my card". This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryMyCard](#contactquerymycard10) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                     | Mandatory | Description                                                     |
| ------ | ---------------------------------------- | --------- | --------------------------------------------------------------- |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes   | Callback used to return the result. If the query of 'My Card' is successful, **err** is undefined and **data** is the obtained 'My Card'; otherwise, it is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Callback used to query 'My Card'.
  contact.queryMyCard((err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryMyCard<sup>10+</sup>

queryMyCard(context: Context, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;): void

Queries "my card" (with support for passing in a list of contact attributes). This API uses an asynchronous callback to return the result.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                     | Mandatory | Description                                                         |
| ------ | ---------------------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                                  | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) of the stage model. |
| attrs    | [ContactAttributes](#contactattributes)  | Yes   | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, and email) are queried.                    |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes   | Callback used to return the result. If the query of "my card" is successful, **err** is **undefined** and **data** is the obtained "my card"; otherwise, **err** is an error object.     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents the **UIAbility** instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryMyCard(context, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });
```

## contact.queryMyCard<sup>(deprecated)</sup>

queryMyCard(attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;): void

Queries the "my card" (supports passing in a list of contact attributes). This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryMyCard](#contactquerymycard10-1) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                     | Mandatory | Description                                                     |
| -------- | ---------------------------------------- | --------- | --------------------------------------------------------------- |
| attrs    | [ContactAttributes](#contactattributes)  | Yes       | List of contact attributes. If this parameter is left empty, all attributes of the contact (including name, phone number, and email address) are queried. |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes       | Callback used to return the result. If the query of "my card" is successful, **err** is **undefined** and **data** is the obtained "my card"; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Pass in the contact attribute list to query "my card".
  contact.queryMyCard({
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryMyCard<sup>10+</sup>

queryMyCard(context: Context,  attrs?: ContactAttributes): Promise&lt;Contact&gt;

Queries "my card" (with support for passing in a list of contact attributes). This API uses a promise to return the result.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System Capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                    | Mandatory | Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context, which is Context. For the definition of Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| attrs   | [ContactAttributes](#contactattributes) | No   | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, and email) are queried.                     |

**Return value**

| Type                               | Description                                   |
| ---------------------------------- | --------------------------------------- |
| Promise&lt;[Contact](#contact)&gt; | Promise used to return the result. Returns the "My Card" contact object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the UIAbilityContext, where **this** represents the UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryMyCard(context, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });
```

## contact.queryMyCard<sup>(deprecated)</sup>

queryMyCard(attrs?: ContactAttributes): Promise&lt;Contact&gt;

Queries my card (with support for passing in a list of contact attributes). This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryMyCard](#contactquerymycard10-2) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                    | Mandatory | Description               |
| ---- | --------------------------------------- | --------- | ------------------------- |
| attrs | [ContactAttributes](#contactattributes) | No   | Attribute list of the contact. If this parameter is left empty, all attribute fields of the contact (including name, phone number, email, etc.) are queried. |

**Return value**

| Type                               | Description                                    |
| ---------------------------------- | ----------------------------------------------- |
| Promise&lt;[Contact](#contact)&gt; | Promise used to return the result. Returns the "My Card" contact object. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Callback function used to query "My Card" by passing in the contact attribute list.
  let promise = contact.queryMyCard({
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });
  ```

## contact.selectContact<sup>(deprecated)</sup>

selectContact(callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Calls the contact selection API to open the contact selection UI. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [selectContacts](#contactselectcontacts10) instead.

**System capability:** SystemCapability.Applications.Contacts

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| ------ | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the contact selection API is called successfully, **err** is **undefined** and **data** is the array of selected contacts; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Open the contact selection UI.
  contact.selectContact((err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to select Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in selecting Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.selectContact<sup>(deprecated)</sup>

selectContact(): Promise&lt;Array&lt;Contact&gt;&gt;

Calls the contact selection API to open the contact selection UI. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [selectContacts](#contactselectcontacts10-1) instead.

**System capability:** SystemCapability.Applications.Contacts

**Return value**

| Type                                            | Description                                    |
| ----------------------------------------------- | ---------------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result. It returns the array of selected contacts. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Open the contact selection UI.
  let promise = contact.selectContact();
  promise.then((data) => {
    console.info(`Succeeded in selecting Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.selectContacts<sup>10+</sup>

selectContacts(callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Calls the contact selection API to open the contact selection UI. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.Contacts

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| ------ | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the API call to select contacts is successful, **err** is **undefined** and **data** is the array of selected contacts; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
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

## contact.selectContacts<sup>10+</sup>

selectContacts(): Promise&lt;Array&lt;Contact&gt;&gt;

Calls the contact selection API to open the contact selection UI. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.Contacts

**Return value**

| Type                                            | Description                                    |
| ----------------------------------------------- | ---------------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result. Array of selected contact objects. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Open the contact selection UI.
  let promise = contact.selectContacts();
  promise.then((data) => {
    console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.selectContacts<sup>10+</sup>

selectContacts(options: ContactSelectionOptions, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Opens the contact selection UI to select a contact. You can pass in filter criteria <a href="#contactselectionoptions10">ContactSelectionOptions</a> when selecting a contact. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                 |
| ------- | ----------------------------------------------------- | --------- | ------------------------------------------- |
| options | [ContactSelectionOptions](#contactselectionoptions10) | Yes       | Filter condition for selecting contacts, indicating single selection or multiple selection. |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes       | Callback used to return the result. If the contact selection API is called successfully, **err** is **undefined** and **data** is the array of selected contacts; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
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

## contact.selectContacts<sup>10+</sup>

selectContacts(options: ContactSelectionOptions): Promise&lt;Array&lt;Contact&gt;&gt;

Calls the contact selection API to open the contact selection UI (with filter conditions supported when selecting contacts). This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.Contacts

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------ |
| options | [ContactSelectionOptions](#contactselectionoptions10) | Yes | Filter conditions for selecting contacts, specifying whether single or multiple selection is used. |

**Return value**

| Type | Description |
| ----------------------------------------------- | --------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result. An array of the selected contacts. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ------------------ |
| 401 | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Open the contact selection UI to select a contact.
  let promise = contact.selectContacts({isMultiSelect:false});
  promise.then((data) => {
    console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContact<sup>10+</sup>

queryContact(context: Context,  key: string,  callback: AsyncCallback&lt;Contact&gt;): void

Queries a contact by key. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name    | Type                                     | Mandatory | Description                                                        |
| -------- | ---------------------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                                  | Yes       | Application context, which is the Context of the app. For the definition of Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| key      | string                                   | Yes       | Unique query key of the contact. The key is a unique identifier automatically generated by the system when a contact is created. Each contact has one key, which can be obtained through [queryKey](#contactquerykey10). |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes       | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the queried contact object; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message          |
| --- | ---------------------- |
| 201 | Permission denied.     |
| 401 | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the UIAbilityContext, where **this** represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContact(context, 'xxx', (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContact<sup>(deprecated)</sup>

queryContact(key: string,  callback: AsyncCallback&lt;Contact&gt;): void

Queries a contact based on the unique identifier key. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContact](#contactquerycontact10) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                     | Mandatory | Description                                                       |
| ------ | ---------------------------------------- | --------- | ---------------------------------------------------------- |
| key    | string                                   | Yes   | Unique query key of a contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key. It can be obtained through [queryKey](#contactquerykey10).                     |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes   | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the queried contact object; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query the contact with key='xxx'.
  contact.queryContact('xxx', (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContact<sup>10+</sup>

queryContact(context: Context,  key: string, holder: Holder, callback: AsyncCallback&lt;Contact&gt;): void

Queries a contact based on the key and holder. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                     | Mandatory | Description                                                         |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) for the stage model. |
| key      | string                                   | Yes   | Unique query key of the contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key. You can obtain the key through [queryKey](#contactquerykey10).                      |
| holder   | [Holder](#holder)                        | Yes   | Application information class of the app that creates the contact. If this parameter is left empty, the system contact app is used for the query by default.                                       |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes   | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the queried contact object; otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents a **UIAbility** instance inherited from **UIAbility**. If you need to use the capabilities provided by **UIAbilityContext** in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContact(context, 'xxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContact<sup>(deprecated)</sup>

queryContact(key: string, holder: Holder, callback: AsyncCallback&lt;Contact&gt;): void

Queries the contact based on the key and holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContact](#contactquerycontact10-1) instead.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                     | Mandatory | Description                                                       |
| ---- | ---------------------------------------- | --------- | ---------------------------------------------------------- |
| key  | string                                   | Yes       | Unique query key of the contact, which is a unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10). |
| holder | [Holder](#holder)                        | Yes       | Application information class for creating the contact. If this parameter is left empty, the system contact app is used for the query by default. |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes       | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the queried contact object; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query the contact with key='xxx' and holderId=1.
  contact.queryContact('xxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContact<sup>10+</sup>

queryContact(context: Context,  key: string,  attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;): void

Queries contacts based on the key and attrs. This API uses an asynchronous callback to return the result.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System Capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                     | Mandatory | Description                                                         |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes   | Application Context. For the definition of the app Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| key      | string                                   | Yes   | Unique query key of the contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                       |
| attrs    | [ContactAttributes](#contactattributes)  | Yes   | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, and email) are queried.                                       |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes   | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the queried contact object; otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
>In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents a **UIAbility** instance inherited from **UIAbility**. If you need to use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContact(context, 'xxx', {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContact<sup>(deprecated)</sup>

queryContact(key: string,  attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;): void

Queries a contact based on the key and specified attributes (attrs). This API uses an asynchronous callback to return the result.

> **NOTE**
>
> Supported since API version 7 and deprecated since API version 10. You are advised to use [queryContact](#contactquerycontact10-2) instead.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                     | Mandatory | Description                                                       |
| ------ | ---------------------------------------- | --------- | ---------------------------------------------------------- |
| key    | string                                   | Yes   | Unique query key of the contact. It is a unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                     |
| attrs  | [ContactAttributes](#contactattributes)  | Yes   | Contact attribute list. If this parameter is left empty, all attribute fields of the contact (including name, phone number, email, etc.) are queried.                                        |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes   | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the queried contact object; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Pass in key='xxx' and the contact attribute list for querying.
  contact.queryContact('xxx', {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContact<sup>10+</sup>

queryContact(context: Context,  key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;): void

Queries a contact based on the key, holder, and attrs. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                     | Mandatory | Description                                                         |
| ------ | ---------------------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                                  | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) for the stage model. |
| key      | string                                   | Yes   | Unique query key of the contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key. You can obtain it through [queryKey](#contactquerykey10).                       |
| holder   | [Holder](#holder)                        | Yes   | App information class for creating a contact. If this parameter is left empty, the system contact app is used for query by default.                                       |
| attrs    | [ContactAttributes](#contactattributes)  | Yes   | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, email address, etc.) are queried.                                           |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes   | Callback used to return the result. If the contact is queried successfully, **err** is undefined and **data** is the queried contact object; otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the examples in this document, UIAbilityContext is obtained through **this.context**, where **this** represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContact(context, 'xxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });
```

## contact.queryContact<sup>(deprecated)</sup>

queryContact(key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;): void

Queries the contact based on the key, holder, and attrs. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContact](#contactquerycontact10-3) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ---------------------------------------- | ---- | ---------------------------------------------------------- |
| key | string | Yes | Unique query key of the contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10). |
| holder | [Holder](#holder) | Yes | App information class for creating the contact. If this parameter is left empty, the system Contacts app is used for the query by default. |
| attrs | [ContactAttributes](#contactattributes) | Yes | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, email, etc.) are queried. |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the queried contact object; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query contacts that meet the conditions specified by key, holder, and attrs.
  contact.queryContact('xxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContact<sup>10+</sup>

queryContact(context: Context,  key: string, holder?: Holder, attrs?: ContactAttributes): Promise&lt;Contact&gt;

Queries contacts based on the key, holder, and attrs. This API uses a promise to return the result.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                    | Mandatory | Description                                                         |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes   | Application context, which is the Context of the app in the stage model. For details, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| key     | string                                  | Yes   | Unique query key of the contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key. You can obtain the key through [queryKey](#contactquerykey10).                       |
| holder  | [Holder](#holder)                       | No   | App information class for creating the contact. If this parameter is not passed, the system Contacts app is used for the query by default.       |
| attrs   | [ContactAttributes](#contactattributes) | No   | List of contact attributes. If this parameter is not passed, all contact attributes are queried by default.           |

**Return value**

| Type                               | Description                                  |
| ---------------------------------- | ------------------------------------- |
| Promise&lt;[Contact](#contact)&gt; | Promise used to return the result. The queried contact object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the UIAbilityContext, where **this** represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryContact(context, 'xxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContact<sup>(deprecated)</sup>

queryContact(key: string, holder?: Holder, attrs?: ContactAttributes): Promise&lt;Contact&gt;

Queries a contact based on the key, holder, and attrs. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContact](#contactquerycontact10-4) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                    | Mandatory | Description                                   |
| ---- | --------------------------------------- | --------- | --------------------------------------------- |
| key    | string                                  | Yes   | Unique query key of the contact. It is a unique identifier automatically generated when a contact is created. Each contact has one key, which can be obtained through [queryKey](#contactquerykey10). |
| holder | [Holder](#holder)                       | No   | App information class for creating the contact. If this parameter is not passed, the system Contacts app is used for the query by default.                |
| attrs  | [ContactAttributes](#contactattributes) | No   | List of contact attributes. If this parameter is not passed, all contact attributes are queried by default.                    |

**Return value**

| Type                               | Description                                  |
| ---------------------------------- | -------------------------------------------- |
| Promise&lt;[Contact](#contact)&gt; | Promise used to return the result. The value is the contact object queried. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Query the contact using an asynchronous callback.
  let promise = contact.queryContact('xxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>10+</sup>

queryContacts(context: Context,  callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts. This API uses an asynchronous callback to return the result.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes   | Application context, which is the Context in the stage model. For details, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, **err** is undefined and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents the **UIAbility** instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContacts(context, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>(deprecated)</sup>

queryContacts(callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContacts](#contactquerycontacts10) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| ------ | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, **err** is **undefined** and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query contacts asynchronously.
  contact.queryContacts((err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>10+</sup>

queryContacts(context: Context, holder: Holder, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts based on the holder. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| ------- | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                                               | Yes   | Application context. For the definition of the app context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| holder   | [Holder](#holder)                                     | Yes   | Application information class for creating a contact. If this parameter is left empty, the system Contacts app is used for the query by default.                                       |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the contacts are queried successfully, **err** is **undefined** and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents a **UIAbility** instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContacts(context, {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>(deprecated)</sup>

queryContacts(holder: Holder, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts based on the holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContacts](#contactquerycontacts10-1) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| ------ | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| holder   | [Holder](#holder)                                     | Yes   | App information class for creating a contact. If this parameter is left empty, the system Contacts app is used for the query by default.                                       |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, **err** is undefined and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query contacts asynchronously.
  contact.queryContacts({
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>10+</sup>

queryContacts(context: Context, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts based on attrs. This API uses an asynchronous callback to return the result.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System Capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| ------ | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                                               | Yes   | Application context, which is the context of the app in the stage model. For the definition of the application context, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| attrs    | [ContactAttributes](#contactattributes)               | Yes   | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, email, etc.) are queried.                                           |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, UIAbilityContext is obtained through **this.context**, where **this** represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContacts(context, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>(deprecated)</sup>

queryContacts(attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts based on attrs. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContacts](#contactquerycontacts10-2) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                  | Mandatory | Description                                                         |
| -------- | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| attrs    | [ContactAttributes](#contactattributes)               | Yes       | List of contact attributes. If this parameter is left empty, all contact attributes (including name, phone number, and email) are queried.                                           |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes       | Callback used to return the result. If the query is successful, **err** is undefined and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query contacts asynchronously.
  contact.queryContacts({
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>10+</sup>

queryContacts(context: Context,  holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts based on the holder and attrs. This API uses an asynchronous callback to return the result.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System Capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name    | Type                                                  | Mandatory | Description                                                         |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) of the stage model. |
| holder   | [Holder](#holder)                                     | Yes  | App information class for creating a contact. If this parameter is left empty, the system contacts app is used for the query by default.                                       |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, and email) are queried.                                           |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
>In the examples of this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents a **UIAbility** instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContacts(context, {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>(deprecated)</sup>

queryContacts(holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts based on the holder and attrs. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContacts](#contactquerycontacts10-3) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| ------ | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| holder | [Holder](#holder)                                     | Yes       | App information class for creating a contact. If this parameter is left empty, the system Contacts app is used for the query by default.                                        |
| attrs  | [ContactAttributes](#contactattributes)               | Yes       | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, and email) are queried.                                           |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes       | Callback used to return the result. If the query is successful, **err** is **undefined** and **data** is the array of contact objects found; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query contacts asynchronously.
  contact.queryContacts({
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>10+</sup>

queryContacts(context: Context,  holder?: Holder, attrs?: ContactAttributes): Promise&lt;Array&lt;Contact&gt;&gt;

Queries all contacts based on the holder and attrs. This API uses a promise to return the result.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                    | Mandatory | Description                                                         |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) of the stage model. |
| holder  | [Holder](#holder)                       | No   | Application information class for creating a contact. If this parameter is left empty, the system Contacts app is used for the query by default.       |
| attrs   | [ContactAttributes](#contactattributes) | No   | List of contact attributes. If this parameter is not passed, all contact attributes are queried by default.               |

**Return value**

| Type                                            | Description                                      |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result. The array of queried contact objects. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the UIAbilityContext, where **this** represents the UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryContacts(context, {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying Contacts. data: ${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>(deprecated)</sup>

queryContacts(holder?: Holder, attrs?: ContactAttributes): Promise&lt;Array&lt;Contact&gt;&gt;

Queries all contacts based on the holder and attrs. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContacts](#contactquerycontacts10-4) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                    | Mandatory | Description                   |
| ---- | --------------------------------------- | --------- | ----------------------------- |
| holder | [Holder](#holder)                       | No   | Application information class for creating a contact. If this parameter is not passed, the system Contacts app is used for the query by default. |
| attrs  | [ContactAttributes](#contactattributes) | No   | List of contact attributes. If this parameter is not passed, all contact attributes are queried by default.     |

**Return value**

| Type                                            | Description                                      |
| ----------------------------------------------- | ------------------------------------------------ |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result. The value is an array of the found contact objects. |

**Example**

```js
  import { contact } from '@kit.ContactsKit';

  // Query all contacts based on holder and attrs.
  let promise = contact.queryContacts({
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });
```

## contact.queryContactsByPhoneNumber<sup>10+</sup>

queryContactsByPhoneNumber(context: Context,  phoneNumber: string, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by phone number. This API uses an asynchronous callback to return the result. This API returns only the **id**, **key**, and **phoneNumbers** attributes in the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API to query by the **key** attribute returned by this API. When an app calls this API in the background to obtain contact information, it must apply for the corresponding continuous task.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name      | Type                                                  | Mandatory | Description                                                         |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                               | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) of the stage model. |
| phoneNumber | string                                                | Yes   | Phone number of the contact. Only exact match is supported, and wildcard matching is not supported.              |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, **err** is undefined and **data** is the array of contact objects found; otherwise, **err** is an error object. |

**Error codes**

For details about the following error codes, see [General Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Internal error. The query resultSet is nullptr. 3.Internal error. The query resultSet is empty.  |

**Example**

> **NOTE**
>
>In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents the **UIAbility** instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>(deprecated)</sup>

queryContactsByPhoneNumber(phoneNumber: string, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by phone number. This API uses an asynchronous callback to return the result. This API returns only the id, key, and phoneNumbers attributes in the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query based on the key attribute returned by that API. When an app calls this API to obtain contact information in the background, it must apply for the corresponding long-running task.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name      | Type                                                  | Mandatory | Description                                                        |
| --------- | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| phoneNumber | string                                                | Yes       | Phone number of the contact. Only exact match is supported, and wildcard matching is not supported.              |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes       | Callback used to return the result. If the query is successful, **err** is **undefined** and **data** is the array of contact objects found; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query contacts by phone number 138xxxxxxxx.
  contact.queryContactsByPhoneNumber('138xxxxxxxx', (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>10+</sup>

queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder: Holder, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by phone number and holder. This API uses an asynchronous callback to return the result. The list returned by this API contains only the id, key, and phoneNumbers attributes in the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query based on the key attribute returned by that API. When an app calls this API in the background to obtain contact information, it must request the corresponding long-term task.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name      | Type                                                  | Mandatory | Description                                                         |
| --------- | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| context     | Context                                               | Yes   | Application context. For the definition of Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| phoneNumber | string                                                | Yes   | Phone number of the contact. Only exact match is supported, and wildcard matching is not supported.                   |
| holder      | [Holder](#holder)                                     | Yes   | App information class for creating the contact. If this parameter is left empty, the system Contacts app is used for the query by default.                                        |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Internal error. The query resultSet is nullptr. 3.Internal error. The query resultSet is empty.   |

**Example**

> **NOTE**
>
>In the examples in this document, **this.context** is used to obtain the UIAbilityContext, where **this** represents the UIAbility instance that inherits from UIAbility. If you need to use the capabilities provided by UIAbilityContext in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>(deprecated)</sup>

queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by phone number and holder. This API uses an asynchronous callback to return the result. The returned list contains only the **id**, **key**, and **phoneNumbers** attributes of the contact information. To query all information of a contact, use the [queryContact](#contactquerycontact10-3) API to query by the **key** attribute returned by this API. When an app calls this API in the background to obtain contact information, it must request the corresponding continuous task.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-1) instead.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name      | Type                                                  | Mandatory | Description                                                        |
| --------- | ----------------------------------------------------- | --------- | ------------------------------------------------------------------ |
| phoneNumber | string                                                | Yes       | Phone number of the contact. Only exact match is supported, and wildcard matching is not supported. |
| holder      | [Holder](#holder)                                     | Yes       | App information class for creating a contact. If this parameter is left empty, the system Contacts app is used for the query by default. |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes       | Callback used to return the result. If the query is successful, **err** is **undefined** and **data** is the array of contact objects found; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query contacts by phone number 138xxxxxxxx and holderId.
  contact.queryContactsByPhoneNumber('138xxxxxxxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>10+</sup>

queryContactsByPhoneNumber(context: Context,  phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by phone number and attrs. This API uses an asynchronous callback to return the result. The list returned by this API contains only the id, key, and phoneNumbers attributes in the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query based on the attribute key returned by that API. When an app calls this API in the background to obtain contact information, it must request the corresponding continuous task.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System Capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name      | Type                                                  | Mandatory | Description                                                         |
| --------- | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| context     | Context                                               | Yes   | Application context Context. For the definition of Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| phoneNumber | string                                                | Yes   | Phone number of the contact. Only exact match is supported; wildcard matching is not supported.                  |
| attrs       | [ContactAttributes](#contactattributes)               | Yes   | List of contact attributes. If empty, all attribute fields of the contact (including name, phone number, email, etc.) are queried.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, **err** is **undefined** and **data** is the array of contact objects found; otherwise, **err** is an error object. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Internal error. The query resultSet is nullptr. 3.Internal error. The query resultSet is empty.   |

**Example**

> **NOTE**
>
>In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents a **UIAbility** instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>(deprecated)</sup>

queryContactsByPhoneNumber(phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by phone number and attrs. This API uses an asynchronous callback to return the result. The list returned by this API contains only the id, key, and phoneNumbers attributes in the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query based on the attribute key returned by that API. When an app calls this API in the background to obtain contact information, it must request the corresponding long-term task.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-2) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name      | Type                                                  | Mandatory | Description                                                         |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| phoneNumber | string                                                | Yes   | Phone number of the contact. Only full match is supported; wildcard matching is not supported.                    |
| attrs       | [ContactAttributes](#contactattributes)               | Yes   | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, and email) are queried.                                           |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, **err** is undefined and **data** is the array of contact objects found; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryContactsByPhoneNumber('138xxxxxxxx', {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>10+</sup>

queryContactsByPhoneNumber(context: Context,  phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by phone number, holder, and attrs. This API uses an asynchronous callback to return the result. The list returned by this API contains only the id, key, and phoneNumbers attributes in the contact information. To query all information about a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query based on the key attribute returned by that API. When an app calls this API to obtain contact information in the background, it must request the corresponding continuous task.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                  | Mandatory | Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                               | Yes   | Application context. For the definition of the application context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| phoneNumber | string                                                | Yes   | Phone number of the contact. Only exact match is supported, and wildcard matching is not supported.                      |
| holder      | [Holder](#holder)                                     | Yes   | Application information class for creating the contact. If this parameter is empty, the system Contacts app is used for the query by default.                                        |
| attrs       | [ContactAttributes](#contactattributes)               | Yes   | Attribute list of the contact. If this parameter is empty, all attribute fields of the contact (including name, phone number, email, etc.) are queried.                                           |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, **err** is **undefined** and **data** is the array of contact objects found; otherwise, **err** is an error object. |

**Error codes**

For details about the following error codes, see [General Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Internal error. The query resultSet is nullptr. 3.Internal error. The query resultSet is empty.   |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents a **UIAbility** instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>(deprecated)</sup>

queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by phone number, holder, and attrs. This API uses an asynchronous callback to return the result. The list returned by this API contains only the id, key, and phoneNumbers attributes in the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query based on the key attribute returned by that API. When an app calls this API in the background to obtain contact information, it must request the corresponding continuous task.

> **NOTE**
>
> Supported since API version 7 and deprecated since API version 10. You are advised to use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-3) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name      | Type                                                  | Mandatory | Description                                                         |
| --------- | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| phoneNumber | string                                                | Yes   | Phone number of the contact. Only exact match is supported, and wildcard matching is not supported.                    |
| holder      | [Holder](#holder)                                     | Yes   | App information class for creating the contact. If this parameter is empty, the system Contacts app is used for the query by default.                                        |
| attrs       | [ContactAttributes](#contactattributes)               | Yes   | List of contact attributes. If this parameter is empty, all attribute fields of the contact are queried.                                           |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, **err** is **undefined** and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryContactsByPhoneNumber('138xxxxxxxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>10+</sup>

queryContactsByPhoneNumber(context: Context,  phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise&lt;Array&lt;Contact&gt;&gt;

Queries contacts by phone number, holder, and attrs. This API uses a promise to return the result. The list returned by this API contains only the id, key, and phoneNumbers attributes of the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query based on the key attribute returned by that API. When an app calls this API in the background to obtain contact information, it must request the corresponding continuous task.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name      | Type                                    | Mandatory | Description                                                         |
| --------- | --------------------------------------- | --------- | ------------------------------------------------------------ |
| context     | Context                                 | Yes   | Application context, that is, Context. For the definition of Context in the Stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| phoneNumber | string                                  | Yes   | Phone number of the contact. Only exact match is supported, and wildcard match is not supported.                      |
| holder      | [Holder](#holder)                       | No   | App information class for creating a contact. If this parameter is not passed, the system Contacts app is used for the query by default.       |
| attrs       | [ContactAttributes](#contactattributes) | No   | List of contact attributes. If not passed, all contact attributes are queried by default.               |

**Return value**

| Type                                            | Description                                      |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the array of queried contact objects. |

**Error codes**

For details about the following error codes, see [General Error Code Description](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Internal error. The query resultSet is nullptr. 3.Internal error. The query resultSet is empty.   |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the UIAbilityContext, where **this** represents the UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>(deprecated)</sup>

queryContactsByPhoneNumber(phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise&lt;Array&lt;Contact&gt;&gt;

Queries contacts by phone number, holder, and attrs. This API uses a promise to return the result. The list returned by this API contains only the id, key, and phoneNumbers attributes in the contact information. To query all information about a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API to query by the key attribute returned by that API. When an app calls this API to obtain contact information in the background, it must request the corresponding long-running task.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-4) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name      | Type                                    | Mandatory | Description                   |
| ----------- | --------------------------------------- | ---- | ---------------------- |
| phoneNumber | string                                  | Yes   | Phone number of the contact. Only full match is supported, and wildcard matching is not supported.     |
| holder      | [Holder](#holder)                       | No   | App information class for creating the contact. If this parameter is not passed, the system Contacts app is used for the query by default. |
| attrs       | [ContactAttributes](#contactattributes) | No   | List of contact attributes. If this parameter is not passed, all contact attributes are queried by default.     |

**Return value**

| Type                                            | Description                                      |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result. Returns an array of the queried contact objects. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  let promise = contact.queryContactsByPhoneNumber('138xxxxxxxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByEmail<sup>10+</sup>

queryContactsByEmail(context: Context,  email: string, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by email. This API uses an asynchronous callback to return the result. The returned list contains only the **id**, **key**, and **Emails** attributes of the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API to query by the **key** attribute returned by this API.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| ------- | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| context | Context                                               | Yes       | Application context, that is, Context. For the definition of Context in the Stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| email   | string                                                | Yes       | Email address of the contact.                                           |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes       | Callback used to return the result. If the query is successful, **err** is **undefined** and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message           |
| --- | ------------------ |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents the **UIAbility** instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContactsByEmail(context, 'xxx@email.com', (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByEmail<sup>(deprecated)</sup>

queryContactsByEmail(email: string, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by email. This API uses an asynchronous callback to return the result. The returned list contains only the id, key, and Emails attributes of the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query by the key attribute returned by that API.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContactsByEmail](#contactquerycontactsbyemail10) instead.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| ------ | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| email    | string                                                | Yes   | Email address of the contact.                                           |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, **err** is **undefined** and **data** is the array of contact objects found; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryContactsByEmail('xxx@email.com', (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByEmail<sup>10+</sup>

queryContactsByEmail(context: Context,  email: string, holder: Holder, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by email and holder. This API uses an asynchronous callback to return the result. The list returned by this API contains only the id, key, and Emails properties in the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API to query by the key property returned by this API.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System Capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes   | App context Context. For the definition of Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| email    | string                                                | Yes   | Email address of the contact.                                           |
| holder   | [Holder](#holder)                                     | Yes   | Application information class for creating the contact. If this parameter is left empty, the system Contacts app is used for the query by default.                                        |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, err is undefined and data is the array of contact objects found; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContactsByEmail(context, 'xxx@email.com', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByEmail<sup>(deprecated)</sup>

queryContactsByEmail(email: string, holder: Holder, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by email and holder. This API uses an asynchronous callback to return the result. The returned list contains only the id, key, and Emails attributes of the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query by the attribute key returned by that API.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContactsByEmail](#contactquerycontactsbyemail10-1) instead.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                  | Mandatory | Description                                                         |
| -------- | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| email    | string                                                | Yes       | Email address of the contact.                                           |
| holder   | [Holder](#holder)                                     | Yes       | Application information class for creating a contact. If this parameter is left empty, the system Contacts app is used for the query by default.                                        |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes       | Callback used to return the result. If the query is successful, **err** is undefined and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryContactsByEmail('xxx@email.com', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByEmail<sup>10+</sup>

queryContactsByEmail(context: Context,  email: string, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by email and attributes. This API uses an asynchronous callback to return the result. The list returned by this API contains only the id, key, and Emails attributes in the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query based on the key attribute returned by that API.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                                         |
| ------ | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                                               | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) for the stage model. |
| email    | string                                                | Yes   | Email address of the contact.                                           |
| attrs    | [ContactAttributes](#contactattributes)               | Yes   | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, email, etc.) are queried.                                           |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes   | Callback used to return the result. If the contact query is successful, **err** is **undefined** and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents the **UIAbility** instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContactsByEmail(context, 'xxx@email.com', {
    attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByEmail<sup>(deprecated)</sup>

queryContactsByEmail(email: string, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on the email and attrs. This API uses an asynchronous callback to return the result. The list returned by this API contains only the id, key, and Emails attributes of the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API to query based on the key attribute returned by that API.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContactsByEmail](#contactquerycontactsbyemail10-2) instead.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                  | Mandatory | Description                                                         |
| -------- | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| email    | string                                                | Yes       | Email address of the contact.                                           |
| attrs    | [ContactAttributes](#contactattributes)               | Yes       | Attribute list of the contact. If this parameter is left empty, all attribute fields of the contact (including name, phone number, email, etc.) are queried.                                           |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes       | Callback used to return the result. If the contact query is successful, **err** is undefined and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryContactsByEmail('xxx@email.com', {
    attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByEmail<sup>10+</sup>

queryContactsByEmail(context: Context,  email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts by email, holder, and attrs. This API uses an asynchronous callback to return the result. The list returned by this API contains only the id, key, and Emails attributes in the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query by the attribute key returned by that API.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory | Description                                                        |
| -------- | ---------------------------------------------------- | --------- | ------------------------------------------------------------------ |
| context  | Context                                              | Yes       | Application context Context. For the definition of application context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| email    | string                                               | Yes       | Email address of the contact.                                      |
| holder   | [Holder](#holder)                                    | Yes       | App information class for creating the contact. If this parameter is left empty, the system contacts app is used for the query by default. |
| attrs    | [ContactAttributes](#contactattributes)              | Yes       | Attribute list of the contact. If this parameter is left empty, all attribute fields of the contact (including name, phone number, email, etc.) are queried. |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes       | Callback used to return the result. If the contact is queried successfully, err is undefined and data is the array of contact objects obtained; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                                                      |
| --- | ------------------------------------------------------------------ |
| 201 | Permission denied.                                                 |
| 401 | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

> **NOTE**
>
> In the examples in this document, UIAbilityContext is obtained through this.context, where this represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContactsByEmail(context, 'xxx@email.com', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByEmail<sup>(deprecated)</sup>

queryContactsByEmail(email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on email, holder, and attrs. This API uses an asynchronous callback to return the result. The list returned by this API contains only the id, key, and Emails attributes in the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query based on the attribute key returned by that API.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryContactsByEmail](#contactquerycontactsbyemail10-3) instead.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                  | Mandatory | Description                                                        |
| -------- | ----------------------------------------------------- | --------- | ------------------------------------------------------------ |
| email    | string                                                | Yes       | Email address of the contact.                                           |
| holder   | [Holder](#holder)                                     | Yes       | Application information class for creating the contact. If this parameter is left empty, the system contact app is used for query by default.                                       |
| attrs    | [ContactAttributes](#contactattributes)               | Yes       | List of contact attributes. If this parameter is left empty, all attribute fields of the contact (including name, phone number, email, etc.) are queried.                                           |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes       | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the array of contact objects obtained; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryContactsByEmail('xxx@email.com', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByEmail<sup>10+</sup>

queryContactsByEmail(context: Context,  email: string, holder?: Holder, attrs?: ContactAttributes): Promise&lt;Array&lt;Contact&gt;&gt;

Queries contacts by email, holder, and attrs. This API uses a promise to return the result. The returned list contains only the id, key, and Emails attributes of the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API to query by the attribute key returned by this API.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System Capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                    | Mandatory | Description                                                         |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes   | Application context. For the definition of the Context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| email   | string                                  | Yes   | Email address of the contact.                                           |
| holder  | [Holder](#holder)                       | No   | App information class for creating the contact. If this parameter is not passed, the system Contacts app is used for the query by default.                                       |
| attrs   | [ContactAttributes](#contactattributes) | No   | List of contact attributes. If not passed, all contact attributes are queried by default.                                           |

**Return value**

| Type                                            | Description                                      |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the array of found contacts. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryContactsByEmail(context, 'xxx@email.com', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByEmail<sup>(deprecated)</sup>

queryContactsByEmail(email: string, holder?: Holder, attrs?: ContactAttributes): Promise&lt;Array&lt;Contact&gt;&gt;

Queries contacts by email, holder, and attrs. This API uses a promise to return the result. The list returned by this API contains only the id, key, and Emails attributes in the contact information. To query all information of a contact, you are advised to use the [queryContact](#contactquerycontact10-3) API and query by the key attribute returned by that API.

> **NOTE**
>
> Supported since API version 7 and deprecated since API version 10. You are advised to use [queryContactsByEmail](#contactquerycontactsbyemail10-4) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                    | Mandatory | Description                   |
| ------ | --------------------------------------- | ---- | ---------------------- |
| email  | string                                  | Yes   | Email address of the contact.     |
| holder | [Holder](#holder)                       | No   | Application information class for creating a contact. If this parameter is not passed, the system Contacts app is used for the query by default. |
| attrs  | [ContactAttributes](#contactattributes) | No   | List of contact attributes. If this parameter is not passed, all contact attributes are queried by default.     |

**Return value**

| Type                                            | Description                                      |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the array of found contact objects. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  let promise = contact.queryContactsByEmail('xxx@email.com', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryGroups<sup>10+</sup>

queryGroups(context: Context,  callback: AsyncCallback&lt;Array&lt;Group&gt;&gt;): void

Queries all groups of a contact. This API uses an asynchronous callback to return the result.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System Capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                              | Mandatory | Description                                                         |
| ----- | ------------------------------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                                           | Yes   | Application Context. For the definition of Application Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes   | Callback used to return the result. If the query of contact groups is successful, **err** is **undefined** and **data** is the array of group objects obtained; otherwise, **err** is an error object. |

**Error codes**

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents a **UIAbility** instance that inherits from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
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

## contact.queryGroups<sup>(deprecated)</sup>

queryGroups(callback: AsyncCallback&lt;Array&lt;Group&gt;&gt;): void

Queries all groups of a contact. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> Supported since API version 7 and deprecated since API version 10. You are advised to use [queryGroups](#contactquerygroups10) instead.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                              | Mandatory | Description                                                         |
| ------ | ------------------------------------------------- | --------- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, **err** is **undefined** and **data** is the array of group objects obtained; otherwise, **err** is an error object. |

**Example**

  ```js
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

## contact.queryGroups<sup>10+</sup>

queryGroups(context: Context, holder: Holder, callback: AsyncCallback&lt;Array&lt;Group&gt;&gt;): void

Queries all groups of a contact based on the holder. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name    | Type                                              | Mandatory | Description                                                         |
| ------- | ------------------------------------------------- | --------- | ------------------------------------------------------------ |
| context | Context                                           | Yes       | Application context. For the definition of Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| holder  | [Holder](#holder)                                 | Yes       | Application information class for creating a contact. If this parameter is left empty, the system Contacts app is used for the query by default.                                       |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes       | Callback used to return the result. If the contact groups are queried successfully, **err** is **undefined** and **data** is the array of group objects obtained; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message           |
| --- | ------------------ |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples of this document, UIAbilityContext is obtained through **this.context**, where **this** represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
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

## contact.queryGroups<sup>(deprecated)</sup>

queryGroups(holder: Holder, callback: AsyncCallback&lt;Array&lt;Group&gt;&gt;): void

Queries all groups of a contact based on the holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> Supported since API version 7 and deprecated since API version 10. You are advised to use [queryGroups](#contactquerygroups10-1) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                              | Mandatory | Description                                                         |
| -------- | ------------------------------------------------- | --------- | ------------------------------------------------------------ |
| holder   | [Holder](#holder)                                 | Yes       | Application information class for creating a contact. If this parameter is left empty, the system Contacts app is used for query by default.                                        |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes       | Callback used to return the result. If the contact groups are queried successfully, **err** is **undefined** and **data** is the array of group objects obtained; otherwise, **err** is an error object. |

**Example**

  ```js
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

## contact.queryGroups<sup>10+</sup>

queryGroups(context: Context,  holder?: Holder): Promise&lt;Array&lt;Group&gt;&gt;

Queries all groups of a contact based on the holder. This API uses a promise to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ----------------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes | Application context. For the definition of the app context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| holder | [Holder](#holder) | No | App information class for creating a contact. If this parameter is not passed, the system Contacts app is used for the query by default. |

**Return value**

| Type | Description |
| ------------------------------------------- | --------------------------------------- |
| Promise&lt;Array&lt;[Group](#group)&gt;&gt; | Promise used to return the result. An array of queried group objects. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ------------------ |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain UIAbilityContext, where **this** refers to a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
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

## contact.queryGroups<sup>(deprecated)</sup>

queryGroups(holder?: Holder): Promise&lt;Array&lt;Group&gt;&gt;

Queries all contact groups based on the holder. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryGroups](#contactquerygroups10-2) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type              | Mandatory | Description                   |
| ------ | ----------------- | ---- | ---------------------- |
| holder | [Holder](#holder) | No   | Application information class for creating a contact. If this parameter is not passed, the system Contacts app is used for the query by default. |

**Return value**

| Type                                        | Description                                    |
| ------------------------------------------- | --------------------------------------- |
| Promise&lt;Array&lt;[Group](#group)&gt;&gt; | Promise used to return the result. The value is an array of group objects found. |

**Example**

  ```js
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

## contact.queryHolders<sup>10+</sup>

queryHolders(context: Context, callback: AsyncCallback&lt;Array&lt;Holder&gt;&gt;): void

Queries information about all apps that create contacts. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                | Mandatory | Description                                                        |
| ------ | --------------------------------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                                             | Yes   | Application context, that is, the Context of the app in the stage model. For details, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| callback | AsyncCallback&lt;Array&lt;[Holder](#holder)&gt;&gt; | Yes   | Callback used to return the result. If the query is successful, err is undefined and data is the array of objects of the app information for creating contacts; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryHolders(context, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Holders. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryHolders<sup>(deprecated)</sup>

queryHolders(callback: AsyncCallback&lt;Array&lt;Holder&gt;&gt;): void

Queries the information of all apps that create contacts. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryHolders](#contactqueryholders10) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                                                | Mandatory | Description                                                         |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Holder](#holder)&gt;&gt; | Yes   | Callback used to return the result. If the query of the application information class for creating contacts is successful, **err** is **undefined** and **data** is the array of queried application information objects; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryHolders((err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Holders. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryHolders<sup>10+</sup>

queryHolders(context: Context): Promise&lt;Array&lt;Holder&gt;&gt;

Queries all app information classes that create contacts. This API uses a promise to return the result.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes | Application Context. For the definition of Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |

**Return value**

| Type | Description |
| --------------------------------------------- | ------------------------------------------------------- |
| Promise&lt;Array&lt;[Holder](#holder)&gt;&gt; | Promise used to return the result. An array of the queried Holder objects. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ------------------ |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { common } from '@kit.AbilityKit';
  import { contact } from '@kit.ContactsKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryHolders(context);
  promise.then((data) => {
    console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryHolders<sup>(deprecated)</sup>

queryHolders(): Promise&lt;Array&lt;Holder&gt;&gt;

Queries all app information classes that created contacts. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryHolders](#contactqueryholders10-1) instead.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Return value**

| Type                                          | Description                                                    |
| --------------------------------------------- | ------------------------------------------------------- |
| Promise&lt;Array&lt;[Holder](#holder)&gt;&gt; | Promise used to return the result. The value is an array of the **Holder** objects found, which contain information about the apps that created the contacts. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  let promise = contact.queryHolders();
  promise.then((data) => {
    console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryKey<sup>10+</sup>

queryKey(context: Context,  id: number, callback: AsyncCallback&lt;string&gt;): void

Queries the key of a contact based on the contact ID. This API uses an asynchronous callback to return the result.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes | Application context. For the definition of Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| id | number | Yes | id attribute of the contact object, which is a unique identifier of the contact object in the database. |
| callback | AsyncCallback&lt;string&gt; | Yes | Callback used to return the result. If the query of the contact key is successful, **err** is undefined and **data** is the key of the contact; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ------------------ |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryKey(context, 1, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Key. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryKey<sup>(deprecated)</sup>

queryKey(id: number, callback: AsyncCallback&lt;string&gt;): void

Queries the key of a contact based on the contact ID. This API uses an asynchronous callback to return the result.

&gt; **NOTE**
&gt;
&gt; This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryKey](#contactquerykey10) instead.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                        | Mandatory | Description                                                         |
| ------ | --------------------------- | --------- | ------------------------------------------------------------ |
| id     | number                      | Yes       | ID attribute of the contact object.                                         |
| callback | AsyncCallback&lt;string&gt; | Yes       | Callback used to return the result. If the query of the contact key is successful, **err** is **undefined** and **data** is the key of the queried contact; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryKey(1, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Key. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryKey<sup>10+</sup>

queryKey(context: Context,  id: number, holder: Holder, callback: AsyncCallback&lt;string&gt;): void

Queries the key of a contact based on the contact ID and holder. This API uses an asynchronous callback to return the result.

**Required Permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name    | Type                        | Mandatory | Description                                                        |
| -------- | --------------------------- | --------- | ------------------------------------------------------------ |
| context  | Context                     | Yes       | Application context, that is, the Context of the app in the stage model. For the definition of Context, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| id       | number                      | Yes       | ID attribute of the contact object.                                         |
| holder   | [Holder](#holder)           | Yes       | App information class for creating a contact. If this parameter is left empty, the system contact app is used for the query.                                        |
| callback | AsyncCallback&lt;string&gt; | Yes       | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the key of the contact; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message          |
| --- | ---------------------- |
| 201 | Permission denied.     |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Example**

> **NOTE**
>
>In the examples in this document, **this.context** is used to obtain the **UIAbilityContext**, where **this** represents a **UIAbility** instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryKey(context, 1, {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Key. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryKey<sup>(deprecated)</sup>

queryKey(id: number, holder: Holder, callback: AsyncCallback&lt;string&gt;): void

Queries the key of a contact based on the contact ID and holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryKey](#contactquerykey10-1) instead.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name   | Type                        | Mandatory | Description                                                         |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| id       | number                      | Yes   | ID attribute of the contact object.                                         |
| holder   | [Holder](#holder)           | Yes   | App information class for creating a contact. If this parameter is left empty, the system contact app is used for the query.                                        |
| callback | AsyncCallback&lt;string&gt; | Yes   | Callback used to return the result. If the contact key is queried successfully, **err** is **undefined** and **data** is the key of the queried contact; otherwise, **err** is an error object. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryKey(1, {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Key. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryKey<sup>10+</sup>

queryKey(context: Context,  id: number, holder?: Holder): Promise&lt;string&gt;

Queries the contact key based on the contact ID and holder. This API uses a promise to return the result.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System Capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ----------------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes | Application context. For the definition of the application context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| id | number | Yes | ID attribute of the contact object. |
| holder | [Holder](#holder) | No | Application information class for creating a contact. If this parameter is not passed, the system Contacts app is used for the query. |

**Return value**

| Type | Description |
| --------------------- | ------------------------------------------ |
| Promise&lt;string&gt; | Promise used to return the result. Returns the key corresponding to the queried contact. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ------------------ |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { common } from '@kit.AbilityKit';
  import { contact } from '@kit.ContactsKit';

  // Obtain the context in the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryKey(context, 1, {
    holderId: 1,
    bundleName: '',
    displayName: ''
  });
  promise.then((data) => {
    console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryKey<sup>(deprecated)</sup>

queryKey(id: number, holder?: Holder): Promise&lt;string&gt;

Queries the key of a contact based on the contact ID and holder. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [queryKey](#contactquerykey10-2) instead.

**Required Permissions**: ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type              | Mandatory | Description                   |
| ------ | ----------------- | ---- | ---------------------- |
| id     | number            | Yes   | ID attribute of the contact object.   |
| holder | [Holder](#holder) | No   | Application information class for creating a contact. If this parameter is not passed, the system Contacts app is used for the query. |

**Return value**

| Type                  | Description                                       |
| --------------------- | ------------------------------------------ |
| Promise&lt;string&gt; | Promise used to return the result. Returns the key corresponding to the queried contact. |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  let promise = contact.queryKey(1, {
    holderId: 1,
    bundleName: '',
    displayName: ''
  });
  promise.then((data) => {
    console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsCount<sup>22+</sup>

queryContactsCount(context: Context): Promise&lt;number&gt;

Queries the total number of contacts. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 22.

**Required permissions:** ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type              | Mandatory | Description                   |
| ------ | ----------------- | ---- | ---------------------- |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)          | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) of the Stage model.   |

**Return value**

| Type                  | Description                                       |
| --------------------- | ------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the number of contacts found. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |

**Example**

> **NOTE**
>
> In the examples of this document, the UIAbilityContext is obtained through this.context, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// Obtain the context in the component.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.queryContactsCount(context);
promise.then((data) => {
  console.info(`Succeeded in querying ContactsCount. data->${JSON.stringify(data)}`);
});
```

## contact.addContactViaUI<sup>15+</sup>

addContactViaUI(context: Context, contact: Contact): Promise&lt;number&gt;

Calls the contact creation API to open the new contact UI page and complete the creation. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name | Type              | Mandatory | Description                   |
| ------ | ----------------- | ---- | ---------------------- |
| context | Context          | Yes   | Application Context. For the definition of the app Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).   |
| contact | [Contact](#contact) | Yes   | Contact information. |

**Return value**

| Type                  | Description                                       |
| --------------------- | ------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the result. Returns the ID of the added contact, which is the unique identifier automatically generated by the system when a new contact is created. One ID uniquely corresponds to one contact. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID                 | Error Message                                       |
| --------------------- | ------------------------------------------ |
| 401       | Parameter error. Possible causes: Mandatory parameters are left unspecified. |
| 801       | The specified SystemCapability name was not found. |
| 16700001       | General error. |
| 16700102       | Failed to set value to contacts data. |
| 16700103       | User cancel. |

**Example**

> **NOTE**
>
> In the examples in this document, the UIAbilityContext is obtained through **this.context**, where **this** represents the UIAbility instance that inherits from **UIAbility**. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// Obtain the context in the component.
let contactInfo: contact.Contact = {
  name: {
    fullName: 'xxx'
  },
  phoneNumbers: [{
    phoneNumber: '138xxxxxx'
  }]
}
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.addContactViaUI(context, contactInfo);
promise.then((data) => {
    console.info(`Succeeded in add Contact via UI.data->${JSON.stringify(data)}`);
  });
```

## contact.saveToExistingContactViaUI<sup>15+</sup>

saveToExistingContactViaUI(context: Context, contact: Contact): Promise&lt;number&gt;

Opens the contact selection UI to save information to an existing contact. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name | Type              | Mandatory | Description                   |
| ------ | ----------------- | ---- | ---------------------- |
| context | Context          | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) of the stage model.   |
| contact | [Contact](#contact) | Yes   | Contact information. |

**Return value**

| Type                  | Description                                       |
| --------------------- | ------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the result. Returns the ID of the added contact. |

**Error codes**

For details about the following error codes, see [General Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID                 | Error Message                                       |
| --------------------- | ------------------------------------------ |
| 401       | Parameter error. Possible causes: Mandatory parameters are left unspecified. |
| 801       | The specified SystemCapability name was not found. |
| 16700001       | General error. |
| 16700101       | Failed to get value from contacts data. |
| 16700102       | Failed to set value to contacts data. |
| 16700103       | User cancel. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// Obtain the context in the component.
let contactInfo: contact.Contact = {
  id: 1,
  name: {
    fullName: 'xxx'
  },
  phoneNumbers: [{
    phoneNumber: '138xxxxxx'
  }]
}
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.saveToExistingContactViaUI(context, contactInfo);
promise.then((data) => {
    console.info(`Succeeded in save to existing Contact via UI.data->${JSON.stringify(data)}`);
  });
``` 

## contact.addContacts<sup>23+</sup>

addContacts(context: Context, contacts: Array&lt;Contact&gt;): Promise&lt;Array&lt;number&gt;&gt;

Adds contacts in batches. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 23.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                | Mandatory | Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes   | App context, that is, Context. For the definition of Context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| contacts | Array&lt;[Contact](#contact)&gt; | Yes   | Array of contact information.                                                 |

**Return value**

| Type                  | Description                              |
| --------------------- | --------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the result. Returns an array of IDs of the contacts added in batch. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |
| 16700002      | Invalid parameter value. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

<!--code_no_check-->

```js
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

const contactInfo1: contact.Contact = {
  name: { fullName: 'xxx1'},
  phoneNumbers: [{ phoneNumber: '138xxxxxx' }]
};
const contactInfo2: contact.Contact = {
  name: { fullName: 'xxx2'},
  phoneNumbers: [{ phoneNumber: '139xxxxxx' }]
};
// Obtain the context in the component.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
contact.addContacts(context, [contactInfo1, contactInfo2]).then((data) => {
  console.info(`Succeeded in addContacts.data->${JSON.stringify(data)}`);
});
```

## contact.hasMatchedCallLog<sup>24+</sup>

hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: number, withinTime: number): Promise&lt;boolean&gt;

Checks whether there are call records that meet the specified conditions, only for carrier calls. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 24.

**Required Permissions:** ohos.permission.CHECK_CALL_LOG

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                | Mandatory | Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes   | Application context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) for the app in the stage model. |
| phoneNumber | string                                  | Yes   | Phone number of the contact.                                           |
| minDuration      | number                      | Yes   | Minimum call duration, in seconds (s). The value must be greater than 0.        |
| withinTime       | number | Yes   | Time range, in seconds (s), within which the start time and end time of the call must fall, counting from the current time. The query time range must be greater than 0 and cannot exceed 6 hours. If the specified value exceeds 6 hours, 6 hours is used for the query.               |

**Return value**

| Type                  | Description                              |
| --------------------- | --------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that there are matching call records, and **false** indicates that there are none. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |
| 16700002      | Invalid parameter value. |

**Example**

> **NOTE**
>
>In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;

const phoneNumber = '138xxxxxxxx';
const minDuration = 60;
const withinTime = 2 * 60 *60;

// Call the API to query.
contact.hasMatchedCallLog(context, phoneNumber, minDuration, withinTime).then((hasMatch:boolean) => {
  console.info(`Has matched call log: ${hasMatch}`);
});
```

## contact.hasMatchedCallLog<sup>24+</sup>

hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: number): Promise&lt;boolean&gt;

Checks whether there are matching call logs. By default, call logs within the last 6 hours are queried, and only carrier calls are targeted. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 24.

**Required Permissions:** ohos.permission.CHECK_CALL_LOG

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                | Mandatory | Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes   | Application context, which is the Context of the app in the stage model. For details, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| phoneNumber | string                                  | Yes   | Phone number of the contact.                                           |
| minDuration      | number                      | Yes   | Minimum call duration, in seconds (s). The value must be greater than 0.       |

**Return value**

| Type                  | Description                              |
| --------------------- | --------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that a matching call record exists, and **false** indicates the opposite. |

**Error codes**

For details about the following error codes, see [General Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |
| 16700002      | Invalid parameter value. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;

const phoneNumber = '138xxxxxxxx';
const minDuration = 60;
// Call the API to query. By default, call logs within the last 6 hours are queried.
contact.hasMatchedCallLog(context, phoneNumber, minDuration).then((hasMatch:boolean) => {
  console.info(`Has matched call log: ${hasMatch}`);
});
```

## contact.syncContacts

syncContacts(context: Context, mode: ContactSyncMode, progress: ContactSyncProgress, contacts: Array&lt;Contact&gt;): Promise&lt;Array&lt;number&gt;&gt;

Synchronizes multiple contacts to the contact database in batches. A maximum of 400 contacts can be synchronized per batch. Synchronizes the third-party app's own contacts to the local device. The caller must be in the foreground.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                | Mandatory | Description                                                         |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes   | App context, which is defined in [Context](../apis-ability-kit/js-apis-inner-application-context.md) for the stage model. |
| mode | [ContactSyncMode](#contactsyncmode)                                  | Yes   | Type of the contact sync mode.                                           |
| progress      | [ContactSyncProgress](#contactsyncprogress)                       | Yes   | Information about the contact sync progress.       |
| contacts      | Array&lt;[Contact](#contact)&gt;                      | Yes   | Array of contact information to be synced to the database.       |

**Return value**

| Type                  | Description                              |
| --------------------- | --------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the result. The array contains valid contact IDs indicating successful creation. |

**Error codes**

For details about the following error codes, see [General Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |
| 16700002      | Invalid parameter value. |
| 16700003      | Background usage is prohibited. |
| 16700004      | The number of contacts exceeds the limit. |
| 16700103      | User cancel. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context within the component.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let mode = contact.ContactSyncMode.MODE_INCREMENTAL;
const totalBatches: number = 3;
const syncId: number = Date.now() / 1000;
const totalCount = 300;
const batchSize = 100;
for (let batch: number = 1; batch <= totalBatches; batch++) {
  try {
    const remaining: number = totalCount - (batch - 1) * batchSize;
    const currentBatchSize: number = Math.min(batchSize, remaining);
    const contacts: contact.Contact[] = [];
    for (let i: number = 0; i < currentBatchSize; i++) {
      const contactData: contact.Contact = {
        name: {
          fullName: `Sync contact ${i + 1}_${batch} batch`
          },
        phoneNumbers: [{
          phoneNumber: `1380000${String(i + 1).padStart(4, '0')}`,
          labelName: 'Mobile'
        }],
        emails: [{
          email: `contact${i + 1}@example.com`,
          labelName: 'Work'
          }]
        };
      contacts.push(contactData);
    }
    const progress: contact.ContactSyncProgress = {
      syncId: syncId,
      currentBatch: batch,
      totalBatches: totalBatches
    };
    console.info(`Sync batch ${batch}/${totalBatches}, contact count: ${currentBatchSize}`);
    let result = await contact.syncContacts(context, mode, progress, contacts);
    console.info(`Batch ${batch} synced successfully, result: `  + JSON.stringify(result));
  }
  catch (err) {
    const e = err as BusinessError;
    console.error(`syncContacts failed: code=${e.code}, message=${e.message}`);
  }
}
```

## contact.queryContactSyncInfo

queryContactSyncInfo(context: Context): Promise&lt;Array&lt;ContactSyncInfo&gt;&gt;

Queries the contact synchronization status of the current app. An empty value indicates that the app has not initiated synchronization or synchronization is complete. This API uses a promise to return the result.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Required permissions:** ohos.permission.READ_CONTACTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type    | Mandatory | Description                                                        |
| ---- | ------- | --------- | ------------------------------------------------------------ |
| context | Context | Yes   | Application context. For the definition of the application context in the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |

**Return value**

| Type                  | Description                              |
| --------------------- | --------------------------------- |
| Promise&lt;Array&lt;[ContactSyncInfo](#contactsyncinfo)&gt;&gt; | Promise used to return the array of contact sync information of the calling app. If no contact is being synced, null is returned. |

**Error codes**

For details about the following error codes, see [General Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message           |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |

**Example**

>**NOTE**
>
>In the examples of this document, UIAbilityContext is obtained through this.context, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context within the component.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
const syncInfoList: contact.ContactSyncInfo[] = await contact.queryContactSyncInfo(context) as contact.ContactSyncInfo[];
console.info('queryContactSyncInfo syncInfoList '  + JSON.stringify(syncInfoList));
```

## contact.importContactsViaUI

importContactsViaUI(context: Context, contacts: Array&lt;Contact&gt;): Promise&lt;Array&lt;number&gt;&gt;

Imports multiple contacts in batches through UI interaction. A maximum of 100 contacts can be imported at a time. Importing contact portraits is not supported.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes | Application context. For the definition of the Context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md). |
| contacts | Array&lt;[Contact](#contact)&gt; | Yes | Array of contact information to be imported into the database. |

**Return value**

| Type | Description |
| --------------------- | --------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the result, which is an array of contact creation results. A value greater than 0 in the array indicates that the contact is created successfully, **-1** indicates creation failure, and **-2** indicates that the user did not select the contact. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID | Error Message |
| -------- | ------------------ |
| 801 | The specified SystemCapability name was not found. |
| 16700001 | General error. |
| 16700002 | Invalid parameter value. |
| 16700004 | The number of contacts exceeds the limit. |
| 16700103 | User cancel. |

**Example**

> **NOTE**
>
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context in the component.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let contactList: contact.Contact[] = [];
let contactInfo: contact.Contact = {
  name: {
    fullName: 'xxx'
  },
  phoneNumbers: [{
    phoneNumber: '138xxxxxx'
  }]
}
contactList.push(contactInfo);
let promise = contact.importContactsViaUI(context, contactList);
promise.then((data) => {
  console.info(`Succeeded in importing Contact via UI: data -> ${JSON.stringify(data)}`);
});
```

## ContactSelectionOptions<sup>10+</sup>

Options for selecting contacts.

**System capability:** SystemCapability.Applications.Contacts

|                Name               |                   Type                 | Read-Only  | Optional  |        Description      |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| isMultiSelect<sup>10+</sup>         | boolean | No   | Yes   | Whether to allow multiple selection. The value **true** means multiple selection, and **false** means single selection. The default value is **false**.<br>**Atomic Service API**: This API is supported in atomic services since API version 11.     |
| maxSelectable<sup>15+</sup>         | number | No   | Yes   | Maximum number of contacts. The default value is **10000**. If the value exceeds the upper limit, the default value is used for filtering.<br>**Atomic Service API**: This API is supported in atomic services since API version 15.     | 
| isDisplayedByName<sup>15+</sup>         | boolean | No   | Yes   | Whether to display by contact name. The value **true** means display by contact name, and **false** means display by contact number. The default value is **false**.<br>**Atomic Service API**: This API is supported in atomic services since API version 15.     |
| filter<sup>15+</sup>         | [ContactSelectionFilter](#contactselectionfilter15) | No   | Yes   | Contact query filter.<br>**Atomic Service API**: This API is supported in atomic services since API version 15.     | 
| isAutoDismissOnNavigation        | boolean | No   | Yes   | Whether to allow automatic dismissal of the picker when the page that launched it undergoes a route change. The value **true** means the picker is allowed to be dismissed automatically, and **false** means the picker is not allowed to be dismissed automatically. The default value is **false**.<br> **Since:** 26.0.0 <br> **Atomic Service API**: This API is supported in atomic services since API version 26.0.0.<br> **Model constraint**: This API can be used only in the stage model.     |

## ContactSelectionFilter<sup>15+</sup>

Defines a contact query filter.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

|                Name               |                  Type                 |  Read-Only  | Optional    |        Description      |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| filterClause        | [FilterClause](#filterclause15) |  No  |  No   |  Filter condition.     |
| filterType        | [FilterType](#filtertype15) |  No  |  No    | Filter type.     |

## FilterType<sup>15+</sup>

Enumerates the contact filter types.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.ContactsData

| Name                  | Value | Description                               |
| --------------------- | ---- | ---------------------------------- |
| SHOW_FILTER    | 0 | Displays only contacts that meet the filter conditions.<br>**System capability**: SystemCapability.Applications.Contacts |
| DEFAULT_SELECT            | 1 | Selects contacts that meet the filter conditions by default.<br>**System capability**: SystemCapability.Applications.Contacts                 |
| SHOW_FILTER_AND_DEFAULT_SELECT | 2 | Selects and displays only contacts that meet the filter conditions by default.<br>**System capability**: SystemCapability.Applications.Contacts                     |

## FilterClause<sup>15+</sup>

Defines the contact filter conditions. Multiple filter conditions are combined with an OR relationship. If a parameter is of the array type, the array can contain a maximum of three elements.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

|                Name               |                  Type                 |   Read-Only  | Optional     |        Description      |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| id         | Array\<[FilterOptions](#filteroptions15)> | No   | Yes   | Contact ID.     |
| name         | Array\<[FilterOptions](#filteroptions15)>  | No   | Yes   | Contact name.     |
| dataItem         | [DataFilter](#datafilter15) | No   | Yes   | Contact data filter item.     |
| focusModeList        | Array\<[FilterOptions](#filteroptions15)>  | No   | Yes   | Focus mode.     |

## FilterOptions<sup>15+</sup>

Defines the filter options for contacts.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

|                Name               |                  Type                 |  Read-Only  | Optional    |        Description      |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| filterCondition         | [FilterCondition](#filtercondition15) | No    |   No   | Filter condition.     |
| value        | string \| ValueType[] |  No    |   Yes   | Filter value. The default value is undefined.     |

## FilterCondition<sup>15+</sup>

Enumerates the filter conditions.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Applications.ContactsData

| Name                  | Value | Description                               |
| --------------------- | ---- | ---------------------------------- |
| IS_NOT_NULL    | 0 | The corresponding field is not null.<br>**System capability:** SystemCapability.Applications.Contacts |
| EQUAL_TO            | 1 | The corresponding field equals a value. The value type is string.<br>**System capability:** SystemCapability.Applications.Contacts |
| NOT_EQUAL_TO | 2 | The corresponding field is not equal to a value.<br>**System capability:** SystemCapability.Applications.Contacts |
| IN | 3 | The corresponding field value is in an array. The value type is string.<br>**System capability:** SystemCapability.Applications.Contacts |
| NOT_IN | 4 | The corresponding field value is not in an array.<br>**System capability:** SystemCapability.Applications.Contacts  |
| CONTAINS | 5 | The corresponding field value contains a value. The value type is string.<br>**System capability:** SystemCapability.Applications.Contacts |

## DataFilter<sup>15+</sup>

Defines a contact data filter item.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

|                Name               |                  Type                 |  Read-Only  | Optional   |        Description      |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| field         | [DataField](#datafield15) | No  | No  | Contact data field.     |
| options         | Array\<[FilterOptions](#filteroptions15)> | No  | No  | Contact filter parameters. The relationship between multiple FilterOptions in the array is OR, and the maximum length of the array is 3.     |

## DataField<sup>15+</sup>

Enumerates the contact data fields.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.ContactsData

| Name                  | Value | Description                               |
| --------------------- | --- | ---------------------------------- |
| EMAIL    | 0 | Contact email address.<br/>**System capability**: SystemCapability.Applications.Contacts |
| PHONE            | 1 | Contact phone number.<br/>**System capability**: SystemCapability.Applications.Contacts |
| ORGANIZATION | 2 | Contact organization.<br/>**System capability**: SystemCapability.Applications.Contacts |

## Contact

Defines a contact object class.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

|       Name        |                   Type                  | Read-Only | Optional | Description                                   |
| ----------------- | --------------------------------------- | ---- | ---- | -------------------------------------- |
| INVALID_CONTACT_ID | number                                 | Yes   | No    | Default contact ID. The value is **-1**.                           |
| id                | number                                  | Yes   | Yes    | Contact ID, which is automatically generated by the system.                           |
| key               | string                                  | Yes   | Yes   | Contact key, which is automatically generated by the system.               |
| contactAttributes | [ContactAttributes](#contactattributes) | No   | Yes   | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                     |
| emails            | [Email](#email)[]                       | No   | Yes   | List of email addresses of the contact.                 |
| events            | [Event](#event)[]                       | No   | Yes   | List of important dates of the contact, such as birthdays and anniversaries. |
| groups            | [Group](#group)[]                       | No   | Yes   | List of groups of the contact.<br> Note: When adding or updating a contact, you can only associate the contact with an existing group. Creating a new group is not supported.                     |
| imAddresses       | [ImAddress](#imaddress)[]               | No   | Yes   | List of instant message addresses of the contact.             |
| phoneNumbers      | [PhoneNumber](#phonenumber)[]           | No   | Yes   | List of phone numbers of the contact.                 |
| portrait          | [Portrait](#portrait)                   | No   | Yes   | Portrait of the contact.                         |
| postalAddresses   | [PostalAddress](#postaladdress)[]       | No   | Yes   | List of postal addresses of the contact.                 |
| relations         | [Relation](#relation)[]                 | No   | Yes   | List of relationships of the contact.                     |
| sipAddresses      | [SipAddress](#sipaddress)[]             | No   | Yes   | List of Session Initiation Protocol (SIP) addresses of the contact.  |
| websites          | [Website](#website)[]                   | No   | Yes   | List of websites of the contact.                     |
| name              | [Name](#name)                           | No   | Yes   | Name of the contact.                         |
| nickName          | [NickName](#nickname)                   | No   | Yes   | Nickname of the contact.                         |
| note              | [Note](#note)                           | No   | Yes   | Note of the contact.                         |
| organization      | [Organization](#organization)           | No   | Yes   | Organization information of the contact.                     |

**Example**

Creates contact data in JSON format.

```js
import { contact } from '@kit.ContactsKit';

let myContact: contact.Contact = {
    phoneNumbers: [{
        phoneNumber: '138xxxxxxxx'
    }],
    name: {
        fullName: 'fullName',
        namePrefix: 'namePrefix'
    },
    nickName: {
        nickName: 'nickName'
    }
};
```

## ContactAttributes

List of contact attributes, generally used as an input parameter to specify the contact attributes to query.

When null is passed in, all attributes are queried by default.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name       | Type                      | Read-Only | Optional | Description                    |
| ---------- | ------------------------- | --------- | -------- | ------------------------------ |
| attributes | [Attribute](#attribute)[] | No        | No       | List of contact attributes.    |

**Example**

Creates data in JSON format.

```js
let contactAttributes: contact.ContactAttributes = {
    attributes: [
        contact.Attribute.ATTR_EMAIL,
        contact.Attribute.ATTR_NAME,
        contact.Attribute.ATTR_PHONE
    ]
};
```

## Attribute

Enumerates the contact attributes. The value is of the number type.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name                  | Value | Description                               |
| --------------------- | ---- | ---------------------------------- |
| ATTR_CONTACT_EVENT    | 0 | Important dates of the contact, such as birthday and anniversary. |
| ATTR_EMAIL            | 1 | Email address of the contact.                 |
| ATTR_GROUP_MEMBERSHIP | 2 | Group of the contact.                     |
| ATTR_IM               | 3 | Instant messaging address of the contact.             |
| ATTR_NAME             | 4 | Name of the contact.                     |
| ATTR_NICKNAME         | 5 | Nickname of the contact.                     |
| ATTR_NOTE             | 6 | Note of the contact.                     |
| ATTR_ORGANIZATION     | 7 | Organization information of the contact.                 |
| ATTR_PHONE            | 8 | Phone number of the contact.                 |
| ATTR_PORTRAIT         | 9 | Portrait of the contact.                     |
| ATTR_POSTAL_ADDRESS   | 10 | Postal address of the contact.                 |
| ATTR_RELATION         | 11 | Relationship of the contact.                     |
| ATTR_SIP_ADDRESS      | 12 | Session Initiation Protocol (SIP) address of the contact.  |
| ATTR_WEBSITE          | 13 | Website of the contact.                     |

**Example**

Creates data in JSON format.

```js
let attributes = [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE];
```

## Email

Email address of the contact.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name        |   Type   | Read-Only | Optional | Description             |
| ----------- | -------- | ---- | ---- | ---------------- |
| CUSTOM_LABEL     | number    | Yes   | No   | Custom email type. The default value is **0**. |
| EMAIL_HOME       | number    | Yes   | No   | Home email type. The default value is **1**.   |
| EMAIL_WORK       | number    | Yes   | No   | Work email type. The default value is **2**.   |
| EMAIL_OTHER      | number    | Yes   | No   | Other email type. The default value is **3**.   |
| INVALID_LABEL_ID | number    | Yes   | No   | Invalid email type. The default value is **-1**.   |
| email       | string   | No   | No   | Email address.       |
| labelName   | string   | No   | Yes   | Type name of the email. |
| displayName | string   | No   | Yes   | Display name of the email. |
| labelId     | number   | No   | Yes   | Type of the email.     |

**Example**

Create data in JSON format.

```js
import { contact } from '@kit.ContactsKit';

let email: contact.Email = {
    email: 'xxx@email.com',
    displayName: 'displayName'
}
```

Alternatively, create data by using the new Email object.

```js
let email = new contact.Email();
email.email = 'xxx@email.com';
```

## Holder

Creates an app information class for a contact.

**System capability**: SystemCapability.Applications.ContactsData

| Name        | Type   | Read-Only | Optional | Description         |
| ----------- | ------ | ---- | ---- | ------------ |
| bundleName  | string | Yes   | No   | Bundle name. The default value is com.ohos.contacts. |
| displayName | string | Yes   | Yes   | App name. The default value is empty.   |
| holderId    | number | No   | Yes   | App ID. The default value is empty.    |

**Example**

Create data in JSON format.

```js
let holder: contact.Holder = {
  bundleName: 'com.ohos.contacts',
  displayName: 'displayName',
  holderId: 1
};
```

## Event

Defines the contact event class.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name              | Type   | Read-Only | Optional | Description                                      |
| ----------------- | ------ | --------- | -------- | ------------------------------------------------ |
| CUSTOM_LABEL      | number | Yes       | No       | Custom event type. The default value is 0.       |
| EVENT_ANNIVERSARY | number | Yes       | No       | Anniversary event type. The default value is 1.  |
| EVENT_OTHER       | number | Yes       | No       | Other event type. The default value is 2.        |
| EVENT_BIRTHDAY    | number | Yes       | No       | Birthday event type. The default value is 3.     |
| INVALID_LABEL_ID  | number | Yes       | No       | Invalid event type. The default value is -1.     |
| eventDate         | string | No        | No       | Date of the event.                               |
| labelName         | string | No        | Yes      | Name of the event type.                          |
| labelId           | number | No        | Yes      | Event type.                                      |

**Example**

Create data in JSON format.

```js
let event: contact.Event = {
    eventDate: '2000-01-01'
};
```

Or create data by instantiating an Event object.

```js
let event = new contact.Event();
event.eventDate = '2000-01-01';
```

## Group

Represents a contact group class.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name    |   Type   | Read-Only | Optional | Description               |
| ------- | -------- | --------- | -------- | ------------------------- |
| groupId | number   | No        | Yes      | ID of the contact group.  |
| title   | string   | No        | No       | Name of the contact group. |

**Example**

  Creates data in JSON format.

```js
import { contact } from '@kit.ContactsKit';

let group: contact.Group = {
    groupId: 1,
    title: 'title'
};
```

## ImAddress

Defines the instant message address of a contact.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name            | Type   | Read-Only | Optional | Description                              |
| --------------- | ------ | --------- | -------- | ---------------------------------------- |
| CUSTOM_LABEL     | number | Yes       | No       | Custom instant message type. The default value is **-1**. |
| IM_AIM           | number | Yes       | No       | AIM instant message type. The default value is **0**.    |
| IM_MSN           | number | Yes       | No       | MSN instant message type. The default value is **1**.    |
| IM_YAHOO         | number | Yes       | No       | YAHOO instant message type. The default value is **2**.  |
| IM_SKYPE         | number | Yes       | No       | SKYPE instant message type. The default value is **3**.  |
| IM_QQ            | number | Yes       | No       | QQ instant message type. The default value is **4**.     |
| IM_ICQ           | number | Yes       | No       | ICQ instant message type. The default value is **6**.    |
| IM_JABBER        | number | Yes       | No       | JABBER instant message type. The default value is **7**. |
| INVALID_LABEL_ID | number | Yes       | No       | Invalid instant message type. The default value is **-2**. |
| imAddress | string | No        | No       | Instant message address.                  |
| labelName | string | No        | Yes      | Name of the instant message type.         |
| labelId   | number | No        | Yes      | Instant message type.                     |

**Example**

Create data in JSON format.

```js
import { contact } from '@kit.ContactsKit';

let imAddress: contact.ImAddress = {
    imAddress: 'imAddress',
    labelName: 'labelName'
};
```

Or create data by instantiating an ImAddress object with new.

```js
let imAddress = new contact.ImAddress();
imAddress.imAddress = 'imAddress';
```

## Name

Defines the name class of a contact.

**System capability**: SystemCapability.Applications.ContactsData

| Name               |   Type   | Read-Only | Optional | Description                        |
| ------------------ | -------- | ---- | ---- | --------------------------- |
| familyName         | string   | No   | Yes   | Family name of the contact. **Atomic service API**: This API is supported in atomic services since API version 11.          |
| familyNamePhonetic | string   | No   | Yes   | Phonetic family name of the contact. **Atomic service API**: This API is supported in atomic services since API version 11.      |
| fullName           | string   | No   | No   | Full name of the contact. **Atomic service API**: This API is supported in atomic services since API version 11.              |
| givenName          | string   | No   | Yes   | Given name (first name) of the contact. **Atomic service API**: This API is supported in atomic services since API version 11. |
| givenNamePhonetic  | string   | No   | Yes   | Phonetic given name of the contact. **Atomic service API**: This API is supported in atomic services since API version 11.          |
| middleName         | string   | No   | Yes   | Middle name of the contact. **Atomic service API**: This API is supported in atomic services since API version 11.            |
| middleNamePhonetic | string   | No   | Yes   | Phonetic middle name of the contact. **Atomic service API**: This API is supported in atomic services since API version 11.        |
| namePrefix         | string   | No   | Yes   | Name prefix of the contact. **Atomic service API**: This API is supported in atomic services since API version 11.          |
| nameSuffix         | string   | No   | Yes   | Name suffix of the contact. **Atomic service API**: This API is supported in atomic services since API version 11.          |
| hasName<sup>22+</sup>            | boolean  | No   | Yes   | Whether the contact information contains a name. The value true indicates that it does, and false indicates that it does not. **Atomic service API**: This API is supported in atomic services since API version 22.          |

**Example**

Create data in JSON format.

```js
import { contact } from '@kit.ContactsKit';

let name: contact.Name = {
    familyName: 'familyName',
    fullName: 'fullName'
};
```

## NickName

Defines the nickname class of a contact.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name     | Type   | Read-Only | Optional | Description                |
| -------- | ------ | --------- | -------- | -------------------------- |
| nickName | string | No        | No       | Nickname of the contact.   |

**Example**

  Create data in JSON format.

```js
import { contact } from '@kit.ContactsKit';

let nickName: contact.NickName = {
    nickName: 'nickName'
};
```

## Note

Defines the note class of a contact.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name        |  Type  | Read-Only | Optional | Description               |
| ----------- | ------ | --------- | -------- | ------------------------- |
| noteContent | string | No        | No       | Note content of the contact. |

**Example**

Create data in JSON format.

```js
let note: contact.Note = {
    noteContent: 'noteContent'
};
```

## Organization

Defines the organization information of a contact.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

| Name  | Type   | Read-Only | Optional | Description       |
| ----- | ------ | --------- | -------- | ----------------- |
| name  | string | No        | No       | Organization name. |
| title | string | No        | Yes      | Job title.        |

**Example**

  Create data in JSON format.

```js
import { contact } from '@kit.ContactsKit';

let organization: contact.Organization = {
    name: 'name',
    title: 'title'
};
```

## PhoneNumber

Defines a contact phone number.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name             |  Type  | Read-Only  | Optional  | Description                                             |
| ---------------- | ---- | ---- | ---- | ------------------------------------------------ |
| CUSTOM_LABEL     |  number  | Yes   | No   | Custom phone type. The default value is **0**.                                 |
| NUM_HOME         |  number  | Yes   | No   | Home phone type. The default value is **1**.                                   |
| NUM_MOBILE       |  number  | Yes   | No   | Mobile phone type. The default value is **2**.                                   |
| NUM_WORK         |  number  | Yes   | No   | Work phone type. The default value is **3**.                                   |
| NUM_FAX_WORK     |  number  | Yes   | No   | Work fax phone type. The default value is **4**.                               |
| NUM_FAX_HOME     |  number  | Yes   | No   | Home fax phone type. The default value is **5**.                               |
| NUM_PAGER        |  number  | Yes   | No   | Pager phone type. The default value is **6**.                                 |
| NUM_OTHER        |  number  | Yes   | No   | Other phone type. The default value is **7**.                                   |
| NUM_CALLBACK     |  number  | Yes   | No   | Callback phone type. The default value is **8**.                                   |
| NUM_CAR          |  number  | Yes   | No   | Car phone type. The default value is **9**.                                   |
| NUM_COMPANY_MAIN |  number  | Yes   | No   | Company main phone type. The default value is **10**.                                   |
| NUM_ISDN         |  number  | Yes   | No   | Integrated Services Digital Network (ISDN) phone type. The default value is **11**.                 |
| NUM_MAIN         |  number  | Yes   | No   | Main phone type. The default value is **12**.                                     |
| NUM_OTHER_FAX    |  number  | Yes   | No   | Other fax phone type. The default value is **13**.                                   |
| NUM_RADIO        |  number  | Yes   | No   | Radio phone type. The default value is **14**.                                   |
| NUM_TELEX        |  number  | Yes   | No   | Telex phone type. The default value is **15**.                                   |
| NUM_TTY_TDD      |  number  | Yes   | No   | Teletypewriter (TTY) or Test-Driven Development (TDD) phone type. The default value is **16**. |
| NUM_WORK_MOBILE  |  number  | Yes   | No   | Work mobile phone type. The default value is **17**.                               |
| NUM_WORK_PAGER   |  number  | Yes   | No   | Work pager phone type. The default value is **18**.                             |
| NUM_ASSISTANT    |  number  | Yes   | No   | Assistant phone type. The default value is **19**.                                   |
| NUM_MMS          |  number  | Yes   | No   | Multimedia Messaging Service (MMS) phone type. The default value is **20**.                                   |
| INVALID_LABEL_ID |  number  | Yes   | No   | Invalid phone type. The default value is **-1**.                                   |
| labelName   | string   | No   | Yes   | Name of the phone number type. |
| phoneNumber | string   | No   | No   | Phone number.         |
| labelId     | number   | No   | Yes   | Phone number type.     |

**Example**

  Create data in JSON format.

```js
import { contact } from '@kit.ContactsKit';

let phoneNumber: contact.PhoneNumber = {
    phoneNumber: '138xxxxxxxx',
    labelId: contact.PhoneNumber.NUM_HOME
};
```

  Or create data by instantiating a PhoneNumber object.

```js
let phoneNumber = new contact.PhoneNumber();
phoneNumber.phoneNumber = '138xxxxxxxx';
```

## Portrait

Defines the portrait of a contact.

> **NOTE**
>
> Since API version 22, contact portrait resources can be set in URI and [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) formats (not supported by the [addContactViaUI](#contactaddcontactviaui15) and [saveToExistingContactViaUI](#contactsavetoexistingcontactviaui15) APIs).<br/>
> The URI is an accessible file address of the contact portrait, and [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) is a [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) object generated from the contact portrait resource.<br/>
> Since API version 22, contact portrait resources can be read in URI format. This format can only be opened using [fileIo.open](../apis-core-file-kit/js-apis-file-fs.md#fileioopen) and cannot be directly displayed in the Image component. It must be read and converted to [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) format for display.

**System capability:** SystemCapability.Applications.ContactsData

| Name | Type | Read-Only | Optional | Description |
| ---- | -------- | ---- | ---- | -------------- |
| uri  | string   | No   | No   | Contact portrait in URI format. **Atomic service API**: Since API version 11, this API is supported in atomic services. |
| photo<sup>22+</sup>  | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)   | No   | Yes   | Contact portrait in PixelMap format. **Atomic service API**: Since API version 22, this API is supported in atomic services. |

**Example**

  Create data using JSON format.

```js
import { contact } from '@kit.ContactsKit';
import { image } from '@kit.ImageKit';

async function SetPortraitUri(uri: string) {
  let portrait: contact.Portrait = {
    uri: uri
  };
}

async function SetPortraitPixelMap(photo: image.PixelMap) {
  let portrait: contact.Portrait = {
    uri: '',
    photo: photo
  };
}
```

## PostalAddress

Defines the postal address of a contact.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name            |  Type  | Read-Only | Optional | Description                                      |
| --------------- | ------ | --------- | -------- | ------------------------------------------------ |
| CUSTOM_LABEL    | number | Yes       | No       | Custom postal address type. The default value is **0**. |
| ADDR_HOME       | number | Yes       | No       | Home address type. The default value is **1**.         |
| ADDR_WORK       | number | Yes       | No       | Work address type. The default value is **2**.         |
| ADDR_OTHER      | number | Yes       | No       | Other address type. The default value is **3**.        |
| INVALID_LABEL_ID | number | Yes       | No       | Invalid address type. The default value is **-1**.     |
| city            | string | No        | Yes      | City of the contact.                             |
| country         | string | No        | Yes      | Country of the contact.                          |
| labelName       | string | No        | Yes      | Postal address type name.                        |
| neighborhood    | string | No        | Yes      | Neighborhood of the contact.                     |
| pobox           | string | No        | Yes      | P.O. box of the contact.                         |
| postalAddress   | string | No        | No       | Postal address of the contact.                   |
| postcode        | string | No        | Yes      | Postal code of the contact's area.               |
| region          | string | No        | Yes      | Region of the contact.                           |
| street          | string | No        | Yes      | Street of the contact.                           |
| labelId         | number | No        | Yes      | Postal address type.                             |

**Example**

Create data using JSON format.

```js
import { contact } from '@kit.ContactsKit';

let postalAddress: contact.PostalAddress = {
    city: 'city',
    postalAddress: 'postalAddress'
};
```

Alternatively, create data by instantiating a PostalAddress object.

```js
import { contact } from '@kit.ContactsKit';

let postalAddress = new contact.PostalAddress();
postalAddress.city = 'city';
postalAddress.postalAddress = 'postalAddress';
```

## Relation

Defines the relation class for a contact.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name                      | Type   | Read-Only | Optional | Description               |
| ------------------------- | ------ | --------- | -------- | ------------------------- |
| CUSTOM_LABEL              | number | Yes       | No       | Custom relation type. The default value is **0**.   |
| RELATION_ASSISTANT        | number | Yes       | No       | Assistant relation type. The default value is **1**.     |
| RELATION_BROTHER          | number | Yes       | No       | Brother relation type. The default value is **2**.     |
| RELATION_CHILD            | number | Yes       | No       | Child relation type. The default value is **3**.     |
| RELATION_DOMESTIC_PARTNER | number | Yes       | No       | Domestic partner relation type. The default value is **4**. |
| RELATION_FATHER           | number | Yes       | No       | Father relation type. The default value is **5**.     |
| RELATION_FRIEND           | number | Yes       | No       | Friend relation type. The default value is **6**.     |
| RELATION_MANAGER          | number | Yes       | No       | Manager relation type. The default value is **7**.   |
| RELATION_MOTHER           | number | Yes       | No       | Mother relation type. The default value is **8**.     |
| RELATION_PARENT           | number | Yes       | No       | Parent relation type. The default value is **9**.     |
| RELATION_PARTNER          | number | Yes       | No       | Partner relation type. The default value is **10**. |
| RELATION_REFERRED_BY      | number | Yes       | No       | Referrer relation type. The default value is **11**.   |
| RELATION_RELATIVE         | number | Yes       | No       | Relative relation type. The default value is **12**.     |
| RELATION_SISTER           | number | Yes       | No       | Sister relation type. The default value is **13**.     |
| RELATION_SPOUSE           | number | Yes       | No       | Spouse relation type. The default value is **14**.     |
| INVALID_LABEL_ID          | number | Yes       | No       | Invalid relation type. The default value is **-1**.   |
| labelName    | string | No        | Yes      | Relation type name. |
| relationName | string | No        | No       | Relation name.     |
| labelId      | number | No        | Yes      | Relation type.     |

**Example**

Create data in JSON format.

```js
import { contact } from '@kit.ContactsKit';

let relation: contact.Relation = {
    relationName: 'relationName',
    labelId: contact.Relation.RELATION_ASSISTANT
};
```

Alternatively, create data by instantiating a Relation object using new.

```js
import { contact } from '@kit.ContactsKit';

let relation = new contact.Relation();
relation.relationName = 'relationName';
relation.labelId = contact.Relation.RELATION_ASSISTANT;
```

## SipAddress

Defines the Session Initiation Protocol (SIP) address class for a contact.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name            | Type   | Read-Only | Optional | Description                              |
| --------------- | ------ | --------- | -------- | ---------------------------------------- |
| CUSTOM_LABEL    | number | Yes       | No       | Custom SIP address type. The default value is **0**. |
| SIP_HOME        | number | Yes       | No       | Home SIP address type. The default value is **1**.   |
| SIP_WORK        | number | Yes       | No       | Work SIP address type. The default value is **2**.   |
| SIP_OTHER       | number | Yes       | No       | Other SIP address type. The default value is **3**.   |
| INVALID_LABEL_ID | number | Yes       | No       | Invalid SIP address type. The default value is **-1**. |
| labelName       | string | No        | Yes      | SIP address type name. |
| sipAddress      | string | No        | No       | SIP address.         |
| labelId         | number | No        | Yes      | SIP address type.     |

**Example**

Create data in JSON format.

```js
import { contact } from '@kit.ContactsKit';

let sipAddress: contact.SipAddress = {
    sipAddress: 'sipAddress'
};
```

Alternatively, create data by instantiating a SipAddress object.

```js
import { contact } from '@kit.ContactsKit';

let sipAddress = new contact.SipAddress();
sipAddress.sipAddress = 'sipAddress';
```

## Website

Defines the website information class for a contact.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

| Name    | Type   | Read-Only | Optional | Description                          |
| ------- | ------ | --------- | -------- | ------------------------------------ |
| website | string | No        | No       | Website information of the contact. |

**Example**

Create data in JSON format.

```js
import { contact } from '@kit.ContactsKit';

let website: contact.Website = {
    website: 'website'
};
```

## ContactSyncMode

Enumerates the sync mode types.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Applications.ContactsData

| Name                  | Value | Description                               |
| --------------------- | ---- | ---------------------------------- |
| MODE_INCREMENTAL    | 1 | Inserts or updates contacts that differ between the cloud and the local device in the database. |
| MODE_CLOUD_BASED            | 2 | Replaces all local contacts with cloud contacts. When using the cloud-overwrite-local mode for batch synchronization, all local contacts (except third-party contacts) are deleted during the first batch synchronization.                 |

## ContactSyncProgress

Defines the contact sync progress information, including the sync ID, current batch, and total batches.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Applications.ContactsData

|                Name               |                  Type                 |  Read-Only  | Optional    |        Description      |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| syncId        | number |  No  |  No   |  Sync identifier used to synchronize all contacts. The value ranges from 0 to 2147483647.     |
| currentBatch        | number |  No  |  No    | Identifier of the current contact batch to synchronize. The value ranges from 1 to totalBatches.     |
| totalBatches        | number |  No  |  No    | Total number of contact batches to synchronize.     |

## ContactSyncInfo

Information about contact synchronization for the calling app.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Applications.ContactsData

|                Name               |                  Type                 |  Read-Only  | Optional    |        Description      |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| mode        | [ContactSyncMode](#contactsyncmode) |  No  |  No   |  Contact synchronization mode.     |
| syncId        | number |  No  |  No    | Synchronization ID used to synchronize all contacts.     |
| completedBatches        | Array&lt;number&gt; |  No  |  No    | Array of batch IDs of contacts that have been successfully synchronized. The value ranges from 1 to **totalBatches**.      |
| totalBatches        | number |  No  |  No    | Total number of contact batches to be synchronized.     |
| lastSyncTime        | number |  No  |  No    | Latest timestamp of contact synchronization, in milliseconds (ms).|