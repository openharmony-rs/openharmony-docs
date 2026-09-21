# importContactsViaUI

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## importContactsViaUI

```TypeScript
function importContactsViaUI(context: Context, contacts: Array<Contact>): Promise<Array<number>>
```

Imports multiple contacts through UI interaction.

A maximum of 100 contacts can be imported at a time. Importing contact portraits is not supported.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.Contacts

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Indicates the context of the application or capability. |
| contacts | Array&lt;[Contact](arkts-contacts-contact-contact-c.md)&gt; | Yes | Indicates the array of contact information to be imported into the database. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Returns the array of contacts creation results. Valid contact ID (which can be obtained by getId) indicates that the creation was successful. [INVALID_CONTACT_ID](arkts-contacts-contact-contact-c.md#invalid_contact_id) indicates the creation failed. -2 indicates that the user has not selected this contact. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | The specified SystemCapability name was not found. |
| [16700001](../errorcode-contacts.md#16700001-system-internal-error) | General error. |
| [16700002](../errorcode-contacts.md#16700002-parameter-check-failed) | Invalid parameter value. |
| [16700004](../errorcode-contacts.md#16700004-number-of-contacts-exceeds-the-limit) | The number of contacts exceeds the limit. |
| [16700103](../errorcode-contacts.md#16700103-operation-canceled) | User cancel. |

**Examples**

> NOTE
> 
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
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
