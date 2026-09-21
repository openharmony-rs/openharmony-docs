# saveToExistingContactViaUI

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## saveToExistingContactViaUI

```TypeScript
function saveToExistingContactViaUI(context: Context, contact: Contact): Promise<number>
```

Saves the information to an existing contact through UI interaction.. This API uses a promise to return the result.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Applications.Contacts

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Indicates the context of application or capability. |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | Yes | Indicates the contact information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result, which is the contact ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |
| [801](../../errorcode-universal.md#801-api-not-supported) | The specified SystemCapability name was not found. |
| [16700001](../errorcode-contacts.md#16700001-system-internal-error) | General error. |
| [16700101](../errorcode-contacts.md#16700101-database-query-failed) | Failed to get value from contacts data. |
| [16700102](../errorcode-contacts.md#16700102-database-data-addition-deletion-or-modification-failed) | Failed to set value to contacts data. |
| [16700103](../errorcode-contacts.md#16700103-operation-canceled) | User cancel. |

**Examples**

> NOTE
> 
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
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
