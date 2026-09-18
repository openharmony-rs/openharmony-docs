# cancel

## Modules to Import

```TypeScript
```

## cancel

```TypeScript
function cancel(agent: WantAgent, callback: AsyncCallback<void>): void
```

Cancel a WantAgent. Only the application that creates the WantAgent can cancel it.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [cancel](arkts-ability-wantagent-cancel-f.md)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-depr-t.md) | Yes | to cancel. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Cancel the callback method for Want in WantAgent. |

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

    // cancel callback
    let cancelCallback = (err: BusinessError) => {
        console.info('==========================>cancelCallback=======================>');
    }
    wantAgent.cancel(wantAgentObj, cancelCallback);
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

```TypeScript
import wantAgent, { WantAgent as _WantAgent } from '@ohos.wantAgent';
import { BusinessError } from '@ohos.base';

// WantAgent object
let wantAgentObj: _WantAgent;

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
}).then((data) => {
    console.info('==========================>getWantAgentCallback=======================>');
    wantAgentObj = data;
    if (wantAgentObj) {        
        wantAgent.cancel(wantAgentObj).then((data) => {
            console.info('==========================>cancelCallback=======================>');
        });
    }
});
```


## cancel

```TypeScript
function cancel(agent: WantAgent): Promise<void>
```

Cancel a WantAgent. Only the application that creates the WantAgent can cancel it.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [cancel](arkts-ability-wantagent-cancel-f.md)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-depr-t.md) | Yes | to cancel. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Examples**

See [cancel](#cancel)
