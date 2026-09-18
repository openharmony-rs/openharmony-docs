# grantUriPermissionByKeyAsCaller (System API)

## Modules to Import

```TypeScript
import { uriPermissionManager } from '@kit.AbilityKit';
```

## grantUriPermissionByKeyAsCaller

```TypeScript
function grantUriPermissionByKeyAsCaller(key: string, flag: wantConstant.Flags, callerTokenId: number, targetTokenId: number): Promise<void>
```

Grants the URI access permission of the specified application to the target application through the unique key of the Unified Data Management Framework (UDMF) data. The permission will be revoked after the target application exits. This API uses a promise to return the result. This API can be properly called only on phones, 2-in-1 devices, and tablets. If it is called on other device types, error code 801 is returned. **System API**: This is a system API.

**Since:** 20

**Required permissions:** ohos.permission.GRANT_URI_PERMISSION_AS_CALLER

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Unique key of the target UDMF data. The key must be created by the application (corresponding to **callerTokenId**) through [unifiedDataChannel.insertData](../../apis-arkdata/arkts-apis/arkts-arkdata-unifieddatachannel-insertdata-f.md), and the written data must be the URIs of the authorized files.<br>Currently, only the keys of the [UDMF data channels](../../apis-arkdata/arkts-apis/arkts-arkdata-unifieddatachannel-intention-e.md) of the **SYSTEM_SHARE**, **PICKER**, and **MENU** types are supported. For details about how to create and use a key, see [Sharing Data via Unified Data Channels](../../../database/unified-data-channels.md). |
| flag | [wantConstant.Flags](arkts-ability-wantconstant-flags-e.md) | Yes | Read or write permission on the file to grant. The options are as follows:<br>- **FLAG_AUTH_READ_URI_PERMISSION**: read permission.<br>- **FLAG_AUTH_WRITE_URI_PERMISSION**: write permission. |
| callerTokenId | number | Yes | Identity of the caller application. You can obtain the value from the **ohos.aafwk.param.callerToken** field in [want](arkts-ability-app-ability-want-want-c.md). |
| targetTokenId | number | Yes | Identity of the target application, which can be obtained through [bundleManager.getApplicationInfo](arkts-ability-bundlemanager-getapplicationinfo-f-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000058](../errorcode-ability.md#16000058-specified-uri-flag-is-invalid) | Invalid URI flag. |
| [16000060](../errorcode-ability.md#16000060-sandbox-applications-cannot-grant-uri-permission) | A sandbox application cannot grant URI permission. |
| [16000091](../errorcode-ability.md#16000091-failed-to-obtain-a-file-uri-by-key) | Failed to get the file URI from the key. |
| [16000092](../errorcode-ability.md#16000092-no-permission-to-authorize-uri) | No permission to authorize the URI. |
| [16000093](../errorcode-ability.md#16000093-invalid-caller-token-id) | The caller token ID is invalid. |
| [16000094](../errorcode-ability.md#16000094-invalid-target-token-id) | The target token ID is invalid. |

**Examples**

```TypeScript
// The bundle name of the caller application is com.example.caller.
// Index.ets
import { common, Want, wantConstant } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)

        Button('Share File')
          .onClick(() => {
            // You can generate a key using unifiedDataChannel.insertData.
            let udKey: string = 'udmf://SystemShare/com.example.caller/ap\\t5kKMYTOSHBh9\\f1@817VnBBvxI[e';
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
            let want: Want = {
              bundleName: 'com.example.test',
              abilityName: 'EntryAbility',
              parameters: {
                [wantConstant.Params.ABILITY_UNIFIED_DATA_KEY]: udKey
              }
            };
            context.startAbility(want);
          })
      }
    }
  }
}
```

```TypeScript
// The bundle name of the API caller is com.example.test.
// EntryAbility.ets
import { AbilityConstant, UIAbility, Want, wantConstant, uriPermissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let udKey: string = want.parameters?.[wantConstant.Params.ABILITY_UNIFIED_DATA_KEY] as string;
    let callerTokenId: number = want.parameters?.['ohos.aafwk.param.callerToken'] as number;
    AppStorage.setOrCreate('udKey', udKey);
    AppStorage.setOrCreate('callerTokenId', callerTokenId);
  }

  onForeground(): void {
    try {
      let udKey: string = AppStorage.get<string>('udKey') as string;
      let callerTokenId: number = AppStorage.get<number>('callerTokenId') as number;
      // You can obtain targetTokenId by calling bundleManager.getApplicationInfo.
      // Assume that the obtained targetTokenId is 1001.
      let targetTokenId: number = 1001;

      uriPermissionManager.grantUriPermissionByKeyAsCaller(udKey,
        wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION, callerTokenId, targetTokenId)
        .then(() => {
          console.info('grantUriPermissionByKeyAsCaller succeeded.');
        }).catch((error: BusinessError) => {
        console.error('grantUriPermissionByKeyAsCaller failed: ' + JSON.stringify(error));
      });
    } catch (error) {
      console.error('grantUriPermissionByKeyAsCaller failed: ' + JSON.stringify(error));
    }
  }
}
```
