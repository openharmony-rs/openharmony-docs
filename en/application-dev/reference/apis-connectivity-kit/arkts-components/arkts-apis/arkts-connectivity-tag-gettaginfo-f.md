# getTagInfo

## Modules to Import

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## getTagInfo

```TypeScript
function getTagInfo(want: Want): TagInfo
```

Obtains **TagInfo** from **Want**, which is initialized by the NFC service and contains the attributes required by **TagInfo**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NFC.Tag

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Data obtained from the parameters of the **onCreate** entry function when an ability is dispatched. |

**Return value:**

| Type | Description |
| --- | --- |
| [TagInfo](arkts-connectivity-tag-taginfo-i.md) | **TagInfo** object obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
