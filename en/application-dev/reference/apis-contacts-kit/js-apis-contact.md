# @ohos.contact (Contacts)

<!--Kit: Contacts Kit-->
<!--Subsystem: Applications-->
<!--Owner: @librahCode-->
<!--Designer: @yanghaoqian-->
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
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the result. If the operation is successful, the ID of the added contact is returned. If the operation fails, an error code is returned.    |

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
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the result. If the operation is successful, the ID of the added contact is returned. If the operation fails, an error code is returned.|

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

**Return value**

| Type                 | Description                             |
| --------------------- | --------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result, which is the ID of the added contact.|

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

**Return value**

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
| key      | string                    | Yes  | Unique query key of a contact. One contact corresponds to one key, which can be obtained through [selectContacts](#contactselectcontacts10-1).           |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, the ID of the deleted contact is returned. If the operation fails, an error code is returned.    |

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
| key      | string                    | Yes  | Unique query key of a contact. One contact corresponds to one key, which can be obtained through [selectContacts](#contactselectcontacts10-1).|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, the ID of the deleted contact is returned. If the operation fails, an error code is returned.|

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
| key     | string  | Yes  | Unique query key of a contact. One contact corresponds to one key, which can be obtained through [selectContacts](#contactselectcontacts10-1).                     |

**Return value**

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
| key    | string | Yes  | Unique query key of a contact. One contact corresponds to one key, which can be obtained through [selectContacts](#contactselectcontacts10-1).|

**Return value**

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
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned.    |

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
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned.|

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
| callback | AsyncCallback&lt;void&gt;               | Yes  | Callback used to return the result. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned.    |

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
| callback | AsyncCallback&lt;void&gt;               | Yes  | Callback used to return the result. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned.|

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

**Return value**

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

**Return value**

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

**Return value**

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

**Return value**

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

**Return value**

| Type                  | Description                                                      |
| ---------------------- | ---------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the contact is included in my card, and the value **false** indicates the opposite.|

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

**Return value**

| Type                  | Description                                                      |
| ---------------------- | ---------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the contact is included in my card, and the value **false** indicates the opposite.|

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
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, information about my card is returned. If the operation fails, an error code is returned.    |

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
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, information about my card is returned. If the operation fails, an error code is returned.|

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
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, information about my card is returned. If the operation fails, an error code is returned.    |

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
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, information about my card is returned. If the operation fails, an error code is returned.|

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

**Return value**

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

**Return value**

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
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of selected contacts is returned. If the operation fails, an error code is returned.|

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

**Return value**

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
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of selected contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

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

**Return value**

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

Selects a contact. ([ContactSelectionOptions10+](#contactselectionoptions10) can be transferred during contact selection.) This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------ |
| options | [ContactSelectionOptions](#contactselectionoptions10) | Yes  | Contact selection options, which specifies whether one contact or multiple contacts can be selected.|
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of selected contacts is returned. If the operation fails, an error code is returned.|

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

**Return value**

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
| key      | string                                   | Yes  | Key of the contact, which is the unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one key.                      |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.  |

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
| key      | string                                   | Yes  | Key of the contact, which is the unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one key.                    |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| key      | string                                   | Yes  | Key of the contact, which is the unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one key.                     |
| holder   | [Holder](#holder)                        | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                      |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.  |

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
    bundleName: "",
    displayName: ""
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
| key      | string                                   | Yes  | Key of the contact, which is the unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one key.                   |
| holder   | [Holder](#holder)                        | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                    |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query the contact whose key is xxx and holder ID is 1.
  contact.queryContact('xxx', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| key      | string                                   | Yes  | Key of the contact, which is the unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one key.                      |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                      |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.  |

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
| key      | string                                   | Yes  | Key of the contact, which is the unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one key.                    |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                       |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| key      | string                                   | Yes  | Key of the contact, which is the unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one key.                      |
| holder   | [Holder](#holder)                        | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                      |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.  |

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
    bundleName: "",
    displayName: ""
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
| key      | string                                   | Yes  | Key of the contact, which is the unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one key.                    |
| holder   | [Holder](#holder)                        | Yes  | Application information for a contact. If this parameter is empty, the system will not filter contacts based on the application information.                                    |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                        |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query the contact whose key, holder and attributes meet the conditions.
  contact.queryContact('xxx', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| key     | string                                  | Yes  | Key of the contact, which is the unique identifier automatically generated by the system when a contact is created. Each contact corresponds to one key.                      |
| holder  | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering.      |
| attrs   | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.          |

**Return value**

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
    bundleName: "",
    displayName: ""
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
| key    | string                                  | Yes  | Key of the contact, which is the unique identifier automatically generated when a contact is created. Each contact corresponds to one key.|
| holder | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, the system will not filter contacts based on the application information.               |
| attrs  | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.                   |

**Return value**

| Type                              | Description                                 |
| ---------------------------------- | ------------------------------------- |
| Promise&lt;[Contact](#contact)&gt; | Promise used to return the result, which is the queried contact.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  // Asynchronous callback used to query contacts.
  let promise = contact.queryContact('xxx', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| holder   | [Holder](#holder)                                     | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                      |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
    bundleName: "",
    displayName: ""
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
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContacts](#contactquerycontacts10) instead.

**Required permissions**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| holder   | [Holder](#holder)                                     | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                      |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Asynchronous callback used to query contacts.
  contact.queryContacts({
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| holder   | [Holder](#holder)                                     | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                      |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
    bundleName: "",
    displayName: ""
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
| holder   | [Holder](#holder)                                     | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                       |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Asynchronous callback used to query contacts.
  contact.queryContacts({
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| holder  | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is empty, the system will not filter contacts based on the application information.      |
| attrs   | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.              |

**Return value**

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
    bundleName: "",
    displayName: ""
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
| holder | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, the system will not filter contacts based on the application information.|
| attrs  | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.    |

**Return value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

**Example**

```js
  import { contact } from '@kit.ContactsKit';

  // Query all contacts based on the specified holder and attributes.
  let promise = contact.queryContacts({
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| holder      | [Holder](#holder)                                     | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                       |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
  contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| holder      | [Holder](#holder)                                     | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                       |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  // Query a contact based on the phone number 138xxxxxxxx and the holder ID.
  contact.queryContactsByPhoneNumber('138xxxxxxxx', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| holder      | [Holder](#holder)                                     | Yes  | Application information for a contact. If this parameter is empty, the system will not filter contacts based on the application information.                                       |
| attrs       | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
  contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| holder      | [Holder](#holder)                                     | Yes  | Application information for a contact. If this parameter is empty, the system will not filter contacts based on the application information.                                       |
| attrs       | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields of the contact are queried.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryContactsByPhoneNumber('138xxxxxxxx', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| holder      | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, the system will not filter contacts based on the application information.      |
| attrs       | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.              |

**Return value**

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
  let promise = contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| holder      | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, the system will not filter contacts based on the application information.|
| attrs       | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.    |

**Return value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  let promise = contact.queryContactsByPhoneNumber('138xxxxxxxx', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| holder   | [Holder](#holder)                                     | Yes  | Application information for a contact. If this parameter is empty, the system contact application is used.                                       |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
    bundleName: "",
    displayName: ""
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
| holder   | [Holder](#holder)                                     | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                       |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryContactsByEmail('xxx@email.com', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| holder   | [Holder](#holder)                                     | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                       |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
    bundleName: "",
    displayName: ""
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
| holder   | [Holder](#holder)                                     | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter contacts based on the application information.                                      |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | Contact attribute list. If this parameter is empty, all attribute fields (including the name, phone number, and email address) of the contact are queried.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryContactsByEmail('xxx@email.com', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| holder  | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, the system will not filter contacts based on the application information.                                      |
| attrs   | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.                                          |

**Return value**

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
    bundleName: "",
    displayName: ""
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
| holder | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, the system will not filter contacts based on the application information.|
| attrs  | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.    |

**Return value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  let promise = contact.queryContactsByEmail('xxx@email.com', {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
| holder   | [Holder](#holder)                                 | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter groups based on the application information.                                      |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

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
    bundleName: "",
    displayName: ""
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
| holder   | [Holder](#holder)                                 | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter groups based on the application information.                                       |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryGroups({
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| holder  | [Holder](#holder) | No  | Application information for a contact. If this parameter is not specified, the system will not filter groups based on the application information.                                      |

**Return value**

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
    bundleName: "",
    displayName: ""
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
| holder | [Holder](#holder) | No  | Application information for a contact. If this parameter is not specified, it is not used for group filtering.|

**Return value**

| Type                                       | Description                                   |
| ------------------------------------------- | --------------------------------------- |
| Promise&lt;Array&lt;[Group](#group)&gt;&gt; | Promise used to return the result, which is an array of groups.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  let promise = contact.queryGroups({
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| callback | AsyncCallback&lt;Array&lt;[Holder](#holder)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of the queried applications is returned. If the operation fails, an error code is returned.|

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
| callback | AsyncCallback&lt;Array&lt;[Holder](#holder)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of the queried applications is returned. If the operation fails, an error code is returned.|

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

**Return value**

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

**Return value**

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
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the operation is successful, the key of the queried contact is returned. If the operation fails, an error code is returned.|

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
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the operation is successful, the key of the queried contact is returned. If the operation fails, an error code is returned.|

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
| holder   | [Holder](#holder)           | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter keys based on the application information.                                       |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the operation is successful, the key of the queried contact is returned. If the operation fails, an error code is returned.|

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
    bundleName: "",
    displayName: ""
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
| holder   | [Holder](#holder)           | Yes  | Application information for a contact. If the passed parameter is empty, the system will not filter keys based on the application information.                                       |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the operation is successful, the key of the queried contact is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';

  contact.queryKey(1, {
    holderId: 1,
    bundleName: "",
    displayName: ""
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
| holder  | [Holder](#holder) | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering.                                      |

**Return value**

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
    bundleName: "",
    displayName: ""
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
| holder | [Holder](#holder) | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering.|

**Return value**

| Type                 | Description                                      |
| --------------------- | ------------------------------------------ |
| Promise&lt;string&gt; | Promise used to return the result, which is the key of the queried contact.|

**Example**

  ```js
  import { contact } from '@kit.ContactsKit';

  let promise = contact.queryKey(1, {
    holderId: 1,
    bundleName: "",
    displayName: ""
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

**Return value**

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

**Return value**

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

**Return value**

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
| 16700101       | Failed to get value to contacts data. |
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

**Return value**

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

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                  | Yes  | Phone number of the contacts.                                          |
| minDuration      | number                      | Yes  | Minimum call duration, in seconds. The value must be greater than 0.       |
| withinTime       | number | Yes  | Period of time that the start time and end time of calls should be within, in seconds. This period starts from the current time. A maximum of six hours can be set. If the query duration exceeds six hours, the query duration is six hours by default.              |

**Return value**

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

const phoneNumber = '13812345678';
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

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type               | Mandatory| Description                                                        |
| ------- | ------------------- | ---- | ------------------------------------------------------------ |
| context | Context             | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                  | Yes  | Phone number of the contacts.                                          |
| minDuration      | number                      | Yes  | Minimum call duration, in seconds. The value must be greater than 0.      |

**Return value**

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

const phoneNumber = '13812345678';
const minDuration = 60;
// Call the API to query call records. By default, call records within the last 6 hours are queried.
contact.hasMatchedCallLog(context, phoneNumber, minDuration).then((hasMatch:boolean) => {
  console.info(`Has matched call log: ${hasMatch}`);
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

## ContactSelectionFilter<sup>15+</sup>

Describes the contact selection filter.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

|                Name              |                  Type                |  Read-Only | Optional   |        Description     |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| filterClause        | [FilterClause](#filterclause15) |  No |  No  |  Filter criteria.    |
| filterType        | [FilterType](#filtertype15) |  No |  No   | Filter type.    |

**Example**
Use **contactSelectionFilter** to filter contacts and use a promise to return the query result.

>**NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use **UIAbilityContext** APIs on pages, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```js
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// Obtain the context within the component.
const ctx = this.getUIContext().getHostContext() as common.UIAbilityContext;
const filter = {
  filterType: 1,
  filterClause: {
    id: [{ filterCondition: contact.FilterCondition.EQUAL_TO, value: '1' }],
    name: [{ filterCondition: contact.FilterCondition.CONTAINS, value: 'Zhang' }],
    dataItem: [{ filterCondition: contact.FilterCondition.IN, value: ['a@x.com', 'b@y.com'] }]
  }
};
contact.getContactList({ uiContext: ctx, selectionFilter: filter})
  .then(r =>console.info(`Return ${r.contacts?.length ?? 0}`))
  .catch(e => console.error (`Query error ${e.code}: ${e.message}`));

```

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

### Constant

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name              | Type  | Value  | Description            |
| ------------------ | ---- | ---- | ---------------- |
| INVALID_CONTACT_ID | number   | -1   | Default contact ID.|

### Attributes

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

|       Name       |                   Type                 | Read-Only| Optional| Description                                  |
| ----------------- | --------------------------------------- | ---- | ---- | -------------------------------------- |
| id                | number                                  | Yes  | Yes  | Contact ID, which is automatically generated by the system.                          |
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
        phoneNumber: "138xxxxxxxx"
    }],
    name: {
        fullName: "fullName",
        namePrefix: "namePrefix"
    },
    nickName: {
        nickName: "nickName"
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

Enumerates contact attributes. The enumerated value is of the number type.

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

### Constant

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name            | Type  | Value  | Description            |
| ---------------- | ---- | ---- | ---------------- |
| CUSTOM_LABEL     | number    |  0    |Custom mailbox type.|
| EMAIL_HOME       | number    | 1    | Home mailbox.  |
| EMAIL_WORK       | number    | 2    | Work mailbox.  |
| EMAIL_OTHER      | number    | 3    | Other mailbox.  |
| INVALID_LABEL_ID | number    | -1   | Invalid mailbox.  |

### Attributes

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name       |   Type  | Read-Only| Optional| Description            |
| ----------- | -------- | ---- | ---- | ---------------- |
| email       | string   | No  | No  | Email addresses      |
| labelName   | string   | No  | Yes  | Name of the mailbox type.|
| displayName | string   | No  | Yes  | Displayed name of the mailbox.|
| labelId     | number   | No  | Yes  | Mailbox type.    |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let email: contact.Email = {
    email: "xxx@email.com",
    displayName: "displayName"
}
```


  Or, create data by configuring an **Email** object.

```js
let email = new contact.Email();
email.email = "xxx@email.com";
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
  bundleName: "com.ohos.contacts",
  displayName: "displayName",
  holderId: 1
};
```

## Event

Defines a contact's event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

### Constant

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name             |   Type  |  Value  | Description              |
| ----------------- | ---- | ---- | ------------------ |
| CUSTOM_LABEL      | number   | 0    | Custom event.  |
| EVENT_ANNIVERSARY | number   | 1    | Anniversary event.|
| EVENT_OTHER       | number   | 2    | Other event.    |
| EVENT_BIRTHDAY    | number   | 3    | Birthday event.    |
| INVALID_LABEL_ID  | number   | -1   | Invalid event.    |

### Attributes

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

|    Name  |   Type  | Read-Only| Optional| Description          |
| --------- | -------- | ---- | ---- | -------------- |
| eventDate | string   | No  | No  | Event date.  |
| labelName | string   | No  | Yes  | Event type.|
| labelId   | number   | No  | Yes  | Event type ID.    |

**Example**

  Create contact data in JSON format:

```js
let event: contact.Event = {
    eventDate: "2000-01-01"
};
```

  Or, create data by configuring an **Event** object.

```js
let event = new contact.Event();
event.eventDate = "2000-01-01";
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
    title: "title"
};
```

## ImAddress

Enumerates IM addresses.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

### Constant

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name            |   Type  | Value  | Description                |
| ---------------- | ---- | ---- | -------------------- |
| CUSTOM_LABEL     | number   | -1   | Custom IM|
| IM_AIM           | number   | 0    | AIM   |
| IM_MSN           | number   | 1    | MSN   |
| IM_YAHOO         | number   | 2    | Yahoo |
| IM_SKYPE         | number   | 3    | Skype |
| IM_QQ            | number   | 4    | QQ    |
| IM_ICQ           | number   | 6    | ICQ   |
| IM_JABBER        | number   | 7    | JABBER|
| INVALID_LABEL_ID | number   | -2   | Invalid IM|

### Attributes

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name     |   Type  | Read-Only| Optional| Description              |
| --------- | -------- | ---- | ---- | ------------------ |
| imAddress | string   | No  | No  | IM address.    |
| labelName | string   | No  | Yes  | IM name.|
| labelId   | number   | No  | Yes  | IM ID.    |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let imAddress: contact.ImAddress = {
    imAddress: "imAddress",
    labelName: "labelName"
};
```


  Or, create data by configuring an **ImAddress** object.

```js
let imAddress = new contact.ImAddress();
imAddress.imAddress = "imAddress";
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
    familyName: "familyName",
    fullName: "fullName"
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
    nickName: "nickName"
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
    noteContent: "noteContent"
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
    name: "name",
    title: "title"
};
```

## PhoneNumber

Defines a contact's phone number.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

### Constant

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name            |  Type | Value  | Description                                            |
| ---------------- | ---- | ---- | ------------------------------------------------ |
| CUSTOM_LABEL     |  number  | 0    | Custom phone type.                                |
| NUM_HOME         |  number  | 1    | Home phone.                                  |
| NUM_MOBILE       |  number  | 2    | Mobile phone.                                  |
| NUM_WORK         |  number  | 3    | Work phone.                                  |
| NUM_FAX_WORK     |  number  | 4    | Work fax.                              |
| NUM_FAX_HOME     |  number  | 5    | Family fax.                              |
| NUM_PAGER        |  number  | 6    | Pager.                                |
| NUM_OTHER        |  number  | 7    | Other phone type.                                  |
| NUM_CALLBACK     |  number  | 8    | Callback phone.                                  |
| NUM_CAR          |  number  | 9    | Car phone.                                  |
| NUM_COMPANY_MAIN |  number  | 10   | Company phone.                                  |
| NUM_ISDN         |  number  | 11   | Integrated Services Digital Network (ISDN) phone.                |
| NUM_MAIN         |  number  | 12   | Main phone.                                    |
| NUM_OTHER_FAX    |  number  | 13   | Other fax phone.                                  |
| NUM_RADIO        |  number  | 14   | Wireless phone.                                  |
| NUM_TELEX        |  number  | 15   | Telex phone.                                  |
| NUM_TTY_TDD      |  number  | 16   | Teletypewriter (TTY) or Test Driven Development (TDD) phone.|
| NUM_WORK_MOBILE  |  number  | 17   | Work mobile phone.                              |
| NUM_WORK_PAGER   |  number  | 18   | Work pager.                            |
| NUM_ASSISTANT    |  number  | 19   | Assistant phone.                                  |
| NUM_MMS          |  number  | 20   | MMS phone.                                  |
| INVALID_LABEL_ID |  number  | -1   | Invalid phone type.                                  |

### Attributes

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name       |   Type  | Read-Only| Optional| Description              |
| ----------- | -------- | ---- | ---- | ------------------ |
| labelName   | string   | No  | Yes  | Phone number type.|
| phoneNumber | string   | No  | No  | Phone number.        |
| labelId     | number   | No  | Yes  | Phone number ID.    |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let phoneNumber: contact.PhoneNumber = {
    phoneNumber: "138xxxxxxxx",
    labelId: contact.PhoneNumber.NUM_HOME
};
```

  Or, create data by configuring a new **PhoneNumber** object.

```js
let phoneNumber = new contact.PhoneNumber();
phoneNumber.phoneNumber = "138xxxxxxxx";
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
    uri: "",
    photo: photo
  };
}
```

## PostalAddress

Defines a contact's postal address.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

### Constant

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name            |   Type  | Value  | Description                |
| ---------------- | ---- | ---- | -------------------- |
| CUSTOM_LABEL     | number   | 0    | Custom postal address type.|
| ADDR_HOME        | number   | 1    | Home address.      |
| ADDR_WORK        | number   | 2    | Work address.      |
| ADDR_OTHER       | number   | 3    | Other addresses.      |
| INVALID_LABEL_ID | number   | -1   | Invalid address type.      |

### Attributes

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name         |   Type  | Read-Only| Optional| Description                      |
| ------------- | -------- | ---- | ---- | -------------------------- |
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
    city: "city",
    postalAddress: "postalAddress"
};
```

  Or, create data by configuring a new **PostalAddress** object.

```js
import { contact } from '@kit.ContactsKit';

let postalAddress = new contact.PostalAddress();
postalAddress.city = "city";
postalAddress.postalAddress = "postalAddress";
```

## Relation

Defines a contact's relationship.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

### Constant

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name                     |  Type  | Value  | Description              |
| ------------------------- | ---- | ---- | ------------------ |
| CUSTOM_LABEL              | number   | 0    | Custom relationship.  |
| RELATION_ASSISTANT        | number   | 1    | Assistant.    |
| RELATION_BROTHER          | number   | 2    | Sibling.    |
| RELATION_CHILD            | number   | 3    | Child.    |
| RELATION_DOMESTIC_PARTNER | number   | 4    | Domestic partner.|
| RELATION_FATHER           | number   | 5    | Father.    |
| RELATION_FRIEND           | number   | 6    | Friend.    |
| RELATION_MANAGER          | number   | 7    | Manager.  |
| RELATION_MOTHER           | number   | 8    | Mother.    |
| RELATION_PARENT           | number   | 9    | Parent.    |
| RELATION_PARTNER          | number   | 10   | Partner.|
| RELATION_REFERRED_BY      | number   | 11   | Referrer.  |
| RELATION_RELATIVE         | number   | 12   | Relative.    |
| RELATION_SISTER           | number   | 13   | Sister.    |
| RELATION_SPOUSE           | number   | 14   | Spouse.    |
| INVALID_LABEL_ID          | number   | -1   | Invalid relationship.  |

### Attributes

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name        |   Type  | Read-Only| Optional| Description          |
| ------------ | -------- | ---- | ---- | -------------- |
| labelName    | string   | No  | Yes  | Relationship type.|
| relationName | string   | No  | No  | Relationship name.    |
| labelId      | number   | No  | Yes  | Relationship ID.    |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let relation: contact.Relation = {
    relationName: "relationName",
    labelId: contact.Relation.RELATION_ASSISTANT
};
```

  Or, create data by configuring a new **Relation** object.

```js
import { contact } from '@kit.ContactsKit';

let relation = new contact.Relation();
relation.relationName = "relationName";
relation.labelId = contact.Relation.RELATION_ASSISTANT;
```

## SipAddress

Defines a contact's SIP address.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

### Constant

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name            |   Type  | Value  | Description                               |
| ---------------- | ---- | ---- | ----------------------------------- |
| CUSTOM_LABEL     | number   | 0    | Custom SIP address.|
| SIP_HOME         | number   | 1    | Home SIP address.  |
| SIP_WORK         | number   | 2    | Work SIP address.  |
| SIP_OTHER        | number   | 3    | Other SIP address.  |
| INVALID_LABEL_ID | number   | -1   | Invalid SIP address.  |

### Attributes

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name      |   Type  | Read-Only| Optional| Description                             |
| ---------- | -------- | ---- | ---- | --------------------------------- |
| labelName  | string   | No  | Yes  | SIP address type.|
| sipAddress | string   | No  | No  | SIP address.        |
| labelId    | number   | No  | Yes  | SIP address ID.    |

**Example**

  Create contact data in JSON format:

```js
import { contact } from '@kit.ContactsKit';

let sipAddress: contact.SipAddress = {
    sipAddress: "sipAddress"
};
```

  Or, create data by configuring a new **SipAddress** object.

```js
import { contact } from '@kit.ContactsKit';

let sipAddress = new contact.SipAddress();
sipAddress.sipAddress = "sipAddress";
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
    website: "website"
};
```
