# @ohos.telephony.vcard (VCard)
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @Fanyl8-->
<!--Designer: @ghxbob-->
<!--Tester: @weitiantian-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=14047a635a9cc5f9823087396220870197d8184c translatedAt=2026-11-03T04:10:35.738Z pushedAt=2026-11-03T10:44:19.517Z nl=1 -->

VCard is a file format standard for electronic name cards. It can contain information such as name, address, phone number, URL, logo, and photo. The VCard module provides VCard capabilities, including importing VCard files into the contact database and exporting contact data as VCard files.

>**NOTE**
>
>The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { vcard } from '@kit.TelephonyKit';
```

## vcard.importVCard

importVCard\(context: Context, filePath: string, accountId: number, callback: AsyncCallback\<void\>\): void

Imports a VCard file into the contact database. This API is applicable to scenarios such as batch importing contacts after receiving VCard files from other devices or applications, and restoring contact data. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**  | Type                       | **Mandatory**| Description                                  |
| -------- | --------------------------- | ---- | -------------------------------------- |
| context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)   | Yes  | Application context.|
| filePath   | string                      | Yes   | File address of the VCF (VCard file). |
| accountId | number | Yes                 | Contact account ID.|
| callback | AsyncCallback&lt;void&gt; | Yes  |Callback used to return the result.  |

**Error codes**:

For details about the error codes, see [Telephony Error Codes](errorcode-telephony.md).

| ID|                 Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example:**

```ts
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { vcard } from '@kit.TelephonyKit';

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        let filePath: string = '/data/storage/vcf/contacts.vcf';
        let accountId: number = 0;
        vcard.importVCard(this.context, filePath, accountId, (err: BusinessError) => {
            console.error(`callback: err->${JSON.stringify(err)}`);
        });
    }
}

```

## vcard.importVCard

importVCard\(context: Context, filePath: string, accountId?: number\): Promise\<void\>

Imports a VCard file into the contact database. This API is applicable to scenarios such as batch importing contacts after receiving VCard files from other devices or applications, and restoring contact data. This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**  | Type                       | **Mandatory**| Description                                  |
| -------- | --------------------------- | ---- | -------------------------------------- |
| context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)      | Yes  | Application context.|
| filePath   | string                      | Yes   | File address of the VCF (VCard file). |
| accountId   | number                      | No   | ID of the contact account. The default account is used if this parameter is not passed. |

**Return value**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<void\> | Promise that returns no value. |

**Error codes**:

For details about the error codes, see [Telephony Error Codes](errorcode-telephony.md).

| ID|                 Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example:**

```ts
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { vcard } from '@kit.TelephonyKit';

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        let filePath: string = '/data/storage/vcf/contacts.vcf';
        let accountId: number = 0;
        vcard.importVCard(this.context, filePath, accountId).then(() => {
            console.info(`importVCard success.`);
        }).catch((err: BusinessError) => {
            console.error(`importVCard failed, promise: err->${JSON.stringify(err)}`);
        });
    }
}
```

## vcard.importVCard
importVCard\(context: Context, filePath: string, callback: AsyncCallback\<void\>\): void

Imports a VCard file into the contact database. This API is applicable to scenarios such as batch importing contacts after receiving VCard files from other devices or applications, and restoring contact data. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**| Type  | **Mandatory**| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)  | Yes  | Application context.|
| filePath | string | Yes | VCF (VCard file) file address. |
| callback | AsyncCallback&lt;void&gt; | Yes  |Callback used to return the result.|

**Error codes**:

For details about the error codes, see [Telephony Error Codes](errorcode-telephony.md).

| ID|                 Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example:**

```ts
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

## vcard.exportVCard

exportVCard\(context: Context, predicates: dataSharePredicates.DataSharePredicates, options: VCardBuilderOptions, callback: AsyncCallback\<string\>\): void

Exports contacts as a VCF (VCard file) file. This API is applicable to scenarios such as backing up contact data, migrating contacts across devices, and sharing contacts through files. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**  | Type                       | **Mandatory**| Description                                  |
| -------- | --------------------------- | ---- | -------------------------------------- |
| context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)                    | Yes  | Application context.|
| predicates| [dataSharePredicates.DataSharePredicates](../../../application-dev/reference/apis-arkdata/js-apis-data-dataSharePredicates.md)| Yes   | Query statement used to filter the contact data to be exported. |
|  options  | VCardBuilderOptions | Yes  | VCard version and encoding type.|
| callback | AsyncCallback&lt;string&gt; | Yes   | Callback used to return the address of the generated VCF (VCard file) file.                             |

