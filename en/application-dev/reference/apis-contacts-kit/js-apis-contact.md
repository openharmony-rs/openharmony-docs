# @ohos.contact (Contacts)

<!--Kit: Contacts Kit-->
<!--Subsystem: Applications-->
<!--Owner: @librahCode-->
<!--Designer: @jiayanhong-hw-->
<!--Tester: @shangzhijie-->
<!--Adviser: @zhang_yixin13-->
The **contact** module provides contact management functions, such as adding, deleting, and updating contacts.

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

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                       | Mandatory| Description                                                        |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                     | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| contact  | [Contact](#contact)         | Yes  | Contact information.                                                |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the result. If the contact is added successfully, **err** is **undefined** and **data** is the ID of the added contact. Otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait.|

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

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
> This API is supported since API version 7 and deprecated since API version 10. Use [addContact](#contactaddcontact10) instead.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                       | Mandatory| Description                                                    |
| -------- | --------------------------- | ---- | -------------------------------------------------------- |
| contact  | [Contact](#contact)         | Yes  | Contact information.                                            |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the result. If the contact is added successfully, **err** is **undefined** and **data** is the ID of the added contact. Otherwise, **err** is an error object.|

**Example**

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

## contact.addContact<sup>10+</sup>

addContact(context: Context, contact: Contact): Promise<number&gt;

Adds a contact. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| contact | [Contact](#contact) | Yes  | Contact information.                                                |

**Return Value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result, which is the ID of the added contact.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

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
> This API is supported since API version 7 and deprecated since API version 10. Use [addContact](#contactaddcontact10-1) instead.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type               | Mandatory| Description        |
| ------- | ------------------- | ---- | ------------ |
| contact | [Contact](#contact) | Yes  | Contact information.|

**Return Value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result, which is the ID of the added contact.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Promise used to return the added data.
  let promise = contact.addContact({
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  });
  // Promise used to return resolve if the execution is successful.
  promise.then((data) => {
    console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  });
  ```

## contact.deleteContact<sup>10+</sup>

deleteContact(context: Context, key: string, callback: AsyncCallback&lt;void&gt;): void

Deletes a contact. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                   | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key      | string                    | Yes  | Unique query key of a contact. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).           |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the contact is deleted successfully, **err** is **undefined**. Otherwise, **err** is an error object.    |

**Error codes**

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

 // Select a contact via selectContacts.
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
> This API is supported since API version 7 and deprecated since API version 10. Use [deleteContact](#contactdeletecontact10) instead.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                     | Mandatory| Description                                |
| -------- | ------------------------- | ---- | ------------------------------------ |
| key      | string                    | Yes  | Unique query key of a contact. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the contact is deleted successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Select a contact via selectContacts.
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

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type   | Mandatory| Description                                                        |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key     | string  | Yes  | Unique query key of a contact. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                     |

**Return Value**

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { common } from '@kit.AbilityKit';
  import { contact } from '@kit.ContactsKit';

  // Select a contact via selectContacts.
  contact.selectContacts().then((data) => {
    // Obtain the context within the component.
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
> This API is supported since API version 7 and deprecated since API version 10. Use [deleteContact](#contactdeletecontact10-1) instead.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| key    | string | Yes  | Unique query key of a contact. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).|

**Return Value**

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Select a contact via selectContacts.
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

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                   | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| contact  | [Contact](#contact)       | Yes  | Contact information. The ID is mandatory and can be obtained through [selectContacts](#contactselectcontacts10-1).                                        |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the contact is updated successfully, **err** is **undefined**. Otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait. 5.Internal error. Invalid contact rawId.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Select a contact via selectContacts.
  contact.selectContacts().then((data) => {
    // Obtain the context within the component.
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

    contact.updateContact(context, {
      id: data[0].id, // Select the contact ID.
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
> This API is supported since API version 7 and deprecated since API version 10. Use [updateContact](#contactupdatecontact10) instead.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                     | Mandatory| Description                                |
| -------- | ------------------------- | ---- | ------------------------------------ |
| contact  | [Contact](#contact)       | Yes  | Contact information. The ID is mandatory and can be obtained through [selectContacts](#contactselectcontacts10-1).                        |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the contact is updated successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Select a contact via selectContacts.
  contact.selectContacts().then((data) => {
    // Obtain the context within the component.
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    contact.updateContact(context, {
      id: data[0].id, // Select the contact ID.
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

Updates a contact. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                   | Mandatory| Description                                                        |
| -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| contact  | [Contact](#contact)                     | Yes  | Contact information. The ID is mandatory and can be obtained through [selectContacts](#contactselectcontacts10-1).                                        |
| attrs    | [ContactAttributes](#contactattributes) | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                        |
| callback | AsyncCallback&lt;void&gt;               | Yes  | Callback used to return the result. If the contact is updated successfully, **err** is **undefined**. Otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait. 5.Internal error. Invalid contact rawId. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Select a contact via selectContacts.
  contact.selectContacts().then((data) => {
    // Obtain the context within the component.
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    contact.updateContact(context, {
      id: data[0].id, // Select the contact ID.
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

Updates a contact. The contact attribute list can be imported. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [updateContact](#contactupdatecontact10-1) instead.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                   | Mandatory| Description                                |
| -------- | --------------------------------------- | ---- | ------------------------------------ |
| contact  | [Contact](#contact)                     | Yes  | Contact information. The ID is mandatory and can be obtained through [selectContacts](#contactselectcontacts10-1).                        |
| attrs    | [ContactAttributes](#contactattributes) | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                  |
| callback | AsyncCallback&lt;void&gt;               | Yes  | Callback used to return the result. If the contact is updated successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';


  // Select a contact via selectContacts.
  contact.selectContacts().then((data) => {
    contact.updateContact({
      id: data[0].id, // Select the contact ID.
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

Updates a contact. (The contact attribute list can be imported.) This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| contact | [Contact](#contact)                     | Yes  | Contact information. The ID is mandatory and can be obtained through [selectContacts](#contactselectcontacts10-1).                                                |
| attrs   | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                      |

**Return Value**

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Failed to open contact portrait file. 3.Internal error. Invalid contact id. Failed to generate contact profile. 4.Internal error. Failed to save contact portrait. 5.Internal error. Invalid contact rawId. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Select a contact via selectContacts.
  contact.selectContacts().then((data) => {
    // Obtain the context within the component.
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let promise = contact.updateContact(context, {
      id: data[0].id, // Select the contact ID.
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

Updates a contact. The contact attribute list can be imported. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [updateContact](#contactupdatecontact10-2) instead.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description              |
| ------- | --------------------------------------- | ---- | ------------------ |
| contact | [Contact](#contact)                     | Yes  | Contact information. The ID is mandatory and can be obtained through [selectContacts](#contactselectcontacts10-1).      |
| attrs   | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.|

**Return Value**

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Select a contact via selectContacts.
  contact.selectContacts().then((data) => {
    let promise = contact.updateContact({
      id: data[0].id, // Select the contact ID.
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

Checks whether the ID of this contact is in the local address book. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                        | Mandatory| Description                                                        |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                      | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| id       | number                       | Yes  | Contact ID. Each contact corresponds to one ID.                  |
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. If the operation is successful, a Boolean value is returned. The value **true** indicates that the contact ID is in the local phonebook, and the value **false** indicates the opposite. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Checks whether the ID of this contact is in the local address book. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [isLocalContact](#contactislocalcontact10) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                        | Mandatory| Description                                                        |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| id       | number                       | Yes  | Contact ID. Each contact corresponds to one ID.                  |
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. If the operation is successful, a Boolean value is returned. The value **true** indicates that the contact ID is in the local phonebook, and the value **false** indicates the opposite. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Check whether the contact whose ID is 1 is in the local address book.
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

Checks whether the ID of this contact is in the local address book. This API uses a promise to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type   | Mandatory| Description                                                        |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| id      | number  | Yes  | Contact ID. Each contact corresponds to one ID.                  |

**Return Value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the contact ID is in the local phonebook, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.isLocalContact(context, 1);
  promise.then((data) => {
    console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
  });
```

## contact.isLocalContact<sup>(deprecated)</sup>

isLocalContact(id: number): Promise&lt;boolean&gt;

Checks whether the ID of this contact is in the local address book. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [isLocalContact](#contactislocalcontact10-1) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type  | Mandatory| Description                                      |
| ------ | ------ | ---- | ------------------------------------------ |
| id     | number | Yes  | Contact ID. Each contact corresponds to one ID.|

**Return Value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the contact ID is in the local phonebook, and the value **false** indicates the opposite.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Check whether the contact whose ID is 1 is in the local address book.
  let promise = contact.isLocalContact(1);
  promise.then((data) => {
    console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.isMyCard<sup>10+</sup>

isMyCard(context: Context,  id: number, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether a contact is included in my card. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                        | Mandatory| Description                                                        |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                      | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| id       | number                       | Yes  | Contact ID.                                          |
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. If the operation is successful, a Boolean value is returned. The value **true** indicates that the contact is included in my card, and the value **false** indicates the opposite. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Checks whether a contact is included in my card. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [isMyCard](#contactismycard10) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                        | Mandatory| Description                                                        |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| id       | number                       | Yes  | Contact ID.                                          |
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. If the operation is successful, a Boolean value is returned. The value **true** indicates that the contact is included in my card, and the value **false** indicates the opposite. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Check whether the contact whose ID is 1 is included in my card.
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

Checks whether a contact is included in my card. This API uses a promise to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type   | Mandatory| Description                                                        |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| id      | number  | Yes  | Contact ID.                                        |

**Return Value**

| Type                  | Description                                                      |
| ---------------------- | ---------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise The value **true** indicates that the contact is included in my card, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.isMyCard(context, 1);
  promise.then((data) => {
    console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  });
```

## contact.isMyCard<sup>(deprecated)</sup>

isMyCard(id: number): Promise&lt;boolean&gt;

Checks whether a contact is included in my card. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [isMyCard](#contactismycard10-1) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| id     | number | Yes  | Contact ID.|

**Return Value**

| Type                  | Description                                                      |
| ---------------------- | ---------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise The value **true** indicates that the contact is included in my card, and the value **false** indicates the opposite.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Check whether the contact whose ID is 1 is included in my card.
  let promise = contact.isMyCard(1);
  promise.then((data) => {
    console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryMyCard<sup>10+</sup>

queryMyCard(context: Context,  callback: AsyncCallback&lt;Contact&gt;): void

Queries my card. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                        |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If my card is queried successfully, **err** is **undefined** and **data** is the **MyCard** object obtained. Otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries my card. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryMyCard](#contactquerymycard10) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                    |
| -------- | ---------------------------------------- | ---- | -------------------------------------------------------- |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If my card is queried successfully, **err** is **undefined** and **data** is the **MyCard** object obtained. Otherwise, **err** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Callback used to query my card.
  contact.queryMyCard((err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryMyCard<sup>10+</sup>

queryMyCard(context: Context,  attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;): void

Queries my card. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                        |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                   |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If my card is queried successfully, **err** is **undefined** and **data** is the **MyCard** object obtained. Otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries my card. (The contact attribute list can be imported.) This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryMyCard](#contactquerymycard10-1) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                    |
| -------- | ---------------------------------------- | ---- | -------------------------------------------------------- |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                      |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If my card is queried successfully, **err** is **undefined** and **data** is the **MyCard** object obtained. Otherwise, **err** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Import the contact attribute list to query my card.
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

Queries my card. (The contact attribute list can be imported.) This API uses a promise to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| attrs   | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                    |

**Return Value**

| Type                              | Description                                   |
| ---------------------------------- | --------------------------------------- |
| Promise&lt;[Contact](#contact)&gt; | Promise used to return the result, which is a contact in my card.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries my card. (The contact attribute list can be imported.) This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryMyCard](#contactquerymycard10-2) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type                                   | Mandatory| Description              |
| ------ | --------------------------------------- | ---- | ------------------ |
| attrs  | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.|

**Return Value**

| Type                              | Description                                   |
| ---------------------------------- | --------------------------------------- |
| Promise&lt;[Contact](#contact)&gt; | Promise used to return the result, which is a contact in my card.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Callback used to import the contact attribute list to query my card.
  let promise = contact.queryMyCard({
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });
  ```

## contact.selectContact<sup>(deprecated)</sup>

selectContact(callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Selects a contact. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [selectContacts](#contactselectcontacts10) instead.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If a contact is selected successfully, **err** is **undefined** and **data** is an array of selected contacts. Otherwise, **err** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Open the UI to select a contact.
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

Selects a contact. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [selectContacts](#contactselectcontacts10-1) instead.

**System capability**: SystemCapability.Applications.Contacts

**Return Value**

| Type                                           | Description                                   |
| ----------------------------------------------- | --------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of selected contacts.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Open the UI to select a contact.
  let promise = contact.selectContact();
  promise.then((data) => {
    console.info(`Succeeded in selecting Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.selectContacts<sup>10+</sup>

selectContacts(callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Selects a contact. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If a contact is selected successfully, **err** is **undefined** and **data** is an array of selected contacts. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Open the UI to select a contact.
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

Selects a contact. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.Contacts

**Return Value**

| Type                                           | Description                                   |
| ----------------------------------------------- | --------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of selected contacts.|


**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Open the UI to select a contact.
  let promise = contact.selectContacts();
  promise.then((data) => {
    console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.selectContacts<sup>10+</sup>

selectContacts(options: ContactSelectionOptions, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Selects a contact. ([ContactSelectionOptions](#contactselectionoptions10) can be transferred during contact selection.) This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------ |
| options | [ContactSelectionOptions](#contactselectionoptions10) | Yes  | Contact selection options, which specifies whether one contact or multiple contacts can be selected.|
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If a contact is selected successfully, **err** is **undefined** and **data** is an array of selected contacts. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Open the UI to select a contact. A contact can be selected.
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

Selects a contact. (Filter criteria can be transferred during contact selection.) This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------ |
| options | [ContactSelectionOptions](#contactselectionoptions10) | Yes  | Contact selection options, which specifies whether one contact or multiple contacts can be selected.|

**Return Value**

| Type                                           | Description                                   |
| ----------------------------------------------- | --------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of selected contacts.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Open the UI to select a contact. A contact can be selected.
  let promise = contact.selectContacts({isMultiSelect:false});
  promise.then((data) => {
    console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContact<sup>10+</sup>

queryContact(context: Context,  key: string,  callback: AsyncCallback&lt;Contact&gt;): void

Queries a contact based on the specified key. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                        |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key      | string                                   | Yes  | Unique query key of a contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                      |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the **Contact** object queried. Otherwise, **data** is an error object.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Query a contact based on the unique identifier (key). This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContact](#contactquerycontact10) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                      |
| -------- | ---------------------------------------- | ---- | ---------------------------------------------------------- |
| key      | string                                   | Yes  | Unique query key of a contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                    |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the **Contact** object queried. Otherwise, **data** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query the contact whose key is xxx.
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

Queries a contact based on the specified key and holder. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                        |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key      | string                                   | Yes  | Unique query key of a contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                     |
| holder   | [Holder](#holder)                        | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                      |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the **Contact** object queried. Otherwise, **data** is an error object.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified key and holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContact](#contactquerycontact10-1) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                      |
| -------- | ---------------------------------------- | ---- | ---------------------------------------------------------- |
| key      | string                                   | Yes  | Unique query key of a contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                   |
| holder   | [Holder](#holder)                        | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                    |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the **Contact** object queried. Otherwise, **data** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query the contact whose key is xxx and holder ID is 1.
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

Queries a contact based on the specified key and attributes. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                        |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key      | string                                   | Yes  | Unique query key of a contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                      |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                      |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the **Contact** object queried. Otherwise, **data** is an error object.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified key and attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContact](#contactquerycontact10-2) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                      |
| -------- | ---------------------------------------- | ---- | ---------------------------------------------------------- |
| key      | string                                   | Yes  | Unique query key of a contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                    |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                       |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the **Contact** object queried. Otherwise, **data** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Pass the key whose value is xxx and the list of contact attributes for query.
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

Queries a contact based on the specified key, holder, and attributes. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                        |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key      | string                                   | Yes  | Unique query key of a contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                      |
| holder   | [Holder](#holder)                        | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                      |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the **Contact** object queried. Otherwise, **data** is an error object.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified key, holder, and attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContact](#contactquerycontact10-3) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                      |
| -------- | ---------------------------------------- | ---- | ---------------------------------------------------------- |
| key      | string                                   | Yes  | Unique query key of a contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                    |
| holder   | [Holder](#holder)                        | Yes  | Contact application information. If this parameter is empty, the system contact application is used for query by default.                                    |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                        |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is the **Contact** object queried. Otherwise, **data** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query the contact whose key, holder and attributes meet the conditions.
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

Queries a contact based on the specified key, holder, and attributes. This API uses a promise to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key     | string                                  | Yes  | Unique query key of a contact, which is a unique identifier automatically generated by the system when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).                      |
| holder  | [Holder](#holder)                       | No  | Contact application information. If this parameter is not passed, the system contact application is used for query by default.      |
| attrs   | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.          |

**Return Value**

| Type                              | Description                                 |
| ---------------------------------- | ------------------------------------- |
| Promise&lt;[Contact](#contact)&gt; | Promise used to return the result, which is the queried contact.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified key, holder, and attributes. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContact](#contactquerycontact10-4) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type                                   | Mandatory| Description                                  |
| ------ | --------------------------------------- | ---- | -------------------------------------- |
| key    | string                                  | Yes  | Unique query key of a contact, which is a unique identifier automatically generated when a contact is created. One contact corresponds to one key, which can be obtained through [queryKey](#contactquerykey10).|
| holder | [Holder](#holder)                       | No  | Contact application information. If this parameter is not passed, the system contact application is used for query by default.               |
| attrs  | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.                   |

**Return Value**

| Type                              | Description                                 |
| ---------------------------------- | ------------------------------------- |
| Promise&lt;[Contact](#contact)&gt; | Promise used to return the result, which is the queried contact.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Asynchronous callback used to query contacts.
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

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContacts](#contactquerycontacts10) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Asynchronous callback used to query contacts.
  contact.queryContacts((err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>10+</sup>

queryContacts(context: Context,  holder: Holder, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts based on the specified holder. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| holder   | [Holder](#holder)                                     | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                      |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries all contacts based on the specified holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContacts](#contactquerycontacts10-1) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| holder   | [Holder](#holder)                                     | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                      |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Asynchronous callback used to query contacts.
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

queryContacts(context: Context,  attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts based on the specified attributes. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries all contacts based on the specified attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContacts](#contactquerycontacts10-2) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Asynchronous callback used to query contacts.
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

Queries all contacts based on the specified holder and attributes. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| holder   | [Holder](#holder)                                     | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                      |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries all contacts based on the specified holder and attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContacts](#contactquerycontacts10-3) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| holder   | [Holder](#holder)                                     | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                       |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Asynchronous callback used to query contacts.
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

Queries all contacts based on the specified holder and attributes. This API uses a promise to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| holder  | [Holder](#holder)                       | No  | Contact application information. If this parameter is empty, the system contact application is used for query by default.      |
| attrs   | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.              |

**Return Value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries all contacts based on the specified holder and attributes. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContacts](#contactquerycontacts10-4) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type                                   | Mandatory| Description                  |
| ------ | --------------------------------------- | ---- | ---------------------- |
| holder | [Holder](#holder)                       | No  | Contact application information. If this parameter is not passed, the system contact application is used for query by default.|
| attrs  | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.    |

**Return Value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

**Example**

```js
  import { contact } from '@kit.ContactsKit';

  // Query all contacts based on the specified holder and attributes.
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

Queries a contact based on the specified phone number. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                                | Yes  | Phone number of a contact. Only full match is supported, and wildcards are not supported.             |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Internal error. The query resultSet is nullptr. 3.Internal error. The query resultSet is empty.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified phone number. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| phoneNumber | string                                                | Yes  | Phone number of a contact. Only full match is supported, and wildcards are not supported.             |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query a contact based on the phone number 138xxxxxxxx.
  contact.queryContactsByPhoneNumber('138xxxxxxxx', (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>10+</sup>

queryContactsByPhoneNumber(context: Context,  phoneNumber: string, holder: Holder, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries a contact based on the specified phone number and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                                | Yes  | Phone number of a contact. Only full match is supported, and wildcards are not supported.                  |
| holder      | [Holder](#holder)                                     | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                       |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Internal error. The query resultSet is nullptr. 3.Internal error. The query resultSet is empty.   |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified phone number and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-1) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| phoneNumber | string                                                | Yes  | Phone number of a contact. Only full match is supported, and wildcards are not supported.                       |
| holder      | [Holder](#holder)                                     | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                       |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query a contact based on the phone number 138xxxxxxxx and the holder ID.
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

Queries a contact based on the specified phone number and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                                | Yes  | Phone number of a contact. Only full match is supported, and wildcards are not supported.                 |
| attrs       | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                         |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Internal error. The query resultSet is nullptr. 3.Internal error. The query resultSet is empty.   |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified phone number and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-2) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| phoneNumber | string                                                | Yes  | Phone number of a contact. Only full match is supported, and wildcards are not supported.                   |
| attrs       | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

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

Queries a contact based on the specified phone number, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                                | Yes  | Phone number of a contact. Only full match is supported, and wildcards are not supported.                     |
| holder      | [Holder](#holder)                                     | Yes  | Contact application information. If this parameter is empty, the system contact application is used for query by default.                                       |
| attrs       | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Internal error. The query resultSet is nullptr. 3.Internal error. The query resultSet is empty.   |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified phone number, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-3) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| phoneNumber | string                                                | Yes  | Phone number of a contact. Only full match is supported, and wildcards are not supported.                   |
| holder      | [Holder](#holder)                                     | Yes  | Contact application information. If this parameter is empty, the system contact application is used for query by default.                                       |
| attrs       | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields of the contact are queried.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

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

Queries a contact based on the specified phone number, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                   | Mandatory| Description                                                        |
| ----------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                  | Yes  | Phone number of a contact. Only full match is supported, and wildcards are not supported.                     |
| holder      | [Holder](#holder)                       | No  | Contact application information. If this parameter is not passed, the system contact application is used for query by default.      |
| attrs       | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.              |

**Return Value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | 1.Parameter error. Possible causes: Mandatory parameters are left unspecified. 2.Internal error. The query resultSet is nullptr. 3.Internal error. The query resultSet is empty.   |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified phone number, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **phoneNumbers** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key. If an application calls this API in the background to obtain contact information, the application must request the corresponding continuous task.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-4) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                   | Mandatory| Description                  |
| ----------- | --------------------------------------- | ---- | ---------------------- |
| phoneNumber | string                                  | Yes  | Phone number of a contact. Only full match is supported, and wildcards are not supported.    |
| holder      | [Holder](#holder)                       | No  | Contact application information. If this parameter is not passed, the system contact application is used for query by default.|
| attrs       | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.    |

**Return Value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

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

Queries a contact based on the specified email. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| email    | string                                                | Yes  | Email address of the contact.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified email. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByEmail](#contactquerycontactsbyemail10) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| email    | string                                                | Yes  | Email address of the contact.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

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

Queries a contact based on the specified email and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| email    | string                                                | Yes  | Email address of the contact.                                          |
| holder   | [Holder](#holder)                                     | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                       |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified email and holder. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByEmail](#contactquerycontactsbyemail10-1) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| email    | string                                                | Yes  | Email address of the contact.                                          |
| holder   | [Holder](#holder)                                     | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                       |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

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

Queries a contact based on the specified email and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| email    | string                                                | Yes  | Email address of the contact.                                          |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified email and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByEmail](#contactquerycontactsbyemail10-2) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| email    | string                                                | Yes  | Email address of the contact.                                          |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

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

Queries a contact based on the specified email, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| email    | string                                                | Yes  | Email address of the contact.                                          |
| holder   | [Holder](#holder)                                     | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                       |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified email, holder, and attributes. This API uses an asynchronous callback to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByEmail](#contactquerycontactsbyemail10-3) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| email    | string                                                | Yes  | Email address of the contact.                                          |
| holder   | [Holder](#holder)                                     | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                      |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the contact is queried successfully, **err** is **undefined** and **data** is an array of queried contacts. Otherwise, **data** is an error object.|

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

Queries a contact based on the specified email, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| email   | string                                  | Yes  | Email address of the contact.                                          |
| holder  | [Holder](#holder)                       | No  | Contact application information. If this parameter is not passed, the system contact application is used for query by default.                                      |
| attrs   | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.                                          |

**Return Value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries a contact based on the specified email, holder, and attributes. This API uses a promise to return the result. The return result of this API includes only the **id**, **key**, and **Emails** attributes. If you want to query all information about a contact, you are advised to call [queryContact](#contactquerycontact10-3) to query the contact based on the specified key.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByEmail](#contactquerycontactsbyemail10-4) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type                                   | Mandatory| Description                  |
| ------ | --------------------------------------- | ---- | ---------------------- |
| email  | string                                  | Yes  | Email address of the contact.    |
| holder | [Holder](#holder)                       | No  | Contact application information. If this parameter is not passed, the system contact application is used for query by default.|
| attrs  | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.    |

**Return Value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

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

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                        |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                           | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the contact group is queried successfully, **err** is **undefined** and **data** is an array of queried groups. Otherwise, **data** is an error object.|

**Error codes**

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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
> This API is supported since API version 7 and deprecated since API version 10. Use [queryGroups](#contactquerygroups10) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                        |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the contact group is queried successfully, **err** is **undefined** and **data** is an array of queried groups. Otherwise, **data** is an error object.|

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

queryGroups(context: Context,  holder: Holder, callback: AsyncCallback&lt;Array&lt;Group&gt;&gt;): void

Queries all groups of a contact based on the specified holder. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                        |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                           | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| holder   | [Holder](#holder)                                 | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                      |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the contact group is queried successfully, **err** is **undefined** and **data** is an array of queried groups. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries all groups of a contact based on the specified holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryGroups](#contactquerygroups10-1) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                        |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| holder   | [Holder](#holder)                                 | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query by default.                                       |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the contact group is queried successfully, **err** is **undefined** and **data** is an array of queried groups. Otherwise, **data** is an error object.|

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

Queries all groups of a contact based on the specified holder. This API uses a promise to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type             | Mandatory| Description                                                        |
| ------- | ----------------- | ---- | ------------------------------------------------------------ |
| context | Context           | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| holder  | [Holder](#holder) | No  | Contact application information. If this parameter is not passed, the system contact application is used for query by default.                                      |

**Return Value**

| Type                                       | Description                                   |
| ------------------------------------------- | --------------------------------------- |
| Promise&lt;Array&lt;[Group](#group)&gt;&gt; | Promise used to return the result, which is an array of groups.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { common } from '@kit.AbilityKit';
  import { contact } from '@kit.ContactsKit';

  // Obtain the context within the component.
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

Queries all groups of a contact based on the specified holder. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryGroups](#contactquerygroups10-2) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type             | Mandatory| Description                  |
| ------ | ----------------- | ---- | ---------------------- |
| holder | [Holder](#holder) | No  | Contact application information. If this parameter is not passed, the system contact application is used for query by default.|

**Return Value**

| Type                                       | Description                                   |
| ------------------------------------------- | --------------------------------------- |
| Promise&lt;Array&lt;[Group](#group)&gt;&gt; | Promise used to return the result, which is an array of groups.|

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

Queries all applications that have created contacts. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                               | Mandatory| Description                                                        |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                             | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| callback | AsyncCallback&lt;Array&lt;[Holder](#holder)&gt;&gt; | Yes  | Callback used to return the result. If the application that creates the contact is queried successfully, **err** is **undefined** and **data** is an array of contacts created by the application. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries all applications that have created contacts. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryHolders](#contactqueryholders10) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                               | Mandatory| Description                                                        |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Holder](#holder)&gt;&gt; | Yes  | Callback used to return the result. If the application that creates the contact is queried successfully, **err** is **undefined** and **data** is an array of contacts created by the application. Otherwise, **data** is an error object.|

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

Queries all applications that have created contacts. This API uses a promise to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type   | Mandatory| Description                                                        |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|

**Return Value**

| Type                                         | Description                                                   |
| --------------------------------------------- | ------------------------------------------------------- |
| Promise&lt;Array&lt;[Holder](#holder)&gt;&gt; | Promise used to return the result, which is an array of queried applications.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { common } from '@kit.AbilityKit';
  import { contact } from '@kit.ContactsKit';

  // Obtain the context within the component.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryHolders(context);
  promise.then((data) => {
    console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryHolders<sup>(deprecated)</sup>

queryHolders(): Promise&lt;Array&lt;Holder&gt;&gt;

Queries all applications that have created contacts. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryHolders](#contactqueryholders10-1) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Return Value**

| Type                                         | Description                                                   |
| --------------------------------------------- | ------------------------------------------------------- |
| Promise&lt;Array&lt;[Holder](#holder)&gt;&gt; | Promise used to return the result, which is an array of queried applications.|

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

Queries the key of a contact based on the specified contact ID. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                       | Mandatory| Description                                                        |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                     | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| id       | number                      | Yes  | Contact ID, which uniquely identifies a contact in the database.                                        |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the contact key is queried successfully, **err** is **undefined** and **data** is the key of the contact. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries the key of a contact based on the specified contact ID. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryKey](#contactquerykey10) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                       | Mandatory| Description                                                        |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| id       | number                      | Yes  | Contact ID.                                        |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the contact key is queried successfully, **err** is **undefined** and **data** is the key of the contact. Otherwise, **data** is an error object.|

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

Queries the key of a contact based on the specified contact ID and holder. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                       | Mandatory| Description                                                        |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                     | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| id       | number                      | Yes  | Contact ID.                                        |
| holder   | [Holder](#holder)           | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query.                                       |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the contact key is queried successfully, **err** is **undefined** and **data** is the key of the contact. Otherwise, **data** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context within the component.
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

Queries the key of a contact based on the specified contact ID and holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryKey](#contactquerykey10-1) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                       | Mandatory| Description                                                        |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| id       | number                      | Yes  | Contact ID.                                        |
| holder   | [Holder](#holder)           | Yes  | Contact application information. If the input parameter is empty, the system contact application is used for query.                                       |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the contact key is queried successfully, **err** is **undefined** and **data** is the key of the contact. Otherwise, **data** is an error object.|

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

Queries the key of a contact based on the specified contact ID and holder. This API uses a promise to return the result.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type             | Mandatory| Description                                                        |
| ------- | ----------------- | ---- | ------------------------------------------------------------ |
| context | Context           | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| id      | number            | Yes  | Contact ID.                                        |
| holder  | [Holder](#holder) | No  | Contact application information. If this parameter is not passed, the system contact application is used for query.                                      |

**Return Value**

| Type                 | Description                                      |
| --------------------- | ------------------------------------------ |
| Promise&lt;string&gt; | Promise used to return the result, which is the key of the queried contact.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.  |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

  ```js
  import { common } from '@kit.AbilityKit';
  import { contact } from '@kit.ContactsKit';

  // Obtain the context within the component.
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

Queries the key of a contact based on the specified contact ID and holder. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryKey](#contactquerykey10-2) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type             | Mandatory| Description                  |
| ------ | ----------------- | ---- | ---------------------- |
| id     | number            | Yes  | Contact ID.  |
| holder | [Holder](#holder) | No  | Contact application information. If this parameter is not passed, the system contact application is used for query.|

**Return Value**

| Type                 | Description                                      |
| --------------------- | ------------------------------------------ |
| Promise&lt;string&gt; | Promise used to return the result, which is the key of the queried contact.|

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

Queries the number of all contacts. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 22.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type             | Mandatory| Description                  |
| ------ | ----------------- | ---- | ---------------------- |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)          | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).  |

**Return Value**

| Type                 | Description                                      |
| --------------------- | ------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the result, which is the number of queried contacts.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// Obtain the context within the component.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.queryContactsCount(context);
promise.then((data) => {
  console.info(`Succeeded in querying ContactsCount. data->${JSON.stringify(data)}`);
});
```

## contact.addContactViaUI<sup>15+</sup>

addContactViaUI(context: Context, contact: Contact): Promise&lt;number&gt;

Opens the **Add contact** page to add a contact. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name| Type             | Mandatory| Description                  |
| ------ | ----------------- | ---- | ---------------------- |
| context | Context          | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).  |
| contact | [Contact](#contact) | Yes  | Contact information.|

**Return Value**

| Type                 | Description                                      |
| --------------------- | ------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the ID of the added contact, which is the unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one ID.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID                | Error Message                                      |
| --------------------- | ------------------------------------------ |
| 401       | Parameter error. Possible causes: Mandatory parameters are left unspecified. |
| 801       | The specified SystemCapability name was not found. |
| 16700001       | General error. |
| 16700102       | Failed to set value to contacts data. |
| 16700103       | User cancel. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// Obtain the context within the component.
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

Opens the **Save to existing** page to save a contact to an existing one. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name| Type             | Mandatory| Description                  |
| ------ | ----------------- | ---- | ---------------------- |
| context | Context          | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).  |
| contact | [Contact](#contact) | Yes  | Contact information.|

**Return Value**

| Type                 | Description                                      |
| --------------------- | ------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the result, which is the contact ID.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID                | Error Message                                      |
| --------------------- | ------------------------------------------ |
| 401       | Parameter error. Possible causes: Mandatory parameters are left unspecified. |
| 801       | The specified SystemCapability name was not found. |
| 16700001       | General error. |
| 16700101       | Failed to get value from contacts data. |
| 16700102       | Failed to set value to contacts data. |
| 16700103       | User cancel. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// Obtain the context within the component.
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

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| contacts | Array&lt;[Contact](#contact)&gt; | Yes  | Contact information array.                                                |

**Return Value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the result, which is the ID array of the contacts added in batches.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |
| 16700002      | Invalid parameter value. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

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
// Obtain the context within the component.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
contact.addContacts(context, [contactInfo1, contactInfo2]).then((data) => {
  console.info(`Succeeded in addContacts.data->${JSON.stringify(data)}`);
});
```

## contact.hasMatchedCallLog<sup>24+</sup>

hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: number, withinTime: number): Promise&lt;boolean&gt;

Checks whether there are call records that meet the specified conditions. This API applies only to carrier calls. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 24.

**Required permissions**: ohos.permission.CHECK_CALL_LOG

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                  | Yes  | Phone number of the contacts.                                          |
| minDuration      | number                      | Yes  | Minimum call duration, in seconds. The value must be greater than 0.       |
| withinTime       | number | Yes  | Period of time that the start time and end time of calls should be within, in seconds. This period starts from the current time. The time range for the query must be greater than 0 and cannot exceed 6 hours. If the time range exceeds 6 hours, calls within 6 hours are queried.              |

**Return Value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result of whether there are call records that meet the specified conditions. The value **true** indicates that there are such records, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |
| 16700002      | Invalid parameter value. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context within the component.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;

const phoneNumber = '138xxxxxxxx';
const minDuration = 60;
const withinTime = 2 * 60 *60;

// Call the API.
contact.hasMatchedCallLog(context, phoneNumber, minDuration, withinTime).then((hasMatch:boolean) => {
  console.info(`Has matched call log: ${hasMatch}`);
});
```

## contact.hasMatchedCallLog<sup>24+</sup>

hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: number): Promise&lt;boolean&gt;

Checks whether there are call records that meet the specified conditions. By default, call records within the last 6 hours are queried. This API applies only to carrier calls. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 24.

**Required permissions**: ohos.permission.CHECK_CALL_LOG

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                  | Yes  | Phone number of the contacts.                                          |
| minDuration      | number                      | Yes  | Minimum call duration, in seconds. The value must be greater than 0.      |

**Return Value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result of whether there are call records that meet the specified conditions. The value **true** indicates that there are such records, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |
| 16700002      | Invalid parameter value. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context within the component.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;

const phoneNumber = '138xxxxxxxx';
const minDuration = 60;
// Call the API to query call records. By default, call records within the last 6 hours are queried.
contact.hasMatchedCallLog(context, phoneNumber, minDuration).then((hasMatch:boolean) => {
  console.info(`Has matched call log: ${hasMatch}`);
});
```

## contact.syncContacts

syncContacts(context: Context, mode: ContactSyncMode, progress: ContactSyncProgress, contacts: Array&lt;Contact&gt;): Promise&lt;Array&lt;number&gt;&gt;

Synchronizes multiple contacts to the contacts database in batches. A maximum of 400 contacts can be synchronized at a time. Synchronizes contacts from a third-party application to the local device. The caller must be running in the foreground.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| mode | [ContactSyncMode](#contactsyncmode)                                  | Yes  | Contact synchronization mode.                                          |
| progress      | [ContactSyncProgress](#contactsyncprogress)                       | Yes  | Contact synchronization mode.      |
| contacts      | Array&lt;[Contact](#contact)&gt;                      | Yes  | Array of contacts to be synchronized to the database.      |

**Return Value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;number&gt; | Promise used to return the array of contacts created. A valid contact ID indicates that the contact is created successfully.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |
| 16700002      | Invalid parameter value. |
| 16700003      | Background usage is prohibited. |
| 16700004      | The number of contacts exceeds the limit. |
| 16700103      | User canceled. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

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
          fullName: `Synchronizing contacts ${i + 1}_${batch} batch`
          },
        phoneNumbers: [{
          phoneNumber: `1380000${String(i + 1).padStart(4, '0')}`,
          labelName: 'Mobile Phone'
        }],
        emails: [{
          email: `contact${i + 1}@example.com`,
          labelName: 'Work'
          }]
        };
      contacts.push(contactData);
    }
    const progress: ContactSyncProgress = {
      syncId: syncId,
      currentBatch: batch,
      totalBatches: totalBatches
    };
    console.info(`Synchronizing batch ${batch}/${totalBatches}, number of contacts: ${currentBatchSize}`);
    let result = await contact.syncContacts(context, mode, progress, contacts);
    console.info(`Batch ${batch} synchronized successfully, result: `  + JSON.stringify(result));
  }
  catch (err) {
    const e = err as BusinessError;
    console.error(`syncContacts failed: code=${e.code}, message=${e.message}`);
  }
}
```

## contact.queryContactSyncInfo

queryContactSyncInfo(context: Context): Promise&lt;Array&lt;ContactSyncInfo&gt;&gt;

Queries the contact information synchronization status of the application. If an empty value is returned, the application does not initiate synchronization or the synchronization is complete.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**Required permissions**: ohos.permission.WRITE_CONTACTS

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|

**Return Value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;Array&lt;[ContactSyncInfo](#contactsyncinfo)&gt;&gt; | Promise used to return an array of contact synchronization information of the calling application. If no contact is being synchronized, **null** is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 16700001      | General error. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context within the component.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
const syncInfoList: ContactSyncInfo[] = await contact.queryContactSyncInfo(context) as ContactSyncInfo[];
console.info('queryContactSyncInfo syncInfoList '  + JSON.stringify(syncInfoList));
```

## contact.importContactsViaUI

importContactsViaUI(context: Context, contacts: Array&lt;Contact&gt;): Promise&lt;Array&lt;number&gt;&gt;

Import multiple contacts in batches through UI interaction. A maximum of 100 contacts can be imported at a time. Contact portraits cannot be imported.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| contacts      | Array&lt;[Contact](#contact)&gt;                      | Yes  | Array of contacts to be imported to the database.      |

**Return Value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the array of contacts created. If the return value in the array is greater than 0, the contact is successfully created. If the return value is **–1**, the contact fails to be created. If the return value is **–2**, the contact is not selected.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Contacts Error Codes](../apis-contacts-kit/errorcode-contacts.md).

| ID| Error Message          |
| -------- | ------------------ |
| 801       | The specified SystemCapability name was not found. |
| 16700001      | General error. |
| 16700002      | Invalid parameter value. |
| 16700004      | The number of contacts exceeds the limit. |
| 16700103      | User canceled. |

**Example**

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context within the component.
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

Defines the contact selection options.

**System capability**: SystemCapability.Applications.Contacts

|                Name              |                  Type                | Read-Only | Optional |        Description     |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| isMultiSelect<sup>10+</sup>         | boolean | No  | Yes  | Whether multiple contacts can be selected. The value **true** indicates that multiple contacts can be selected, and the value **false** indicates that only one contact can be selected. The default value is **false**. **Atomic service API**: This API can be used in atomic services since API version 11.    |
| maxSelectable<sup>15+</sup>         | number | No  | Yes  | Maximum number of contacts. The default value is **10000**. If the value exceeds the maximum number, the default value is used. **Atomic service API**: This API can be used in atomic services since API version 15.    | 
| isDisplayedByName<sup>15+</sup>         | boolean | No  | Yes  | Whether to display contacts by name. The value **true** indicates that contacts are displayed by name, and the value **false** indicates that contacts are displayed by number. The default value is **false**. **Atomic service API**: This API can be used in atomic services since API version 15.    |
| filter<sup>15+</sup>         | [ContactSelectionFilter](#contactselectionfilter15) | No  | Yes  | Contact selection filter. **Atomic service API**: This API can be used in atomic services since API version 15.    | 
| isAutoDismissOnNavigation        | boolean | No  | Yes  | Whether the picker can be automatically dismissed during route changes on the page where the picker is triggered. The value **true** indicates that the picker can be automatically dismissed, and the value **false** indicates the opposite. The default value is **false**.<br> **Since**: 26.0.0<br> **Atomic service API**: This API can be used in atomic services since API version 26.<br> **Model restriction**: This API can be used only in the stage model.    |

## ContactSelectionFilter<sup>15+</sup>

Describes the contact selection filter.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

|                Name              |                  Type                |  Read-Only | Optional   |        Description     |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| filterClause        | [FilterClause](#filterclause15) |  No |  No  |  Filter criteria.    |
| filterType        | [FilterType](#filtertype15) |  No |  No   | Filter type.    |

## FilterType<sup>15+</sup>

Enumerates contact filter types.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.ContactsData

| Name                 | Value| Description                              |
| --------------------- | ---- | ---------------------------------- |
| SHOW_FILTER    | 0 | Shows only contacts that meet the filter criteria.<br>**System capability**: SystemCapability.Applications.Contacts|
| DEFAULT_SELECT            | 1 | Selects contacts that meet the filter criteria by default.<br>**System capability**: SystemCapability.Applications.Contacts                |
| SHOW_FILTER_AND_DEFAULT_SELECT | 2 | Shows only contacts that meet the filter criteria and selects these contacts by default.<br>**System capability**: SystemCapability.Applications.Contacts                    |

## FilterClause<sup>15+</sup>

Defines the contact filter criteria. Multiple filter criteria are ORed. If the parameter is an array, the array can contain a maximum of three elements.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

|                Name              |                  Type                |   Read-Only | Optional    |        Description     |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| id         | Array\<[FilterOptions](#filteroptions15)> | No  | Yes  | Contact ID.    |
| name         | Array\<[FilterOptions](#filteroptions15)>  | No  | Yes  | Contact name.    |
| dataItem         | [DataFilter](#datafilter15) | No  | Yes  | Contact data filter item.    |
| focusModeList        | Array\<[FilterOptions](#filteroptions15)>  | No  | Yes  | Focus mode list.    |

## FilterOptions<sup>15+</sup>

Defines contact filter options.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

|                Name              |                  Type                |  Read-Only | Optional   |        Description     |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| filterCondition         | [FilterCondition](#filtercondition15) | No   |   No  | Filter criteria.    |
| value        | string \| ValueType[] |  No   |   Yes  | Filter value. The default value is **undefined**.    |

## FilterCondition<sup>15+</sup>

Enumerates filter criteria.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.ContactsData

| Name                 | Value| Description                              |
| --------------------- | ---- | ---------------------------------- |
| IS_NOT_NULL    | 0 | The corresponding field is not empty.<br>**System capability**: SystemCapability.Applications.Contacts|
| EQUAL_TO            | 1 | The corresponding field is equal to a value. The value type is string.<br>**System capability**: SystemCapability.Applications.Contacts|
| NOT_EQUAL_TO | 2 | The corresponding field is not equal to a value.<br>**System capability**: SystemCapability.Applications.Contacts|
| IN | 3 | The value of the corresponding field is in an array. The value type is string.<br>**System capability**: SystemCapability.Applications.Contacts|
| NOT_IN | 4 | The value of the corresponding field is not in an array.<br>**System capability**: SystemCapability.Applications.Contacts |
| CONTAINS | 5 | The value of the corresponding field contains a certain value. The value type is string.<br>**System capability**: SystemCapability.Applications.Contacts|

## DataFilter<sup>15+</sup>

Defines the contact data filter item.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

|                Name              |                  Type                |  Read-Only | Optional  |        Description     |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| field         | [DataField](#datafield15) | No | No | Contact data field.    |
| options         | Array\<[FilterOptions](#filteroptions15)> | No | No | Contact filtering parameter. Multiple filter options in the array are ORed. The maximum length of the array is 3.    |

## DataField<sup>15+</sup>

Enumerates contact data fields.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.ContactsData

| Name                 | Value| Description                              |
| --------------------- | --- | ---------------------------------- |
| EMAIL    | 0 | Email of the contact.<br>**System capability**: SystemCapability.Applications.Contacts|
| PHONE            | 1 | Phone number of the contact.<br>**System capability**: SystemCapability.Applications.Contacts|
| ORGANIZATION | 2 | Organization of the contact.<br>**System capability**: SystemCapability.Applications.Contacts|

## Contact

Defines a contact.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData


|       Name       |                   Type                 | Read-Only| Optional| Description                                  |
| ----------------- | --------------------------------------- | ---- | ---- | -------------------------------------- |
| INVALID_CONTACT_ID | number                                 | Yes  | No   | Default contact ID. The value is **–1**.                          |
| id                | number                                  | Yes  | Yes   | Contact ID, which is automatically generated by the system.                          |
| key               | string                                  | Yes  | Yes  | Contact key, which is automatically generated by the system.              |
| contactAttributes | [ContactAttributes](#contactattributes) | No  | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                    |
| emails            | [Email](#email)[]                       | No  | Yes  | List of email addresses of the contact.                |
| events            | [Event](#event)[]                       | No  | Yes  | List of important dates such as birthdays and anniversaries of the contact.|
| groups            | [Group](#group)[]                       | No  | Yes  | List of groups of the contact.                    |
| imAddresses       | [ImAddress](#imaddress)[]               | No  | Yes  | List of instant message addresses of the contact.            |
| phoneNumbers      | [PhoneNumber](#phonenumber)[]           | No  | Yes  | List of phone numbers of the contact.                |
| portrait          | [Portrait](#portrait)                   | No  | Yes  | Contact portrait.                        |
| postalAddresses   | [PostalAddress](#postaladdress)[]       | No  | Yes  | List of postal addresses of the contact.                |
| relations         | [Relation](#relation)[]                 | No  | Yes  | List of relationships with the contact.                    |
| sipAddresses      | [SipAddress](#sipaddress)[]             | No  | Yes  | List of Session Initiation Protocol (SIP) addresses of the contact. |
| websites          | [Website](#website)[]                   | No  | Yes  | List of websites of the contact.                    |
| name              | [Name](#name)                           | No  | Yes  | Contact name.                        |
| nickName          | [NickName](#nickname)                   | No  | Yes  | Contact nickname.                        |
| note              | [Note](#note)                           | No  | Yes  | Contact notes.                        |
| organization      | [Organization](#organization)           | No  | Yes  | Organization of the contact.                    |

**Example**

Create contact data in JSON format:

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

Provides a list of contact attributes, which are generally used as arguments. 

If **null** is passed, all attributes are queried by default.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name      |            Type          | Read-Only| Optional| Description            |
| ---------- | ------------------------- | ---- | ---- | ---------------- |
| attributes | [Attribute](#attribute)[] | No  | No  | List of contact attributes.|

**Example**

Create contact data in JSON format:

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

Enumerates contact attributes. The enumerated value is of the number type. List of contact attributes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name                 | Value| Description                              |
| --------------------- | ---- | ---------------------------------- |
| ATTR_CONTACT_EVENT    | 0 | Important dates such as birthday and anniversaries of the contact.|
| ATTR_EMAIL            | 1 | Email address of the contact.                |
| ATTR_GROUP_MEMBERSHIP | 2 | Groups of the contact.                    |
| ATTR_IM               | 3 | IM addresses of the contact.            |
| ATTR_NAME             | 4 | Contact name.                    |
| ATTR_NICKNAME         | 5 | Contact nickname.                    |
| ATTR_NOTE             | 6 | Contact notes.                    |
| ATTR_ORGANIZATION     | 7 | Organization of the contact.                |
| ATTR_PHONE            | 8 | Phone number of the contacts.                |
| ATTR_PORTRAIT         | 9 | Contact portrait.                    |
| ATTR_POSTAL_ADDRESS   | 10 | Postal address of the contact.                |
| ATTR_RELATION         | 11 | Relationship with the contact.                    |
| ATTR_SIP_ADDRESS      | 12 | SIP addresses of the contact. |
| ATTR_WEBSITE          | 13 | Website that stores the contact information.                    |

**Example**

Create contact data in JSON format:

```js
let attributes = [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE];
```

## Email

Defines a contact's email.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name       |   Type  | Read-Only| Optional| Description            |
| ----------- | -------- | ---- | ---- | ---------------- |
| CUSTOM_LABEL     | number    | Yes  | No  |Custom email. The default value is **0**.|
| EMAIL_HOME       | number    | Yes  | No  | Home email. The default value is **1**.  |
| EMAIL_WORK       | number    | Yes  | No  | Work email. The default value is **2**.  |
| EMAIL_OTHER      | number    | Yes  | No  | Other email type. The default value is **3**.  |
| INVALID_LABEL_ID | number    | Yes  | No  | Invalid email type. The default value is **–1**.  |
| email       | string   | No  | No  | Email addresses      |
| labelName   | string   | No  | Yes  | Name of the mailbox type.|
| displayName | string   | No  | Yes  | Displayed name of the mailbox.|
| labelId     | number   | No  | Yes  | Mailbox type.    |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let email: contact.Email = {
    email: 'xxx@email.com',
    displayName: 'displayName'
}
```


  Or, create data by configuring an **Email** object.

```js
let email = new contact.Email();
email.email = 'xxx@email.com';
```

## Holder

Defines an application that creates the contact.

**System capability**: SystemCapability.Applications.ContactsData

| Name       | Type  | Read-Only| Optional| Description        |
| ----------- | ------ | ---- | ---- | ------------ |
| bundleName  | string | Yes  | No  | Bundle name. The default value is **com.ohos.contacts**.|
| displayName | string | Yes  | Yes  | Application name. The default value is empty.  |
| holderId    | number | No  | Yes  | Application ID. The default value is empty.   |

**Example**

  Create contact data in JSON format:

```js
let holder: contact.Holder = {
  bundleName: 'com.ohos.contacts',
  displayName: 'displayName',
  holderId: 1
};
```

## Event

Defines a contact's event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

|    Name  |   Type  | Read-Only| Optional| Description          |
| --------- | -------- | ---- | ---- | -------------- |
| CUSTOM_LABEL      | number   | Yes  | No  | Custom event. The default value is **0**.  |
| EVENT_ANNIVERSARY | number   | Yes  | No  | Anniversary event. The default value is **1**.|
| EVENT_OTHER       | number   | Yes  | No  | Other event type. The default value is **2**.    |
| EVENT_BIRTHDAY    | number   | Yes  | No  | Birthday event. The default value is **3**.    |
| INVALID_LABEL_ID  | number   | Yes  | No  | Invalid event type. The default value is **–1**.    |
| eventDate | string   | No  | No  | Event date.  |
| labelName | string   | No  | Yes  | Event type.|
| labelId   | number   | No  | Yes  | Event type.    |

**Example**

  Create contact data in JSON format:

```js
let event: contact.Event = {
    eventDate: '2000-01-01'
};
```

  Or, create data by configuring an **Event** object.

```js
let event = new contact.Event();
event.eventDate = '2000-01-01';
```

## Group

Defines a contact group.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name   |   Type  | Read-Only| Optional| Description              |
| ------- | -------- | ---- | ---- | ------------------ |
| groupId | number   | No  | Yes  | ID of a contact group.  |
| title   | string   | No  | No  | Name of a contact group.|

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let group: contact.Group = {
    groupId: 1,
    title: 'title'
};
```

## ImAddress

Enumerates IM addresses.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name     |   Type  | Read-Only| Optional| Description              |
| --------- | -------- | ---- | ---- | ------------------ |
| CUSTOM_LABEL     | number   | Yes  | No  | Custom IM. The default value is **–1**.|
| IM_AIM           | number   | Yes  | No  | AIM. The default value is **0**.   |
| IM_MSN           | number   | Yes  | No  | MSN. The default value is **1**.   |
| IM_YAHOO         | number   | Yes  | No  | YAHOO. The default value is **2**. |
| IM_SKYPE         | number   | Yes  | No  | SKYPE. The default value is **3**. |
| IM_QQ            | number   | Yes  | No  | QQ. The default value is **4**.    |
| IM_ICQ           | number   | Yes  | No  | ICQ. The default value is **6**.   |
| IM_JABBER        | number   | Yes  | No  | JABBER. The default value is **7**.|
| INVALID_LABEL_ID | number   | Yes  | No  | Invalid IM type. The default value is **–2**.|
| imAddress | string   | No  | No  | IM address.    |
| labelName | string   | No  | Yes  | IM name.|
| labelId   | number   | No  | Yes  | IM ID.    |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let imAddress: contact.ImAddress = {
    imAddress: 'imAddress',
    labelName: 'labelName'
};
```


  Or, create data by configuring an **ImAddress** object.

```js
let imAddress = new contact.ImAddress();
imAddress.imAddress = 'imAddress';
```

## Name

Defines a contact's name.

**System capability**: SystemCapability.Applications.ContactsData

| Name              |   Type  | Read-Only| Optional| Description                       |
| ------------------ | -------- | ---- | ---- | --------------------------- |
| familyName         | string   | No  | Yes  | Family name. **Atomic service API**: This API can be used in atomic services since API version 11.         |
| familyNamePhonetic | string   | No  | Yes  | Family name in pinyin. **Atomic service API**: This API can be used in atomic services since API version 11.     |
| fullName           | string   | No  | No  | Full name of the contact. **Atomic service API**: This API can be used in atomic services since API version 11.             |
| givenName          | string   | No  | Yes  | Given name of the contact. **Atomic service API**: This API can be used in atomic services since API version 11.|
| givenNamePhonetic  | string   | No  | Yes  | Given name of the contact in pinyin. **Atomic service API**: This API can be used in atomic services since API version 11.         |
| middleName         | string   | No  | Yes  | Middle name of the contact. **Atomic service API**: This API can be used in atomic services since API version 11.           |
| middleNamePhonetic | string   | No  | Yes  | Middle name of the contact in pinyin. **Atomic service API**: This API can be used in atomic services since API version 11.       |
| namePrefix         | string   | No  | Yes  | Prefix of the contact name. **Atomic service API**: This API can be used in atomic services since API version 11.         |
| nameSuffix         | string   | No  | Yes  | Suffix of the contact name. **Atomic service API**: This API can be used in atomic services since API version 11.         |
| hasName<sup>22+</sup>            | boolean  | No  | Yes  | Whether the contact information contains the name. The value **true** indicates that the contact information contains the name, and the value **false** indicates the opposite. **Atomic service API**: This API can be used in atomic services since API version 22.         |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let name: contact.Name = {
    familyName: 'familyName',
    fullName: 'fullName'
};
```

## NickName

Defines a contact's nickname.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name    |   Type  | Read-Only| Optional| Description          |
| -------- | -------- | ---- | ---- | -------------- |
| nickName | string   | No  | No  | Contact nickname.|

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let nickName: contact.NickName = {
    nickName: 'nickName'
};
```

## Note

Defines a contact's note.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name       |   Type  | Read-Only| Optional| Description              |
| ----------- | -------- | ---- | ---- | ------------------ |
| noteContent | string   | No  | No  | Notes of the contact.|

**Example**

  Create contact data in JSON format:

```js
let note: contact.Note = {
    noteContent: 'noteContent'
};
```

## Organization

Defines a contact's organization.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name |   Type  | Read-Only| Optional| Description      |
| ----- | -------- | ---- | ---- | ---------- |
| name  | string   | No  | No  | Organization name.|
| title | string   | No  | Yes  | Job title.|

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let organization: contact.Organization = {
    name: 'name',
    title: 'title'
};
```

## PhoneNumber

Defines a contact's phone number.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData


| Name            |  Type | Read-Only | Optional | Description                                            |
| ---------------- | ---- | ---- | ---- | ------------------------------------------------ |
| CUSTOM_LABEL     |  number  | Yes  | No  | Custom phone. The default value is **0**.                                |
| NUM_HOME         |  number  | Yes  | No  | Home phone. The default value is **1**.                                  |
| NUM_MOBILE       |  number  | Yes  | No  | Mobile phone. The default value is **2**.                                  |
| NUM_WORK         |  number  | Yes  | No  | Work phone. The default value is **3**.                                  |
| NUM_FAX_WORK     |  number  | Yes  | No  | Work fax. The default value is **4**.                              |
| NUM_FAX_HOME     |  number  | Yes  | No  | Family fax. The default value is **5**.                              |
| NUM_PAGER        |  number  | Yes  | No  | Pager. The default value is **6**.                                |
| NUM_OTHER        |  number  | Yes  | No  | Other phone type. The default value is **7**.                                  |
| NUM_CALLBACK     |  number  | Yes  | No  | Callback phone. The default value is **8**.                                  |
| NUM_CAR          |  number  | Yes  | No  | Car phone. The default value is **9**.                                  |
| NUM_COMPANY_MAIN |  number  | Yes  | No  | Company phone. The default value is **10**.                                  |
| NUM_ISDN         |  number  | Yes  | No  | Integrated Services Digital Network (ISDN) phone. The default value is **11**.                |
| NUM_MAIN         |  number  | Yes  | No  | Main phone. The default value is **12**.                                    |
| NUM_OTHER_FAX    |  number  | Yes  | No  | Other fax phone. The default value is **13**.                                  |
| NUM_RADIO        |  number  | Yes  | No  | Wireless phone. The default value is **14**.                                  |
| NUM_TELEX        |  number  | Yes  | No  | Telex phone. The default value is **15**.                                  |
| NUM_TTY_TDD      |  number  | Yes  | No  | Teletypewriter (TTY) or Test Driven Development (TDD) phone. The default value is **16**.|
| NUM_WORK_MOBILE  |  number  | Yes  | No  | Work mobile phone. The default value is **17**.                              |
| NUM_WORK_PAGER   |  number  | Yes  | No  | Work pager. The default value is **18**.                            |
| NUM_ASSISTANT    |  number  | Yes  | No  | Assistant phone. The default value is **19**.                                  |
| NUM_MMS          |  number  | Yes  | No  | MMS phone. The default value is **20**.                                  |
| INVALID_LABEL_ID |  number  | Yes  | No  | Invalid phone type. The default value is **–1**.                                  |
| labelName   | string   | No  | Yes  | Phone number type.|
| phoneNumber | string   | No  | No  | Phone number.        |
| labelId     | number   | No  | Yes  | Phone number type.    |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let phoneNumber: contact.PhoneNumber = {
    phoneNumber: '138xxxxxxxx',
    labelId: contact.PhoneNumber.NUM_HOME
};
```

  Or, create data by configuring a new **PhoneNumber** object.

```js
let phoneNumber = new contact.PhoneNumber();
phoneNumber.phoneNumber = '138xxxxxxxx';
```

## Portrait

Defines a contact's portrait.

> **NOTE**
>
>  Since API version 22, contact portraits can be set in URI or [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) format. (Currently, contact avatars cannot be set through the [addContactViaUI](#contactaddcontactviaui15) or [saveToExistingContactViaUI](#contactsavetoexistingcontactviaui15) API.)<br>
URI indicates the address of the contact portrait file that can be accessed, and [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) indicates the [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) object generated based on the contact portrait resource.<br>
>  Since API version 22, the profile picture resource can be read through URI. The resource can be opened only in **fileIo.open** mode and cannot be directly displayed in the **Image** component using a URI. You need to read the resource and display it in [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) format.

**System capability**: SystemCapability.Applications.ContactsData

| Name|   Type  | Read-Only| Optional| Description          |
| ---- | -------- | ---- | ---- | -------------- |
| uri  | string   | No  | No  | Contact portrait in URI format. **Atomic service API**: This API can be used in atomic services since API version 11.|
| photo<sup>22+</sup>  | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)   | No  | Yes  | Contact portrait in PixelMap format. **Atomic service API**: This API can be used in atomic services since API version 22.|

**Example**

  Create contact data in JSON format:

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

Defines a contact's postal address.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name         |   Type  | Read-Only| Optional| Description                      |
| ------------- | -------- | ---- | ---- | -------------------------- |
| CUSTOM_LABEL     | number   | Yes  | No  | Custom postal address. The default value is **0**.|
| ADDR_HOME        | number   | Yes  | No  | Home address. The default value is **1**.      |
| ADDR_WORK        | number   | Yes  | No  | Work address. The default value is **2**.      |
| ADDR_OTHER       | number   | Yes  | No  | Other address type. The default value is **3**.      |
| INVALID_LABEL_ID | number   | Yes  | No | Invalid address type. The default value is **–1**.      |
| city          | string   | No  | Yes  | City where the contact is located.        |
| country       | string   | No  | Yes  | Country/Region where the contact is located.        |
| labelName     | string   | No  | Yes  | Postal address type.        |
| neighborhood  | string   | No  | Yes  | Neighbor of the contact.            |
| pobox         | string   | No  | Yes  | Email of the contact.            |
| postalAddress | string   | No  | No  | Postal address of the contact.        |
| postcode      | string   | No  | Yes  | Postal code of the region where the contact is located.|
| region        | string   | No  | Yes  | Area where the contact is located.        |
| street        | string   | No  | Yes  | Street where the contact resides.        |
| labelId       | number   | No  | Yes  | Postal address type.            |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let postalAddress: contact.PostalAddress = {
    city: 'city',
    postalAddress: 'postalAddress'
};
```

  Or, create data by configuring a new **PostalAddress** object.

```js
import { contact } from '@kit.ContactsKit';

let postalAddress = new contact.PostalAddress();
postalAddress.city = 'city';
postalAddress.postalAddress = 'postalAddress';
```

## Relation

Defines a contact's relationship.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name                     |  Type  | Read-Only |  Optional | Description              |
| ------------------------- | ---- | ---- | ---- | ------------------ |
| CUSTOM_LABEL              | number   | Yes | No | Custom relationship. The default value is **0**.  |
| RELATION_ASSISTANT        | number   | Yes | No | Assistant. The default value is **1**.    |
| RELATION_BROTHER          | number   | Yes | No | Brother. The default value is **2**.    |
| RELATION_CHILD            | number   | Yes | No | Child. The default value is **3**.    |
| RELATION_DOMESTIC_PARTNER | number   | Yes | No | Domestic partner. The default value is **4**.|
| RELATION_FATHER           | number   | Yes | No | Father. The default value is **5**.    |
| RELATION_FRIEND           | number   | Yes | No | Friend. The default value is **6**.    |
| RELATION_MANAGER          | number   | Yes | No | Manager. The default value is **7**.  |
| RELATION_MOTHER           | number   | Yes | No | Mother. The default value is **8**.    |
| RELATION_PARENT           | number   | Yes | No | Parent. The default value is **9**.    |
| RELATION_PARTNER          | number   | Yes | No| Partner. The default value is **10**.|
| RELATION_REFERRED_BY      | number   | Yes | No| Referrer. The default value is **11**.  |
| RELATION_RELATIVE         | number   | Yes | No| Relative. The default value is **12**.    |
| RELATION_SISTER           | number   | Yes | No| Sister. The default value is **13**.    |
| RELATION_SPOUSE           | number   | Yes | No| Spouse. The default value is **14**.    |
| INVALID_LABEL_ID          | number   | Yes | No| Invalid relationship. The default value is **–1**.  |
| labelName    | string   | No  | Yes  | Relationship type.|
| relationName | string   | No  | No  | Relationship name.    |
| labelId      | number   | No  | Yes  | Relationship type.    |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let relation: contact.Relation = {
    relationName: 'relationName',
    labelId: contact.Relation.RELATION_ASSISTANT
};
```

  Or, create data by configuring a new **Relation** object.

```js
import { contact } from '@kit.ContactsKit';

let relation = new contact.Relation();
relation.relationName = 'relationName';
relation.labelId = contact.Relation.RELATION_ASSISTANT;
```

## SipAddress

Defines a contact's SIP address.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name      |   Type  | Read-Only| Optional| Description                             |
| ---------- | -------- | ---- | ---- | --------------------------------- |
| CUSTOM_LABEL     | number   | Yes  | No   | Custom SIP address. The default value is **0**.|
| SIP_HOME         | number   | Yes  | No   | Home SIP address. The default value is **1**.  |
| SIP_WORK         | number   | Yes  | No   | Work SIP address. The default value is **2**.  |
| SIP_OTHER        | number   | Yes  | No   | Other SIP address. The default value is **3**.  |
| INVALID_LABEL_ID | number   | Yes  | No   | Invalid SIP address. The default value is **–1**.  |
| labelName  | string   | No  | Yes  | SIP address type.|
| sipAddress | string   | No  | No  | SIP address.        |
| labelId    | number   | No  | Yes  | SIP address ID.    |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let sipAddress: contact.SipAddress = {
    sipAddress: 'sipAddress'
};
```

  Or, create data by configuring a new **SipAddress** object.

```js
import { contact } from '@kit.ContactsKit';

let sipAddress = new contact.SipAddress();
sipAddress.sipAddress = 'sipAddress';
```

## Website

Defines a contact's website.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name   |   Type  | Read-Only| Optional| Description              |
| ------- | -------- | ---- | ---- | ------------------ |
| website | string   | No  | No  | Website of the contact.|

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let website: contact.Website = {
    website: 'website'
};
```


## ContactSyncMode

Enumerates the contacts synchronization modes.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**System capability**: SystemCapability.Applications.ContactsData

| Name                 | Value| Description                              |
| --------------------- | ---- | ---------------------------------- |
| MODE_INCREMENTAL    | 1 | Contacts that are different between the cloud and the local device will be inserted or updated in the database.<br>**System capability**: SystemCapability.Applications.Contacts|
| MODE_CLOUD_BASED            | 2 | All local contacts will be replaced by cloud contacts. When the cloud-to-local mode is used for batch synchronization, all local contacts (except third-party contacts) will be deleted during the first batch synchronization.<br>**System capability**: SystemCapability.Applications.Contacts                |

## ContactSyncProgress

Describes the contacts synchronization progress, including the synchronization ID, current batch, and total batch.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**System capability**: SystemCapability.Applications.Contacts

|                Name              |                  Type                |  Read-Only | Optional   |        Description     |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| syncId        | number |  No |  No  |  Synchronization ID used to synchronize all contacts. The value range is [0, 2147483647].    |
| currentBatch        | number |  No |  No   | ID of the current batch of contacts to be synchronized. The value ranges from 1 to **totalBatches**.    |
| totalBatches        | number |  No |  No   | Total batches of contacts to be synchronized.    |

## ContactSyncInfo

Describes the contacts synchronization information of the calling application.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.

**System capability**: SystemCapability.Applications.Contacts

|                Name              |                  Type                |  Read-Only | Optional   |        Description     |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| mode        | [ContactSyncMode](#contactsyncmode) |  No |  No  |  Contacts synchronization mode.    |
| syncId        | number |  No |  No   | Synchronization ID used to synchronize all contacts.    |
| completedBatches        | Array&lt;number&gt; |  No |  No   | Array of batch IDs of contacts that have been successfully synchronized. The value ranges from 1 to **totalBatches**.     |
| totalBatches        | number |  No |  No   | Total batches of contacts to be synchronized.    |
| lastSyncTime        | number |  No |  No   | Latest timestamp for contact synchronization, in milliseconds.|
