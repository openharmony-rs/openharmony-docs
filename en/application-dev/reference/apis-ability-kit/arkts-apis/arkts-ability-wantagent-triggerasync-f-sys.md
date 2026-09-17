# triggerAsync (System API)

## Modules to Import

```TypeScript
import { wantAgent, WantAgent } from '@kit.AbilityKit';
```

## triggerAsync

```TypeScript
function triggerAsync(agent: WantAgent, triggerInfo: TriggerInfo, context: Context): Promise<CompleteData>
```

Asynchronously triggers a predefined operation encration encapsulated in a Wantagent with specified trigger information. If the specified wantAgent is local, you need to apply for permission: ohos.permission.TRIGGER_LOCAL_WANTAGENT permission.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-t.md) | Yes | Indicates the WantAgent. |
| triggerInfo | [TriggerInfo](arkts-ability-wantagent-triggerinfo-t.md) | Yes | Indicates the information required for triggering a WantAgent. |
| context | [Context](arkts-ability-context-c.md) | Yes | Indicates current context. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CompleteData](arkts-ability-wantagent-completedata-i.md)&gt; | Returns the CompleteData. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [16000020](../errorcode-ability.md#16000020-context-is-not-an-ability-level-context) | The context is not ability context. |
| [16000151](../errorcode-ability.md#16000151-invalid-wantagent-object) | Invalid wantAgent object. |
| [16000153](../errorcode-ability.md#16000153-wantagent-object-is-canceled) | The WantAgent has been canceled. |

**Examples**

```TypeScript
import { wantAgent, Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';
import type { WantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// WantAgent object.
let wantAgentData: WantAgent;
// triggerInfo
let triggerInfo: wantAgent.TriggerInfo = {
  code: 0 // Custom result code.
};
// WantAgentInfo object.
let wantAgentInfo: wantAgent.WantAgentInfo = {
  // Custom parameters.
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
  // Specified operation.
  actionType: wantAgent.OperationType.START_ABILITY,
  requestCode: 0,
  // WantAgent object type.
  wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    try {
      // Create a WantAgent object.
      wantAgent.getWantAgent(wantAgentInfo, (err: BusinessError, data: WantAgent) => {
        if (err) {
          console.info(`getWantAgent failed, code: ${err.code}, message: ${err.message}`);
        } else {
          wantAgentData = data;
        }

        try {
          // Proactively trigger a WantAgent object.
          wantAgent.triggerAsync(wantAgentData, triggerInfo, this.context).then((data) => {
            console.info(`trigger success, data: ${JSON.stringify(data)}`);
          }).catch((err: BusinessError) => {
            console.error(`triggerAsync failed! ${err.code} ${err.message}`);
          });
        } catch (err) {
          console.error(`triggerAsync failed! ${err.code} ${err.message}`);
         }
       });
     } catch (err) {
       let code = (err as BusinessError).code;
       let msg = (err as BusinessError).message;
       console.error(`getWantAgent failed, code: ${code}, message: ${msg}.`);
     }
   }
 }
```
