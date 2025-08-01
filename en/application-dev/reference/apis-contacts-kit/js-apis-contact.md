# @ohos.contact (Contacts)

The **contact** module provides contact management functions, such as adding, deleting, and updating contacts.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```
import { contact } from '@kit.ContactsKit';
```

## contact.addContact<sup>10+</sup>

addContact(context: Context, contact: Contact, callback: AsyncCallback&lt;number&gt;): void 

Adds a contact. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Permission required**: ohos.permission.WRITE_CONTACTS

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

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.addContact(
    context,
    {
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

## contact.addContact<sup>(deprecated)7+</sup>

addContact(contact: Contact, callback: AsyncCallback&lt;number&gt;): void

Adds a contact. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [addContact](#contactaddcontact10) instead.

**Permission required**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                       | Mandatory| Description                                                    |
| -------- | --------------------------- | ---- | -------------------------------------------------------- |
| contact  | [Contact](#contact)         | Yes  | Contact information.                                            |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the result. If the operation is successful, the ID of the added contact is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  contact.addContact({
      name: {
	    fullName: 'xxx'
	  },
      phoneNumbers: [{
	    phoneNumber: '138xxxxxxxx'
	  }]
  }, (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to add Contact. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  });
  ```

## contact.addContact<sup>10+</sup>

addContact(context: Context, contact: Contact): Promise<number&gt;

Adds a contact. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Permission required**: ohos.permission.WRITE_CONTACTS

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

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.addContact(
    context,
    {
	  name: {
	    fullName: 'xxx'
	  },
      phoneNumbers: [{
	    phoneNumber: '138xxxxxxxx'
	  }]
  });
  promise.then((data) => {
    console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to add Contact. Code: ${err.code}, message: ${err.message}`);
  });
```

## contact.addContact<sup>(deprecated)7+</sup>

addContact(contact: Contact): Promise&lt;number&gt;

Adds a contact. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [addContact](#contactaddcontact10-1) instead.

**Permission required**: ohos.permission.WRITE_CONTACTS

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
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.addContact({
      name: {
	    fullName: 'xxx'
	  },
      phoneNumbers: [{
	    phoneNumber: '138xxxxxxxx'
	  }]
  });
  promise.then((data) => {
      console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to add Contact. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.deleteContact<sup>10+</sup>

deleteContact(context: Context, key: string, callback: AsyncCallback&lt;void&gt;): void

Deletes a contact based on the specified contact key. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                   | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key      | string                    | Yes  | Unique query key of a contact. One contact corresponds to one key.            |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, the ID of the deleted contact is returned. If the operation fails, an error code is returned.    |

**Error codes**

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.deleteContact(context, 'xxx', (err: BusinessError) => {
      if (err) {
          console.error(`Failed to delete Contact. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info('Succeeded in deleting Contact.');
  });
```

## contact.deleteContact<sup>(deprecated)7+</sup>

deleteContact(key: string, callback: AsyncCallback&lt;void&gt;): void

Deletes a contact based on the specified contact key. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [deleteContact](#contactdeletecontact10) instead.

**Permission required**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                     | Mandatory| Description                                |
| -------- | ------------------------- | ---- | ------------------------------------ |
| key      | string                    | Yes  | Unique query key of a contact. One contact corresponds to one key.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, the ID of the deleted contact is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  contact.deleteContact('xxx', (err: BusinessError) => {
      if (err) {
          console.error(`Failed to delete Contact. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info('Succeeded in deleting Contact.');
  });
  ```

## contact.deleteContact<sup>10+</sup>

deleteContact(context: Context,  key: string): Promise&lt;void&gt;

Deletes a contact based on the specified contact key. This API uses a promise to return the result.

**Permission required**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type   | Mandatory| Description                                                        |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key     | string  | Yes  | Unique query key of a contact. One contact corresponds to one key.                      |

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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.deleteContact(context, 'xxx');
  promise.then(() => {
      console.info(`Succeeded in deleting Contact.`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to delete Contact. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.deleteContact<sup>(deprecated)7+</sup>

deleteContact(key: string): Promise&lt;void&gt;

Deletes a contact based on the specified contact key. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [deleteContact](#contactdeletecontact10-1) instead.

**Permission required**: ohos.permission.WRITE_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| key    | string | Yes  | Unique query key of a contact. One contact corresponds to one key.|

**Return Value**

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.deleteContact('xxx');
  promise.then(() => {
      console.info(`Succeeded in deleting Contact.`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to delete Contact. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.updateContact<sup>10+</sup>

updateContact(context: Context, contact: Contact, callback: AsyncCallback&lt;void&gt;): void

Updates a contact based on the specified contact information. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                   | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| contact  | [Contact](#contact)       | Yes  | Contact information. Contact ID, which is mandatory.                                        |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned.    |

**Error codes**

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.updateContact(context, {
      id: 1,
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
  ```

## contact.updateContact<sup>(deprecated)7+</sup>

updateContact(contact: Contact, callback: AsyncCallback&lt;void&gt;): void

