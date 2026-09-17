# isLocalWantAgent (System API)

## Modules to Import

```TypeScript
import { wantAgent, WantAgent } from '@kit.AbilityKit';
```

## isLocalWantAgent

```TypeScript
function isLocalWantAgent(agent: WantAgent): boolean
```

Checks whether the specified WantAgent is local.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-t.md) | Yes | Indicates the WantAgent. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the WantAgent is local. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System app. Interface caller is not a system app. |

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

// Create a WantAgent object and check whether it is local.
try {
  wantAgentData = wantAgent.createLocalWantAgent(localWantAgentInfo);
  // Check whether the WantAgent instance is a local instance.
  let isLocal: boolean = wantAgent.isLocalWantAgent(wantAgentData);
} catch (err) {
  console.error('call isLocalWantAgent failed');
}
```
