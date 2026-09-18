# disableSilentProxy (System API)

## Modules to Import

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## disableSilentProxy

```TypeScript
function disableSilentProxy(context: Context, uri?: string): Promise<void>
```

Disables silent access. This API uses a promise to return the result.

Observe the following when using this API:

- The data provider calls this API to disable silent access.  
- Whether silent access is disabled is determined based on the return value of this API and the  
**isSilentProxyEnable** field in the [data_share_config.json](../../../database/share-data-by-datashareextensionability-sys.md) file together.  
- If silent access is disabled for a URI using this API, the setting takes effect when the related  
**datashareHelper** API is called. Otherwise, the setting of **isSilentProxyEnable** in the **data_share_config.json** file is used to determine whether to disable silent access.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Consumer

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the application. |
| uri | string | No | URI of the data, for which silent access is to be disabled.Global setting: If **uri** is **undefined** or **null** or is not specified, all the previous settings will be cleared and silent access will be disabled globally for the data provider.URI-specific setting: If a URI is specified, silent access to the specified URI will be disabled.When datashareHelper APIs are called, the URI-specific setting is preferentially applied. If no match is found, the global setting is applied.URI format: **datashare:///{bundleName}/{moduleName}/{storeName}/{tableName}** |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 19 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [15700011](../errorcode-datashare.md#15700011-uri-does-not-exist) | The URI does not exist. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let uri = "datashare:///com.acts.datasharetest/entry/DB00/TBL00?Proxy=true";
    let context = this.context;
    dataShare.disableSilentProxy(context, uri).then(() => {
      console.info("disableSilentProxy succeed");
    }).catch((err: BusinessError) => {
      console.error(`Failed to disable silent proxy. Code: ${err.code}, message: ${err.message}`);
    });
  }
}
```