Updates a contact based on the specified contact information. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [updateContact](#contactupdatecontact10) instead.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                     | Mandatory| Description                                |
| -------- | ------------------------- | ---- | ------------------------------------ |
| contact  | [Contact](#contact)       | Yes  | Contact information. Contact ID, which is mandatory.                        |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  contact.updateContact({
      id: 1,
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
  ```

## contact.updateContact<sup>10+</sup>

updateContact(context: Context,  contact: Contact, attrs: ContactAttributes, callback: AsyncCallback&lt;void&gt;): void

Updates a contact based on the specified contact information. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                   | Mandatory| Description                                                        |
| -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| contact  | [Contact](#contact)                     | Yes  | Contact information. Contact ID, which is mandatory.                                        |
| attrs    | [ContactAttributes](#contactattributes) | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;void&gt;               | Yes  | Callback used to return the result. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned.    |

**Error codes**

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.updateContact(context, {
      id: 1,
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
  ```

## contact.updateContact<sup>(deprecated)7+</sup>

updateContact(contact: Contact, attrs: ContactAttributes, callback: AsyncCallback&lt;void&gt;): void

Updates a contact based on the specified contact information. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [updateContact](#contactupdatecontact10-1) instead.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                   | Mandatory| Description                                |
| -------- | --------------------------------------- | ---- | ------------------------------------ |
| contact  | [Contact](#contact)                     | Yes  | Contact information. Contact ID, which is mandatory.                        |
| attrs    | [ContactAttributes](#contactattributes) | Yes  | List of contact attributes.                  |
| callback | AsyncCallback&lt;void&gt;               | Yes  | Callback used to return the result. If the operation is successful, the ID of the updated contact is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  contact.updateContact({
      id: 1,
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
  ```

## contact.updateContact<sup>10+</sup>

updateContact(context: Context,  contact: Contact, attrs?: ContactAttributes): Promise&lt;void&gt;

Updates a contact based on the specified contact information and attributes. This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| contact | [Contact](#contact)                     | Yes  | Contact information. Contact ID, which is mandatory.                                                |
| attrs   | [ContactAttributes](#contactattributes) | No  | List of contact attributes.                                          |

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

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.updateContact(context, {
      id: 1,
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
  }).catch((err: BusinessError) => {
      console.error(`Failed to update Contact. Code: ${err.code}, message: ${err.message}`);
  });
```

## contact.updateContact<sup>(deprecated)7+</sup>

updateContact(contact: Contact, attrs?: ContactAttributes): Promise&lt;void&gt;

Updates a contact based on the specified contact information and attributes. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [updateContact](#contactupdatecontact10-2) instead.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description              |
| ------- | --------------------------------------- | ---- | ------------------ |
| contact | [Contact](#contact)                     | Yes  | Contact information. Contact ID, which is mandatory.      |
| attrs   | [ContactAttributes](#contactattributes) | No  | List of contact attributes.|

**Return Value**

| Type               | Description                                  |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.updateContact({
      id: 1,
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
  }).catch((err: BusinessError) => {
      console.error(`Failed to update Contact. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.isLocalContact<sup>10+</sup>

isLocalContact(context: Context,  id: number, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the ID of this contact is in the local address book. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.isLocalContact(context, /*id*/1, (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to isLocalContact. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in isLocalContact.`);
  });
  ```

## contact.isLocalContact<sup>(deprecated)7+</sup>

isLocalContact(id: number, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the ID of this contact is in the local address book. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [isLocalContact](#contactislocalcontact10) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                        | Mandatory| Description                                                        |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| id       | number                       | Yes  | Contact ID. Each contact corresponds to one ID.                  |
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. If the operation is successful, a Boolean value is returned. The value **true** indicates that the contact ID is in the local phonebook, and the value **false** indicates the opposite. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  contact.isLocalContact(/*id*/1, (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to isLocalContact. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in isLocalContact.`);
  });
  ```

## contact.isLocalContact<sup>10+</sup>

isLocalContact(context: Context,  id: number): Promise&lt;boolean&gt;

Checks whether the ID of this contact is in the local address book. This API uses a promise to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

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

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.isLocalContact(context, /*id*/1);
  promise.then((data) => {
      console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to isLocalContact. Code: ${err.code}, message: ${err.message}`);
  });
```

## contact.isLocalContact<sup>(deprecated)7+</sup>

isLocalContact(id: number): Promise&lt;boolean&gt;

Checks whether the ID of this contact is in the local address book. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [isLocalContact](#contactislocalcontact10-1) instead.[isLocalContact](#contactislocalcontact10-1)

**Permission required**: ohos.permission.READ_CONTACTS

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
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.isLocalContact(/*id*/1);
  promise.then((data) => {
      console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to isLocalContact. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.isMyCard<sup>10+</sup>

isMyCard(context: Context,  id: number, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether a contact is included in my card. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

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

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.isMyCard(context, /*id*/1, (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to isMyCard. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  });
```

## contact.isMyCard<sup>(deprecated)7+</sup>

isMyCard(id: number, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether a contact is included in my card. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [isMyCard](#contactismycard10) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                        | Mandatory| Description                                                        |
| -------- | ---------------------------- | ---- | ------------------------------------------------------------ |
| id       | number                       | Yes  | Contact ID.                                          |
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. If the operation is successful, a Boolean value is returned. The value **true** indicates that the contact is included in my card, and the value **false** indicates the opposite. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  contact.isMyCard(/*id*/1, (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to isMyCard. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  });
  ```

## contact.isMyCard<sup>10+</sup>

isMyCard(context: Context,  id: number): Promise&lt;boolean&gt;

Checks whether a contact is included in my card. This API uses a promise to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type   | Mandatory| Description                                                        |
| ------- | ------- | ---- | ------------------------------------------------------------ |
| context | Context | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| id      | number  | Yes  | Contact ID.                                        |

**Return Value**

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

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.isMyCard(context, /*id*/1);
  promise.then((data) => {
      console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to isMyCard. Code: ${err.code}, message: ${err.message}`);
  });
```

## contact.isMyCard<sup>(deprecated)7+</sup>

isMyCard(id: number): Promise&lt;boolean&gt;

Checks whether a contact is included in my card. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [isMyCard](#contactismycard10-1) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| id     | number | Yes  | Contact ID.|

**Return Value**

| Type                  | Description                                                      |
| ---------------------- | ---------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the contact is included in my card, and the value **false** indicates the opposite.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.isMyCard(/*id*/1);
  promise.then((data) => {
      console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to isMyCard. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryMyCard<sup>10+</sup>

queryMyCard(context: Context,  callback: AsyncCallback&lt;Contact&gt;): void

Queries my card. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

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

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryMyCard(context, (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });
```

## contact.queryMyCard<sup>(deprecated)7+</sup>

queryMyCard(callback: AsyncCallback&lt;Contact&gt;): void

Queries my card. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryMyCard](#contactquerymycard10) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                    |
| -------- | ---------------------------------------- | ---- | -------------------------------------------------------- |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, information about my card is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries my card. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                        |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, information about my card is returned. If the operation fails, an error code is returned.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryMyCard<sup>(deprecated)7+</sup>

queryMyCard(attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;): void

Queries my card. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryMyCard](#contactquerymycard10-1) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                    |
| -------- | ---------------------------------------- | ---- | -------------------------------------------------------- |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | List of contact attributes.                                      |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, information about my card is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries my card based on the specified contact attributes. This API uses a promise to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| attrs   | [ContactAttributes](#contactattributes) | No  | List of contact attributes.                                          |

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

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryMyCard(context, {
      attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
      console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
  });
```

## contact.queryMyCard<sup>(deprecated)7+</sup>

queryMyCard(attrs?: ContactAttributes): Promise&lt;Contact&gt;

Queries my card based on the specified contact attributes. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryMyCard](#contactquerymycard10-2) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type                                   | Mandatory| Description              |
| ------ | --------------------------------------- | ---- | ------------------ |
| attrs  | [ContactAttributes](#contactattributes) | No  | List of contact attributes.|

**Return Value**

| Type                              | Description                                   |
| ---------------------------------- | --------------------------------------- |
| Promise&lt;[Contact](#contact)&gt; | Promise used to return the result, which is a contact in my card.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.queryMyCard({
      attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
      console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.selectContact<sup>(deprecated)7+</sup>

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

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  contact.selectContact((err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to select Contact. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in selecting Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.selectContact<sup>(deprecated)7+</sup>

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
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.selectContact();
  promise.then((data) => {
      console.info(`Succeeded in selecting Contact. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to select Contact. Code: ${err.code}, message: ${err.message}`);
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
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.selectContacts();
  promise.then((data) => {
      console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to select Contacts. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.selectContacts<sup>10+</sup>

selectContacts(options: ContactSelectionOptions, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Selects a contact. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------ |
| options | [ContactSelectionOptions](#contactselectionoptions10) | Yes  | Contact selection options.|
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of selected contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Selects a contact. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.Contacts

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------ |
| options | [ContactSelectionOptions](#contactselectionoptions10) | Yes  | Contact selection options.|

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
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.selectContacts({isMultiSelect:false});
  promise.then((data) => {
      console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to select Contacts. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryContact<sup>10+</sup>

queryContact(context: Context,  key: string,  callback: AsyncCallback&lt;Contact&gt;): void

Queries a contact based on the specified key. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                        |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key      | string                                   | Yes  | Contact key. Each contact corresponds to one key.                      |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, the queried contact is returned. If the operation fails, an error code is returned.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContact(context, 'xxx', (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContact<sup>(deprecated)7+</sup>

queryContact(key: string,  callback: AsyncCallback&lt;Contact&gt;): void

Queries a contact based on the specified key. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContact](#contactquerycontact10) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                      |
| -------- | ---------------------------------------- | ---- | ---------------------------------------------------------- |
| key      | string                                   | Yes  | Contact key. Each contact corresponds to one key.                    |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, the queried contact is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                        |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key      | string                                   | Yes  | Contact key. Each contact corresponds to one key.                      |
| holder   | [Holder](#holder)                        | Yes  | Application that creates the contacts.                                      |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, the queried contact is returned. If the operation fails, an error code is returned.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContact<sup>(deprecated)7+</sup>

queryContact(key: string, holder: Holder, callback: AsyncCallback&lt;Contact&gt;): void

Queries a contact based on the specified key and holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContact](#contactquerycontact10-1) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                      |
| -------- | ---------------------------------------- | ---- | ---------------------------------------------------------- |
| key      | string                                   | Yes  | Contact key. Each contact corresponds to one key.                    |
| holder   | [Holder](#holder)                        | Yes  | Application that creates the contacts.                                    |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, the queried contact is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                        |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key      | string                                   | Yes  | Contact key. Each contact corresponds to one key.                      |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, the queried contact is returned. If the operation fails, an error code is returned.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContact<sup>(deprecated)7+</sup>

queryContact(key: string,  attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;): void

Queries a contact based on the specified key and attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContact](#contactquerycontact10-2) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                      |
| -------- | ---------------------------------------- | ---- | ---------------------------------------------------------- |
| key      | string                                   | Yes  | Contact key. Each contact corresponds to one key.                    |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | List of contact attributes.                                        |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, the queried contact is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                        |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                  | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key      | string                                   | Yes  | Contact key. Each contact corresponds to one key.                      |
| holder   | [Holder](#holder)                        | Yes  | Application that creates the contacts.                                      |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, the queried contact is returned. If the operation fails, an error code is returned.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContact<sup>(deprecated)7+</sup>

queryContact(key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Contact&gt;): void

Queries a contact based on the specified key, holder, and attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContact](#contactquerycontact10-3) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                    | Mandatory| Description                                                      |
| -------- | ---------------------------------------- | ---- | ---------------------------------------------------------- |
| key      | string                                   | Yes  | Contact key. Each contact corresponds to one key.                    |
| holder   | [Holder](#holder)                        | Yes  | Application that creates the contacts.                                    |
| attrs    | [ContactAttributes](#contactattributes)  | Yes  | List of contact attributes.                                        |
| callback | AsyncCallback&lt;[Contact](#contact)&gt; | Yes  | Callback used to return the result. If the operation is successful, the queried contact is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| key     | string                                  | Yes  | Contact key. Each contact corresponds to one key.                      |
| holder  | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering by default.      |
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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryContact<sup>(deprecated)7+</sup>

queryContact(key: string, holder?: Holder, attrs?: ContactAttributes): Promise&lt;Contact&gt;

Queries a contact based on the specified key, holder, and attributes. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContact](#contactquerycontact10-4) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type                                   | Mandatory| Description                                  |
| ------ | --------------------------------------- | ---- | -------------------------------------- |
| key    | string                                  | Yes  | Contact key. Each contact corresponds to one key.|
| holder | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering by default.               |
| attrs  | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.                   |

**Return Value**

| Type                              | Description                                 |
| ---------------------------------- | ------------------------------------- |
| Promise&lt;[Contact](#contact)&gt; | Promise used to return the result, which is the queried contact.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.queryContact('xxx', {
      holderId: 1,
      bundleName: "",
      displayName: ""
  }, {
      attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
      console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryContacts<sup>10+</sup>

queryContacts(context: Context,  callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContacts(context, (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContacts<sup>(deprecated)7+</sup>

queryContacts(callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries all contacts. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContacts](#contactquerycontacts10) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries contacts based on the specified holder. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| holder   | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContacts<sup>(deprecated)7+</sup>

queryContacts(holder: Holder, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on the specified holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContacts](#contactquerycontacts10) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| holder   | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries contacts based on the specified attributes. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContacts<sup>(deprecated)7+</sup>

queryContacts(attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on the specified attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContacts](#contactquerycontacts10-2) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries contacts based on the specified holder and attributes. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| holder   | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContacts<sup>(deprecated)7+</sup>

queryContacts(holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on the specified holder and attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContacts](#contactquerycontacts10-3) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| holder   | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries contacts based on the specified holder and attributes. This API uses a promise to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| holder  | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering by default.      |
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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryContacts<sup>(deprecated)7+</sup>

queryContacts(holder?: Holder, attrs?: ContactAttributes): Promise&lt;Array&lt;Contact&gt;&gt;

Queries contacts based on the specified holder and attributes. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContacts](#contactquerycontacts10-4) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type                                   | Mandatory| Description                  |
| ------ | --------------------------------------- | ---- | ---------------------- |
| holder | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering by default.|
| attrs  | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.    |

**Return Value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

**Example**

```js
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.queryContacts({
      holderId: 1,
      bundleName: "",
      displayName: ""
  }, {
      attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
      console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
  });
```

## contact.queryContactsByPhoneNumber<sup>10+</sup>

queryContactsByPhoneNumber(context: Context,  phoneNumber: string, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on the specified phone number. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                                | Yes  | Phone number of the contacts.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>(deprecated)7+</sup>

queryContactsByPhoneNumber(phoneNumber: string, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on the specified phone number. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| phoneNumber | string                                                | Yes  | Phone number of the contacts.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries contacts based on the specified phone number and holder. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                                | Yes  | Phone number of the contacts.                                          |
| holder      | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContactsByPhoneNumber<sup>(deprecated)7+</sup>

queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on the specified phone number and holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-1) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| phoneNumber | string                                                | Yes  | Phone number of the contacts.                                          |
| holder      | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries contacts based on the specified phone number and attributes. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                                | Yes  | Phone number of the contacts.                                          |
| attrs       | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContactsByPhoneNumber<sup>(deprecated)7+</sup>

queryContactsByPhoneNumber(phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on the specified phone number and attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-2) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| phoneNumber | string                                                | Yes  | Phone number of the contacts.                                          |
| attrs       | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries contacts based on the specified phone number, holder, and attributes. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                                | Yes  | Phone number of the contacts.                                          |
| holder      | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| attrs       | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContactsByPhoneNumber<sup>(deprecated)7+</sup>

queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on the specified phone number, holder, and attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-3) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                                 | Mandatory| Description                                                        |
| ----------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| phoneNumber | string                                                | Yes  | Phone number of the contacts.                                          |
| holder      | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| attrs       | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback    | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries contacts based on the specified phone number, holder, and attributes. This API uses a promise to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                   | Mandatory| Description                                                        |
| ----------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context     | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| phoneNumber | string                                  | Yes  | Phone number of the contacts.                                          |
| holder      | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering by default.      |
| attrs       | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.              |

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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryContactsByPhoneNumber<sup>(deprecated)7+</sup>

queryContactsByPhoneNumber(phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise&lt;Array&lt;Contact&gt;&gt;

Queries contacts based on the specified phone number, holder, and attributes. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByPhoneNumber](#contactquerycontactsbyphonenumber10-4) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name     | Type                                   | Mandatory| Description                  |
| ----------- | --------------------------------------- | ---- | ---------------------- |
| phoneNumber | string                                  | Yes  | Phone number of the contacts.    |
| holder      | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering by default.|
| attrs       | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.    |

**Return Value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.queryContactsByPhoneNumber('138xxxxxxxx', {
      holderId: 1,
      bundleName: "",
      displayName: ""
  }, {
      attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
      console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryContactsByEmail<sup>10+</sup>

queryContactsByEmail(context: Context,  email: string, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on the specified email address. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryContactsByEmail(context, 'xxx@email.com', (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryContactsByEmail<sup>(deprecated)7+</sup>

queryContactsByEmail(email: string, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries contacts based on the specified email address. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByEmail](#contactquerycontactsbyemail10) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| email    | string                                                | Yes  | Email address of the contact.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries a contact based on the specified email and holder. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| email    | string                                                | Yes  | Email address of the contact.                                          |
| holder   | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContactsByEmail<sup>(deprecated)7+</sup>

queryContactsByEmail(email: string, holder: Holder, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries a contact based on the specified email and holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByEmail](#contactquerycontactsbyemail10-1) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| email    | string                                                | Yes  | Email address of the contact.                                          |
| holder   | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries a contact based on the specified email and attributes. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| email    | string                                                | Yes  | Email address of the contact.                                          |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContactsByEmail<sup>(deprecated)7+</sup>

queryContactsByEmail(email: string, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries a contact based on the specified email and attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByEmail](#contactquerycontactsbyemail10-2) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| email    | string                                                | Yes  | Email address of the contact.                                          |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries a contact based on the specified email, holder, and attributes. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                               | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| email    | string                                                | Yes  | Email address of the contact.                                          |
| holder   | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryContactsByEmail<sup>(deprecated)7+</sup>

queryContactsByEmail(email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback&lt;Array&lt;Contact&gt;&gt;): void

Queries a contact based on the specified email, holder, and attributes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByEmail](#contactquerycontactsbyemail10-3) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| email    | string                                                | Yes  | Email address of the contact.                                          |
| holder   | [Holder](#holder)                                     | Yes  | Application that creates the contacts.                                      |
| attrs    | [ContactAttributes](#contactattributes)               | Yes  | List of contact attributes.                                          |
| callback | AsyncCallback&lt;Array&lt;[Contact](#contact)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried contacts is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries a contact based on the specified email, holder, and attributes. This API uses a promise to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type                                   | Mandatory| Description                                                        |
| ------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context | Context                                 | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| email   | string                                  | Yes  | Email address of the contact.                                          |
| holder  | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering by default.                                      |
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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryContactsByEmail<sup>(deprecated)7+</sup>

queryContactsByEmail(email: string, holder?: Holder, attrs?: ContactAttributes): Promise&lt;Array&lt;Contact&gt;&gt;

Queries a contact based on the specified email, holder, and attributes. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryContactsByEmail](#contactquerycontactsbyemail10-4) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type                                   | Mandatory| Description                  |
| ------ | --------------------------------------- | ---- | ---------------------- |
| email  | string                                  | Yes  | Email address of the contact.    |
| holder | [Holder](#holder)                       | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering by default.|
| attrs  | [ContactAttributes](#contactattributes) | No  | Contact attribute list. If this parameter is not specified, all contact attributes are queried by default.    |

**Return Value**

| Type                                           | Description                                     |
| ----------------------------------------------- | ----------------------------------------- |
| Promise&lt;Array&lt;[Contact](#contact)&gt;&gt; | Promise used to return the result, which is an array of queried contacts.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.queryContactsByEmail('xxx@email.com', {
      holderId: 1,
      bundleName: "",
      displayName: ""
  }, {
      attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
  });
  promise.then((data) => {
      console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryGroups<sup>10+</sup>

queryGroups(context: Context,  callback: AsyncCallback&lt;Array&lt;Group&gt;&gt;): void

Queries all groups of this contact. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                        |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                           | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried groups is returned. If the operation fails, an error code is returned.|

**Error codes**

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryGroups(context, (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to query Groups. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in querying Groups. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryGroups<sup>(deprecated)7+</sup>

queryGroups(callback: AsyncCallback&lt;Array&lt;Group&gt;&gt;): void

Queries all groups of this contact. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryGroups](#contactquerygroups10) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                        |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried groups is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries all groups of this contact based on the specified holder. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                        |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                                           | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| holder   | [Holder](#holder)                                 | Yes  | Application that creates the contacts.                                      |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried groups is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: Mandatory parameters are left unspecified.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
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

## contact.queryGroups<sup>(deprecated)7+</sup>

queryGroups(holder: Holder, callback: AsyncCallback&lt;Array&lt;Group&gt;&gt;): void

Queries all groups of this contact based on the specified holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryGroups](#contactquerygroups10-1) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                             | Mandatory| Description                                                        |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| holder   | [Holder](#holder)                                 | Yes  | Application that creates the contacts.                                      |
| callback | AsyncCallback&lt;Array&lt;[Group](#group)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of queried groups is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

Queries all groups of this contact based on the specified holder. This API uses a promise to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type             | Mandatory| Description                                                        |
| ------- | ----------------- | ---- | ------------------------------------------------------------ |
| context | Context           | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| holder  | [Holder](#holder) | No  | Application information for a contact. If this parameter is not specified, it is not used for group filtering by default.                                      |

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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryGroups(context, {
      holderId: 1,
      bundleName: "",
      displayName: ""
  });
  promise.then((data) => {
      console.info(`Succeeded in querying Groups. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Groups. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryGroups<sup>(deprecated)7+</sup>

queryGroups(holder?: Holder): Promise&lt;Array&lt;Group&gt;&gt;

Queries all groups of this contact based on the specified holder. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryGroups](#contactquerygroups10-2) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type             | Mandatory| Description                  |
| ------ | ----------------- | ---- | ---------------------- |
| holder | [Holder](#holder) | No  | Application information for a contact. If this parameter is not specified, it is not used for group filtering by default.|

**Return Value**

| Type                                       | Description                                   |
| ------------------------------------------- | --------------------------------------- |
| Promise&lt;Array&lt;[Group](#group)&gt;&gt; | Promise used to return the result, which is an array of groups.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.queryGroups({
      holderId: 1,
      bundleName: "",
      displayName: ""
  });
  promise.then((data) => {
      console.info(`Succeeded in querying Groups. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Groups. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryHolders<sup>10+</sup>

queryHolders(context: Context, callback: AsyncCallback&lt;Array&lt;Holder&gt;&gt;): void

Queries all applications that have created contacts. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryHolders(context, (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to query Holders. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryHolders<sup>(deprecated)7+</sup>

queryHolders(callback: AsyncCallback&lt;Array&lt;Holder&gt;&gt;): void

Queries all applications that have created contacts. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryHolders](#contactqueryholders10) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                                               | Mandatory| Description                                                        |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;Array&lt;[Holder](#holder)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, an array of the queried applications is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
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

**Permission required**: ohos.permission.READ_CONTACTS

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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryHolders(context);
  promise.then((data) => {
      console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Holders. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryHolders<sup>(deprecated)7+</sup>

queryHolders(): Promise&lt;Array&lt;Holder&gt;&gt;

Queries all applications that have created contacts. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryHolders](#contactqueryholders10-1) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Return Value**

| Type                                         | Description                                                   |
| --------------------------------------------- | ------------------------------------------------------- |
| Promise&lt;Array&lt;[Holder](#holder)&gt;&gt; | Promise used to return the result, which is an array of queried applications.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.queryHolders();
  promise.then((data) => {
      console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Holders. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryKey<sup>10+</sup>

queryKey(context: Context,  id: number, callback: AsyncCallback&lt;string&gt;): void

Queries the key of a contact based on the specified contact ID. This API uses an asynchronous callback to return the result.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                       | Mandatory| Description                                                        |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                     | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| id       | number                      | Yes  | Contact ID.                                        |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the operation is successful, the key of the queried contact is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryKey(context, /*id*/1, (err: BusinessError, data) => {
      if (err) {
          console.error(`Failed to query Key. Code: ${err.code}, message: ${err.message}`);
          return;
      }
      console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
  });
  ```

## contact.queryKey<sup>(deprecated)7+</sup>

queryKey(id: number, callback: AsyncCallback&lt;string&gt;): void

Queries the key of a contact based on the specified contact ID. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryKey](#contactquerykey10) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                       | Mandatory| Description                                                        |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| id       | number                      | Yes  | Contact ID.                                        |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the operation is successful, the key of the queried contact is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  contact.queryKey(/*id*/1, (err: BusinessError, data) => {
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

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                       | Mandatory| Description                                                        |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context                     | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| id       | number                      | Yes  | Contact ID.                                        |
| holder   | [Holder](#holder)           | Yes  | Application that creates the contacts.                                      |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the operation is successful, the key of the queried contact is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message          |
| -------- | ------------------ |
| 201      | Permission denied. |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.  |

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryKey(context, /*id*/1, {
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

## contact.queryKey<sup>(deprecated)7+</sup>

queryKey(id: number, holder: Holder, callback: AsyncCallback&lt;string&gt;): void

Queries the key of a contact based on the specified contact ID and holder. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryKey](#contactquerykey10-1) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name  | Type                       | Mandatory| Description                                                        |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| id       | number                      | Yes  | Contact ID.                                        |
| holder   | [Holder](#holder)           | Yes  | Application that creates the contacts.                                      |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the operation is successful, the key of the queried contact is returned. If the operation fails, an error code is returned.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  contact.queryKey(/*id*/1, {
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

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name | Type             | Mandatory| Description                                                        |
| ------- | ----------------- | ---- | ------------------------------------------------------------ |
| context | Context           | Yes  | Application context. For the application context of the stage model, see [Context](../apis-ability-kit/js-apis-inner-application-context.md).|
| id      | number            | Yes  | Contact ID.                                        |
| holder  | [Holder](#holder) | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering by default.                                      |

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

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  // Obtain the application context.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.queryKey(context, /*id*/1, {
      holderId: 1,
      bundleName: "",
      displayName: ""
  });
  promise.then((data) => {
      console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Key. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## contact.queryKey<sup>(deprecated)7+</sup>

queryKey(id: number, holder?: Holder): Promise&lt;string&gt;

Queries the key of a contact based on the specified contact ID and holder. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. Use [queryKey](#contactquerykey10-2) instead.

**Permission required**: ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Applications.ContactsData

**Parameters**

| Name| Type             | Mandatory| Description                  |
| ------ | ----------------- | ---- | ---------------------- |
| id     | number            | Yes  | Contact ID.  |
| holder | [Holder](#holder) | No  | Application information for a contact. If this parameter is not specified, it is not used for contact filtering by default.|

**Return Value**

| Type                 | Description                                      |
| --------------------- | ------------------------------------------ |
| Promise&lt;string&gt; | Promise used to return the result, which is the key of the queried contact.|

**Example**

  ```js
  import { BusinessError } from '@kit.BasicServicesKit';
  let promise = contact.queryKey(/*id*/1, {
      holderId: 1,
      bundleName: "",
      displayName: ""
  });
  promise.then((data) => {
      console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
      console.error(`Failed to query Key. Code: ${err.code}, message: ${err.message}`);
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
| Promise&lt;number&gt; | Promise Contact ID.|

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

```js
import { BusinessError } from '@kit.BasicServicesKit';
// Obtain the application context.
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
| Promise&lt;number&gt; | Promise Contact ID.|

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

```js
import { BusinessError } from '@kit.BasicServicesKit';
// Obtain the application context.
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
``` 

## ContactSelectionOptions<sup>10+</sup>

Defines the contact selection options.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.Contacts

|                Name              |                  Type                | Read-Only | Optional |        Description     |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| isMultiSelect<sup>10+</sup>         | boolean | No  | Yes  | Whether multiple contacts can be selected. The default value is **false**. **Atomic service API**: This API can be used in atomic services since API version 11.    |
| maxSelectable<sup>15+</sup>         | number | No  | Yes  | Maximum number of contacts that can be selected. The default value is **10000**. **Atomic service API**: This API can be used in atomic services since API version 15.    | 
| isDisplayedByName<sup>15+</sup>         | boolean | No  | Yes  | Whether to display contacts by name. The default value is **false**. **Atomic service API**: This API can be used in atomic services since API version 15.    |
| filter<sup>15+</sup>         | [ContactSelectionFilter](#contactselectionfilter15) | No  | Yes  | Contact selection filter. **Atomic service API**: This API can be used in atomic services since API version 15.    |

## ContactSelectionFilter<sup>15+</sup>

Defines the contact selection filter.

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

| Name                 | Type| Value| Description                              |
| --------------------- | ---- | ---- | ---------------------------------- |
| SHOW_FILTER    | number  | 0 | Shows only contacts that meet the filter criteria.<br/>**System capability**:SystemCapability.Applications.Contacts|
| DEFAULT_SELECT            | number  | 1 | Selects contacts that meet the filter criteria by default. <br/>**System capability**:SystemCapability.Applications.Contacts|
| SHOW_FILTER_AND_DEFAULT_SELECT | number  | 2 | Shows only contacts that meet the filter criteria and selects these contacts by default. <br/>**System capability**:SystemCapability.Applications.Contacts|

## FilterClause<sup>15+</sup>

Defines the contact filter criteria.

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

| Name                 | Type| Value| Description                                                    |
| --------------------- | ---- | ---- |----------------------------------------------------------------|
| IS_NOT_NULL    | number  | 0 | The corresponding field is not empty.<br/>**System capability**:SystemCapability.Applications.Contacts |
| EQUAL_TO            | number  | 1 | The corresponding field is equal to a value.<br/>**System capability**:SystemCapability.Applications.Contacts                   |
| NOT_EQUAL_TO | number  | 2 | The corresponding field is not equal to a value.<br/>**System capability**:SystemCapability.Applications.Contacts               |
| IN | number  | 3 | The value of the corresponding field is in an array.<br/>**System capability**:SystemCapability.Applications.Contacts           |
| NOT_IN | number  | 4 | The value of the corresponding field is not in an array.<br/>**System capability**:SystemCapability.Applications.Contacts       |
| CONTAINS | number  | 5 | The value of the corresponding field contains a certain value.<br/>**System capability**:SystemCapability.Applications.Contacts |

## DataFilter<sup>15+</sup>

Defines the contact data filter item.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.Contacts

|                Name              |                  Type                |  Read-Only | Optional  |        Description     |
| --------------------------------- | ------------------------------------- | ---- | ---- | ---------------- |
| field         | [DataField](#datafield15) | No | No | Contact data field.    |
| options         | Array\<[FilterOptions](#filteroptions15)> | No | No | Filter options.    |

## DataField<sup>15+</sup>

Enumerates contact data fields.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Applications.ContactsData

| Name                 | Type| Value| Description                  |
| --------------------- | ---- | --- |------------------------------|
| EMAIL    | number | 0 | Email of the contact.<br/>**System capability**: SystemCapability.Applications.Contacts|
| PHONE            | number | 1 | Phone number of the contact.<br/>**System capability**: SystemCapability.Applications.Contacts|
| ORGANIZATION | number | 2 | Organization of the contact.<br/>**System capability**: SystemCapability.Applications.Contacts |

## Contact

Defines a contact.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

### Constant

| Name              | Type  | Value  | Description            |
| ------------------ | ---- | ---- | ---------------- |
| INVALID_CONTACT_ID | number   | -1   | Default contact ID.|

### Attributes

|       Name       |                   Type                 | Read-Only| Optional| Description                                  |
| ----------------- | --------------------------------------- | ---- | ---- | -------------------------------------- |
| id                | number                                  | Yes  | Yes  | Contact ID.                          |
| key               | string                                  | Yes  | Yes  | Contact key.                         |
| contactAttributes | [ContactAttributes](#contactattributes) | No  | Yes  | List of contact attributes.                    |
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

Enumerates contact attributes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name                 | Description                              |
| --------------------- | ---------------------------------- |
| ATTR_CONTACT_EVENT    | Important dates such as birthday and anniversaries of the contact.|
| ATTR_EMAIL            | Email address of the contact.                |
| ATTR_GROUP_MEMBERSHIP | Groups of the contact.                    |
| ATTR_IM               | IM addresses of the contact.            |
| ATTR_NAME             | Contact name.                    |
| ATTR_NICKNAME         | Contact nickname.                    |
| ATTR_NOTE             | Contact notes.                    |
| ATTR_ORGANIZATION     | Organization of the contact.                |
| ATTR_PHONE            | Phone number of the contacts.                |
| ATTR_PORTRAIT         | Contact portrait.                    |
| ATTR_POSTAL_ADDRESS   | Postal address of the contact.                |
| ATTR_RELATION         | Relationship with the contact.                    |
| ATTR_SIP_ADDRESS      | SIP addresses of the contact. |
| ATTR_WEBSITE          | Website that stores the contact information.                    |

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

| Name            | Type  | Value  | Description            |
| ---------------- | ---- | ---- | ---------------- |
| CUSTOM_LABEL     | number    |  0    |Custom mailbox type.|
| EMAIL_HOME       | number    | 1    | Home mailbox.  |
| EMAIL_WORK       | number    | 2    | Work mailbox.  |
| EMAIL_OTHER      | number    | 3    | Other mailbox.  |
| INVALID_LABEL_ID | number    | -1   | Invalid mailbox.  |

### Attributes

| Name       |   Type  | Read-Only| Optional| Description            |
| ----------- | -------- | ---- | ---- | ---------------- |
| email       | string   | No  | No  | Email addresses      |
| labelName   | string   | No  | Yes  | Name of the mailbox type.|
| displayName | string   | No  | Yes  | Displayed name of the mailbox.|
| labelId     | number   | No  | Yes  | Mailbox type.    |

**Example**

  Create contact data in JSON format:

```js
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
| bundleName  | string | Yes  | No  | Bundle name. The value is **com.ohos.contacts**.|
| displayName | string | Yes  | Yes  | Application name.  |
| holderId    | number | No  | Yes  | Application ID.    |

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

| Name             |   Type  |  Value  | Description              |
| ----------------- | ---- | ---- | ------------------ |
| CUSTOM_LABEL      | number   | 0    | Custom event.  |
| EVENT_ANNIVERSARY | number   | 1    | Anniversary event.|
| EVENT_OTHER       | number   | 2    | Other event.    |
| EVENT_BIRTHDAY    | number   | 3    | Birthday event.    |
| INVALID_LABEL_ID  | number   | -1   | Invalid event.    |

### Attributes

|    Name  |   Type  | Read-Only| Optional| Description          |
| --------- | -------- | ---- | ---- | -------------- |
| eventDate | string   | No  | No  | Event date.  |
| labelName | string   | No  | Yes  | Event type.|
| labelId   | number   | No  | Yes  | Event type ID.    |

**Example**

  Create contact data in JSON format:

```js
let event: contact.Event = {
    eventDate: "xxxxxx"
};
```

  Or, create data by configuring an **Event** object.

```js
let event = new contact.Event();
event.eventDate = "xxxxxx";
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

| Name     |   Type  | Read-Only| Optional| Description              |
| --------- | -------- | ---- | ---- | ------------------ |
| imAddress | string   | No  | No  | IM address.    |
| labelName | string   | No  | Yes  | IM name.|
| labelId   | number   | No  | Yes  | IM ID.    |

**Example**

  Create contact data in JSON format:

```js
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

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name              |   Type  | Read-Only| Optional| Description                       |
| ------------------ | -------- | ---- | ---- | --------------------------- |
| familyName         | string   | No  | Yes  | Family name.         |
| familyNamePhonetic | string   | No  | Yes  | Family name in pinyin.     |
| fullName           | string   | No  | No  | Full name of the contact.             |
| givenName          | string   | No  | Yes  | Given name of the contact.|
| givenNamePhonetic  | string   | No  | Yes  | Given name of the contact in pinyin.         |
| middleName         | string   | No  | Yes  | Middle name of the contact.           |
| middleNamePhonetic | string   | No  | Yes  | Middle name of the contact in pinyin.       |
| namePrefix         | string   | No  | Yes  | Prefix of the contact name.         |
| nameSuffix         | string   | No  | Yes  | Suffix of the contact name.         |

**Example**

  Create contact data in JSON format:

```js
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
| nickName | string   | No  | Yes  | Contact nickname.|

**Example**

  Create contact data in JSON format:

```js
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

| Name       |   Type  | Read-Only| Optional| Description              |
| ----------- | -------- | ---- | ---- | ------------------ |
| labelName   | string   | No  | Yes  | Phone number type.|
| phoneNumber | string   | No  | No  | Phone number.        |
| labelId     | number   | No  | Yes  | Phone number ID.    |

**Example**

  Create contact data in JSON format:

```js
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

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

| Name|   Type  | Read-Only| Optional| Description          |
| ---- | -------- | ---- | ---- | -------------- |
| uri  | string   | No  | No  | Contact portrait.|

**Example**

  Create contact data in JSON format:

```js
let portrait: contact.Portrait = {
    uri: "uri"
};
```

## PostalAddress

Defines a contact's postal address.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

### Constant

| Name            |   Type  | Value  | Description                |
| ---------------- | ---- | ---- | -------------------- |
| CUSTOM_LABEL     | number   | 0    | Custom postal address type.|
| ADDR_HOME        | number   | 1    | Home address.      |
| ADDR_WORK        | number   | 2    | Work address.      |
| ADDR_OTHER       | number   | 3    | Other addresses.      |
| INVALID_LABEL_ID | number   | -1   | Invalid address type.      |

### Attributes

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
let postalAddress: contact.PostalAddress = {
    city: "city",
    postalAddress: "postalAddress"
};
```

  Or, create data by configuring a new **PostalAddress** object.

```js
let postalAddress = new contact.PostalAddress();
postalAddress.city = "city";
postalAddress.postalAddress = "postalAddress";
```

## Relation

Defines a contact's relationship.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

### Constant

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

| Name        |   Type  | Read-Only| Optional| Description          |
| ------------ | -------- | ---- | ---- | -------------- |
| labelName    | string   | No  | Yes  | Relationship type.|
| relationName | string   | No  | No  | Relationship name.    |
| labelId      | number   | No  | Yes  | Relationship ID.    |

**Example**

  Create contact data in JSON format:

```js
let relation: contact.Relation = {
    relationName: "relationName",
    labelId: contact.Relation.RELATION_ASSISTANT
};
```

  Or, create data by configuring a new **Relation** object.

```js
let relation = new contact.Relation();
relation.relationName = "relationName";
relation.labelId = contact.Relation.RELATION_ASSISTANT;
```

## SipAddress

Defines a contact's SIP address.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Applications.ContactsData

### Constant

| Name            |   Type  | Value  | Description                               |
| ---------------- | ---- | ---- | ----------------------------------- |
| CUSTOM_LABEL     | number   | 0    | Custom SIP address.|
| SIP_HOME         | number   | 1    | Home SIP address.  |
| SIP_WORK         | number   | 2    | Work SIP address.  |
| SIP_OTHER        | number   | 3    | Other SIP address.  |
| INVALID_LABEL_ID | number   | -1   | Invalid SIP address.  |

### Attributes

| Name      |   Type  | Read-Only| Optional| Description                             |
| ---------- | -------- | ---- | ---- | --------------------------------- |
| labelName  | string   | No  | Yes  | SIP address type.|
| sipAddress | string   | No  | No  | SIP address.        |
| labelId    | number   | No  | Yes  | SIP address ID.    |

**Example**

  Create contact data in JSON format:

```js
let sipAddress: contact.SipAddress = {
    sipAddress: "sipAddress"
};
```

  Or, create data by configuring a new **SipAddress** object.

```js
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
let website: contact.Website = {
    website: "website"
};
```
