# createLocalWantAgent (System API)

## Modules to Import

```TypeScript
import { wantAgent, WantAgent } from '@kit.AbilityKit';
```

## createLocalWantAgent

```TypeScript
function createLocalWantAgent(info: LocalWantAgentInfo): WantAgent
```

Create a local WantAgent object. The WantAgent created by this interface stores data on the client side and is not managed by the WantAgent servcer. If this WantAgent object is passed across processes, its contained data will be serialized and transmitted to the target process.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [LocalWantAgentInfo](arkts-ability-wantagent-localwantagentinfo-t-sys.md) | Yes | Information about the local WantAgent object to create. |

**Return value:**

| Type | Description |
| --- | --- |
| [WantAgent](arkts-ability-wantagent-t.md) | Returns the created WantAgent. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |

**Examples**

```TypeScript
import { wantAgent, Want } from '@kit.AbilityKit';
import type { WantAgent } from '@kit.AbilityKit';

// Declare a wantAgent object.
let wantAgentData: WantAgent;
// Create a LocalWantAgentInfo object.
let localWantAgentInfo: wantAgent.LocalWantAgentInfo = {
  wants: [
    {
      deviceId: 'deviceId',
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility',
      action: 'action1',
      entities: ['entity1'],
      type: 'MIMETYPE',
      uri: 'key={true,true,false}',
      parameters:
      {
        mykey0: 2222,
        mykey1: [1, 2, 3],
        mykey2: '[1, 2, 3]',
        mykey3: 'ssssssssssssssssssssssssss',
        mykey4: [false, true, false],
        mykey5: ['qqqqq', 'wwwwww', 'aaaaaaaaaaaaaaaaa'],
        mykey6: true,
      }
    } as Want
  ],
  operationType: wantAgent.OperationType.START_ABILITY,
  requestCode: 0
};
// Create a local WantAgent object.
try {
  wantAgentData = wantAgent.createLocalWantAgent(localWantAgentInfo);
} catch (err) {
  console.error('createLocalWantAgent failed');
}
```
