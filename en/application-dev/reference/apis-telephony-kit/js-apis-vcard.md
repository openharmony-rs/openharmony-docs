# @ohos.telephony.vcard (VCard)
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @Fanyl8-->
<!--Designer: @ghxbob-->
<!--Tester: @weitiantian-->
<!--Adviser: @zhang_yixin13-->

VCard is a file format standard for electronic business cards. It contains information such as names, addresses, phone numbers, URLs, logos, and photos. The VCard module provides the VCard management functions, including importing VCard files to the contact database and exporting contact data to VCard files.

>**NOTE**
>
>The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { vcard } from '@kit.TelephonyKit';
```

## vcard.importVCard

importVCard\(context: Context, filePath: string, accountId: number, callback: AsyncCallback\<void\>\): void

Imports a VCard file (that is, **.vcf** file) to the contact database. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**  | **Type**                       | **Mandatory**| **Description**                                  |
| -------- | --------------------------- | ---- | -------------------------------------- |
| Context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)   | Yes  | Application context.|
| filePath   | string                      | Yes  | URL of the vcard file (VCF).|
| accountId | number | Yes                 | Contact account ID.|
| callback | AsyncCallback&lt;void&gt; | Yes  |Callback used to return the result.  |

**Error codes**:

For details about the error codes, see[ohos.telephony (Telephony) Error Codes](errorcode-telephony.md).

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
        let accountId: number = 0;
        vcard.importVCard(this.context, filePath, accountId, (err: BusinessError) => {
            console.error(`callback: err->${JSON.stringify(err)}`);
        });
    }
}

```

## vcard.importVCard

importVCard\(context: Context, filePath: string, accountId?: number\): Promise\<void\>

Imports a VCard file (that is, **.vcf** file) to the contact database. This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**  | Type                       | **Mandatory**| **Description**                                  |
| -------- | --------------------------- | ---- | -------------------------------------- |
| Context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)      | Yes  | Application context.|
| filePath   | string                      | Yes  | URL of the vcard file (VCF).|
| accountId   | number                      | Yes  | Contact account ID.|

**Return value**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<void\> | Promise used to return the operation result.|

**Error codes**:

For details about the error codes, see[ohos.telephony (Telephony) Error Codes](errorcode-telephony.md).

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

Imports a VCard file (that is, **.vcf** file) to the contact database. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**| Type  | **Mandatory**| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| Context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)  | Yes  | Application context.|
| filePath | string | Yes  |  URL of the vcard file (VCF).|
| callback | AsyncCallback&lt;void&gt; | Yes  |Callback used to return the result.|

**Error codes**:

For details about the error codes, see[ohos.telephony (Telephony) Error Codes](errorcode-telephony.md).

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

exportVCard\(context: Context, predicates: dataSharePredicates.DataSharePredicates, options: VCardBuliderOptions, callback: AsyncCallback\<string\>\): void

Export contacts as a vcard file (VCF). This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**  | Type                       | **Mandatory**| Description                                  |
| -------- | --------------------------- | ---- | -------------------------------------- |
| Context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)                    | Yes  | Application context.|
| predicates| [dataSharePredicates.DataSharePredicates](../../../application-dev/reference/apis-arkdata/js-apis-data-dataSharePredicates.md)| Yes  | Query statement.|
|  options  | VCardBuilderOptions | No  | VCard version and encoding type.|
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to Address of the generated vcard file (VCF).                            |

**Error codes**:

For details about the error codes, see[ohos.telephony (Telephony) Error Codes](errorcode-telephony.md).

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
        vcard.exportVCard(this.context, predicates, options, (err: BusinessError, data: string) => {
            console.error(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
        });
    }
}

```

## vcard.exportVCard

exportVCard\(context: Context, predicates: dataSharePredicates.DataSharePredicates, options?: VCardBuilderOptions\): Promise\<string\>

Export contacts as a vcard file (VCF). This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**  | Type                       | **Mandatory**| Description                                  |
| -------- | --------------------------- | ---- | -------------------------------------- |
| Context   | [Context](../apis-ability-kit/js-apis-inner-application-context.md)               | Yes  | Application context.|
| predicates | [dataSharePredicates.DataSharePredicates](../../../application-dev/reference/apis-arkdata/js-apis-data-dataSharePredicates.md) | Yes  | Query statement.|
| options   | VCardBuilderOptions | Yes  | VCard version and encoding type.|  

**Return value**

| Type                 | Description                              |
| --------------------- | ---------------------------------- |
| Promise\<string\> | Promise used to return the operation result.|

**Error codes**:

For details about the error codes, see[ohos.telephony (Telephony) Error Codes](errorcode-telephony.md).

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

Export contacts as a vcard file (VCF). This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.WRITE_CONTACTS and ohos.permission.READ_CONTACTS

**System capability**: SystemCapability.Telephony.CoreService

**Parameters**

| **Name**| Type  | **Mandatory**| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| Context      | [Context](../apis-ability-kit/js-apis-inner-application-context.md)     | Yes  | Application context.|
| predicates   | [dataSharePredicates.DataSharePredicates](../../../application-dev/reference/apis-arkdata/js-apis-data-dataSharePredicates.md) | Yes  | Query statement.|
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to Address of the generated vcard file (VCF).|

**Error codes**:

For details about the error codes, see[ohos.telephony (Telephony) Error Codes](errorcode-telephony.md).

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
