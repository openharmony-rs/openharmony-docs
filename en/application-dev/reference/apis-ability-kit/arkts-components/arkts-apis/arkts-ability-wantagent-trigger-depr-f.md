# trigger

## Modules to Import

```TypeScript
```

## trigger

```TypeScript
function trigger(agent: WantAgent, triggerInfo: TriggerInfo, callback?: Callback<CompleteData>): void
```

Triggers a WantAgent.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [trigger](arkts-ability-wantagent-trigger-f.md)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-depr-t.md) | Yes | to trigger. |
| triggerInfo | [TriggerInfo](arkts-ability-triggerinfo-triggerinfo-i.md) | Yes | parameters. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;CompleteData&gt; | No | Indicates the callback method to be called after the [WantAgent](arkts-ability-wantagent-depr-t.md#wantagent) is triggered. |

**Examples**

```TypeScript
import wantAgent, { WantAgent as _WantAgent } from '@ohos.wantAgent';
import { BusinessError } from '@ohos.base';

// WantAgent object
let wantAgentObj: _WantAgent;

// getWantAgent callback
function getWantAgentCallback(err: BusinessError, data: _WantAgent) {
    console.info('==========================>getWantAgentCallback=======================>');
    if (err.code == 0) {
        wantAgentObj = data;
    } else {
        console.error('getWantAgent failed, error: ' + JSON.stringify(err));
        return;
    }

    // trigger callback
    let triggerCallback = (data: wantAgent.CompleteData) => {
        console.info('==========================>triggerCallback=======================>');
    };

    wantAgent.trigger(wantAgentObj, {code:0}, triggerCallback);
}

wantAgent.getWantAgent({
    wants: [
        {
            deviceId: 'deviceId',
            bundleName: 'com.neu.setResultOnAbilityResultTest1',
            abilityName: 'com.example.test.EntryAbility',
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
        }
    ],
    operationType: wantAgent.OperationType.START_ABILITY,
    requestCode: 0,
    wantAgentFlags:[wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
}, getWantAgentCallback);
```
