# syncContacts

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## syncContacts

```TypeScript
function syncContacts(context: Context, mode: ContactSyncMode, progress: ContactSyncProgress, contacts: Array<Contact>): Promise<Array<number>>
```

Synchronizes multiple contacts to the contacts database in batches.

A maximum of 400 contacts can be synchronized at a time. The caller must be running in the foreground.

**Since:** 26.0.0

**Required permissions:** ohos.permission.WRITE_CONTACTS

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Indicates the context of the application or capability. |
| mode | [ContactSyncMode](arkts-contacts-contact-contactsyncmode-e.md) | Yes | Indicates the type of contact synchronization mode. |
| progress | [ContactSyncProgress](arkts-contacts-contact-contactsyncprogress-i.md) | Yes | Indicates the information about the contact synchronization progress. |
| contacts | Array&lt;[Contact](arkts-contacts-contact-contact-c.md)&gt; | Yes | Indicates the array of contact information to be synchronized into the database. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Returns the array of contacts creation results. Valid contact ID (which can be obtained by getId) indicates that the creation was successful. [INVALID_CONTACT_ID](arkts-contacts-contact-contact-c.md#invalid_contact_id) indicates the creation failed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [16700001](../errorcode-contacts.md#16700001-system-internal-error) | General error. |
| [16700002](../errorcode-contacts.md#16700002-parameter-check-failed) | Invalid parameter value. |
| [16700003](../errorcode-contacts.md#16700003-background-service-calling-prohibited) | Background usage is prohibited. |
| [16700004](../errorcode-contacts.md#16700004-number-of-contacts-exceeds-the-limit) | The number of contacts exceeds the limit. |
| [16700103](../errorcode-contacts.md#16700103-operation-canceled) | User cancel. |

**Examples**

> NOTE
> 
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
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
