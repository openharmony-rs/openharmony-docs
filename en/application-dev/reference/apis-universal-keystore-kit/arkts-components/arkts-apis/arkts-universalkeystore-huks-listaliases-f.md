# listAliases

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## listAliases

```TypeScript
function listAliases(options: HuksOptions): Promise<HuksListAliasesReturnResult>
```

Lists key aliases. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Parameters for listing key aliases. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksListAliasesReturnResult](arkts-universalkeystore-huks-hukslistaliasesreturnresult-i.md)&gt; | Promise that returns the operation result. If the operation is successful, **keyAliases** of **HuksListAliasesReturnResult** is the obtained key aliases. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [12000004](../errorcode-huks.md#12000004-file-error) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the group id specified by the access group tag is invalid<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit'

async function testListAliases() {
  let queryProperties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_DE
    }
  ];
  let queryOptions: huks.HuksOptions = {
    properties: queryProperties
  };

  try{
    await huks.listAliases(queryOptions)
      .then((data) => {
      console.info(`promise: listAliases success, data: ` + JSON.stringify(data));
    });
  } catch (error) {
    console.error(`promise: listAliases failed, errCode : ${error.code}, errMsg : ${error.message}`);
  }
}
```
