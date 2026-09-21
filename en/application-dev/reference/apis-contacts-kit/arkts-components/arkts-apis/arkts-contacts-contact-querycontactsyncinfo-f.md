# queryContactSyncInfo

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## queryContactSyncInfo

```TypeScript
function queryContactSyncInfo(context: Context): Promise<Array<ContactSyncInfo>>
```

Queries information about ongoing contact synchronization for the calling application.

If the returned contact synchronization information is empty, the invoking party does not synchronize contacts or the contact synchronization is complete.

**Since:** 26.0.0

**Required permissions:** ohos.permission.READ_CONTACTS

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.ContactsData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Indicates the context of the application or capability. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ContactSyncInfo](arkts-contacts-contact-contactsyncinfo-i.md)&gt;&gt; | Returns the array of contacts synchronization information for the calling application. Returns null if no contacts are being synchronized. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [16700001](../errorcode-contacts.md#16700001-system-internal-error) | General error. |

**Examples**

> NOTE
> 
> In the examples of this document, UIAbilityContext is obtained through this.context, where this represents a UIAbility instance inherited from UIAbility. If you need to use the capabilities provided by UIAbilityContext in the UI, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// Obtain the context within the component.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
const syncInfoList: contact.ContactSyncInfo[] = await contact.queryContactSyncInfo(context) as contact.ContactSyncInfo[];
console.info('queryContactSyncInfo syncInfoList '  + JSON.stringify(syncInfoList));
```
