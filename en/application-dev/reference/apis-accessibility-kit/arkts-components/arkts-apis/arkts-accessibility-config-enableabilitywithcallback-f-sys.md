# enableAbilityWithCallback (System API)

## Modules to Import

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## enableAbilityWithCallback

```TypeScript
function enableAbilityWithCallback(
    name: string,
    capability: Array<accessibility.Capability>,
    connectCallback: ConnectCallback
  ): Promise<void>
```

Enables an accessibility extension and specifies [ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md) as the callback for disconnection events of the accessibility extension. This API uses a promise to return the result.

When the accessibility extension process is abnormally disconnected, the onDisconnect callback of ConnectCallback will be triggered. This API must be used together with [config.disableAbility](arkts-accessibility-config-disableability-f-sys.md).

**Since:** 23

**Required permissions:** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the accessibility extension ability, in the format of 'bundleName/abilityName'. |
| capability | Array&lt;[accessibility.Capability](arkts-accessibility-accessibility-capability-t.md)&gt; | Yes | Capabilities of the auxiliary extension ability. |
| connectCallback | [ConnectCallback](arkts-accessibility-config-connectcallback-i-sys.md) | Yes | Callback invoked when an accessibility extension app is disconnected, used to listen for disconnection events of the accessibility extension. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [9300001](../errorcode-accessibility.md#9300001-invalid-bundle-name-or-ability-name) | Invalid bundle name or ability name. |
| [9300002](../errorcode-accessibility.md#9300002-target-ability-already-enabled) | Target ability already enabled. |

**Examples**

```TypeScript
import { accessibility, config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let name: string = 'com.ohos.example/axExtension';
let capability: accessibility.Capability[] = ['retrieve'];
let connectCallback: config.ConnectCallback = {
  onDisconnect: () => {
    console.info(`Ability is disconnected.`);
  }
};

config.enableAbilityWithCallback(name, capability, connectCallback).then(() => {
  console.info(`Succeeded in enabling ability, name is ${name}, capability is ${capability}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to enable ability. Code: ${err.code}, message: ${err.message}`);
});
```