**Error codes**:

For details about the error codes, see [Telephony Error Codes](errorcode-telephony.md).

| ID|                 Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example:**

```ts
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { vcard } from '@kit.TelephonyKit';
import { dataSharePredicates } from '@kit.ArkData';

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        let predicates = new dataSharePredicates.DataSharePredicates();
        predicates.equalTo('NAME', 'Rose');
        let options: vcard.VCardBuilderOptions = {
            cardType: vcard.VCardType.VERSION_21,
            charset: 'UTF-8'
        };
        vcard.exportVCard(this.context, predicates, options, (err: BusinessError, data: string) => {
            console.error(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
        });
    }
}

```

## vcard.exportVCard

exportVCard\(context: Context, predicates: dataSharePredicates.DataSharePredicates, options?: VCardBuilderOptions\): Promise\<string\>

Exports contacts as a VCF (VCard file) file. This API is applicable to scenarios such as backing up contact data, migrating contacts across devices, and sharing contacts through files. This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**  | Type                       | **Mandatory**| Description                                  |
| -------- | --------------------------- | ---- | -------------------------------------- |
| context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)               | Yes  | Application context.|
| predicates | [dataSharePredicates.DataSharePredicates](../../../application-dev/reference/apis-arkdata/js-apis-data-dataSharePredicates.md) | Yes | Query statement used to filter the contact data to be exported. |
| options   | VCardBuilderOptions | No  | VCard version and encoding type.|

**Return value**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<string\> | Promise used to return the file address of the generated VCF (VCard file). |

**Error codes**:

For details about the error codes, see [Telephony Error Codes](errorcode-telephony.md).

| ID|                 Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example:**

```ts
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { vcard } from '@kit.TelephonyKit';
import { dataSharePredicates } from '@kit.ArkData';

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        let predicates = new dataSharePredicates.DataSharePredicates();
        predicates.equalTo("NAME", "Rose");
        let options: vcard.VCardBuilderOptions = {
            cardType: vcard.VCardType.VERSION_21,
            charset: "UTF-8"
        };
        vcard.exportVCard(this.context, predicates, options).then(() => {
            console.info(`exportVCard success.`);
        }).catch((err: BusinessError) => {
            console.error(`exportVCard failed, promise: err->${JSON.stringify(err)}`);
        });
    }
}
```

## vcard.exportVCard

exportVCard\(context: Context, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback\<string\>\): void

Exports contacts as a VCF (VCard file) file. This API is applicable to scenarios such as backing up contact data, migrating contacts across devices, and sharing contacts through files. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**| Type  | **Mandatory**| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| context      | [Context](../apis-ability-kit/js-apis-inner-application-context.md)     | Yes  | Application context.|
| predicates   | [dataSharePredicates.DataSharePredicates](../../../application-dev/reference/apis-arkdata/js-apis-data-dataSharePredicates.md) | Yes   | Query statement used to filter the contacts to export.  |
| callback | AsyncCallback&lt;string&gt; | Yes   | Callback used to return the address of the generated VCF (VCard file) file.|

**Error codes**:

For details about the error codes, see [Telephony Error Codes](errorcode-telephony.md).

| ID|                 Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error.                               |

**Example:**

```ts
import { window } from '@kit.ArkUI';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { vcard } from '@kit.TelephonyKit';
import { dataSharePredicates } from '@kit.ArkData';

class EntryAbility extends UIAbility {
    onWindowStageCreate(windowStage: window.WindowStage) {
        let predicates = new dataSharePredicates.DataSharePredicates();
        predicates.equalTo("NAME", "Rose");

        vcard.exportVCard(this.context, predicates, (err: BusinessError, data: string) => {
            console.error(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
        });
    }
}

```
## VCardBuilderOptions

Defines the VCard information.

**System capability**: SystemCapability.Telephony.CoreService

| Name        | Type  | Read-Only| Optional|    Description   |
| ------------ | ------ | ----|----| ---------- |
| cardType     | [VCardType](#vcardtype) |  No| Yes | VCard version type (the default value is **VERSION_21**).|
| charset       | string |  No|Yes | VCard encoding type. The default value is **UTF-8**.    |

## VCardType

Enumerates VCard versions.

**System capability**: SystemCapability.Telephony.CoreService

| Name           | Value  | Description      |
| --------------- | ---- | ---------- |
| VERSION_21 | 0 | VCard 2.1.|
| VERSION_30 | 1 | VCard 3.0.|
| VERSION_40 | 2 | VCard 4.0.|