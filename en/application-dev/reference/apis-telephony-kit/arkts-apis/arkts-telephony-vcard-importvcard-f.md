# importVCard

## Modules to Import

```TypeScript
import { vcard } from '@kit.TelephonyKit';
```

## importVCard

```TypeScript
function importVCard(context: Context, filePath: string, accountId: number, callback: AsyncCallback<void>): void
```

Imports a VCard file (that is, **.vcf** file) to the contact database. This API uses an asynchronous callback to return the result.

**Since:** 23

**Required permissions:** ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. |
| filePath | string | Yes | URL of the vcard file (VCF). |
| accountId | number | Yes | Contact account ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs.<br>**Applicable version:** 11 - 22 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { vcard } from '@kit.TelephonyKit';

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        let filePath: string = "/data/storage/vcf/contacts.vcf";
        let accountId: number = 0;
        vcard.importVCard(this.context, filePath, accountId, (err: BusinessError) => {
            console.error(`callback: err->${JSON.stringify(err)}`);
        });
    }
}
```


<a id="importvcard-1"></a>

## importVCard

```TypeScript
function importVCard(context: Context, filePath: string, accountId?: number): Promise<void>
```

Imports a VCard file (that is, **.vcf** file) to the contact database. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. |
| filePath | string | Yes | URL of the vcard file (VCF). |
| accountId | number | No | Contact account ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the operation result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs.<br>**Applicable version:** 11 - 22 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { vcard } from '@kit.TelephonyKit';

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        let filePath: string = "/data/storage/vcf/contacts.vcf";
        let accountId: number = 0;
        vcard.importVCard(this.context, filePath, accountId).then(() => {
            console.info(`importVCard success.`);
        }).catch((err: BusinessError) => {
            console.error(`importVCard failed, promise: err->${JSON.stringify(err)}`);
        });
    }
}
```


<a id="importvcard-2"></a>

## importVCard

```TypeScript
function importVCard(context: Context, filePath: string, callback: AsyncCallback<void>): void
```

Imports a VCard file (that is, **.vcf** file) to the contact database. This API uses an asynchronous callback to return the result.

**Since:** 23

**Required permissions:** ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. |
| filePath | string | Yes | URL of the vcard file (VCF). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs.<br>**Applicable version:** 11 - 22 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |

**Examples**

```TypeScript
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { vcard } from '@kit.TelephonyKit';

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        let filePath: string = "/data/storage/vcf/contacts.vcf";
        vcard.importVCard(this.context, filePath, (err: BusinessError) => {
            console.error(`callback: err->${JSON.stringify(err)}`);
        });
    }
}
```
