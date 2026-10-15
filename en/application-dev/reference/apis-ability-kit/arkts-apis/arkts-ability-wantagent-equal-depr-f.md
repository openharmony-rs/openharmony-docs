# equal

## Modules to Import

```TypeScript
```

<a id="equal1"></a>

## equal

```TypeScript
function equal(agent: WantAgent, otherAgent: WantAgent, callback: AsyncCallback<boolean>): void
```

Checks whether two WantAgent objects are equal to determine whether the same operation is from the same application. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [equal](arkts-ability-wantagent-equal-f.md)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-wantAgent-function equal(agent: WantAgent, otherAgent: WantAgent, callback: AsyncCallback<boolean>): void--><!--Device-wantAgent-function equal(agent: WantAgent, otherAgent: WantAgent, callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-depr-t.md) | Yes | The first WantAgent object. |
| otherAgent | [WantAgent](arkts-ability-wantagent-depr-t.md) | Yes | WantAgent Object. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. true if the two WantAgent objects are equal, false otherwise. |

**Examples**

```TypeScript
import wantAgent, { WantAgent as _WantAgent } from '@ohos.wantAgent';
import { BusinessError } from '@ohos.base';

// WantAgent object
let wantAgentObj1: _WantAgent;
let wantAgentObj2: _WantAgent;

// getWantAgent callback
function getWantAgentCallback(err: BusinessError, data: _WantAgent) {
    console.info('==========================>getWantAgentCallback=======================>');
    if (err.code == 0) {
        wantAgentObj1 = data;
        wantAgentObj2 = data;
    } else {
        console.error('getWantAgent failed, error: ' + JSON.stringify(err));
        return;
    }

    // equal callback
    let equalCallback = (err: BusinessError, data: boolean) => {
        console.info('==========================>equalCallback=======================>');
    };
    wantAgent.equal(wantAgentObj1, wantAgentObj2, equalCallback);
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


<a id="equal2"></a>

## equal

```TypeScript
function equal(agent: WantAgent, otherAgent: WantAgent): Promise<boolean>
```

Checks whether two WantAgent objects are equal to determine whether the same operation is from the same application. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [equal](arkts-ability-wantagent-equal-f.md)

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-wantAgent-function equal(agent: WantAgent, otherAgent: WantAgent): Promise<boolean>--><!--Device-wantAgent-function equal(agent: WantAgent, otherAgent: WantAgent): Promise<boolean>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-depr-t.md) | Yes | The first WantAgent object. |
| otherAgent | [WantAgent](arkts-ability-wantagent-depr-t.md) | Yes | WantAgent Object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. true if the two WantAgent objects are equal, false otherwise. |

**Examples**

```TypeScript
import wantAgent, { WantAgent as _WantAgent } from '@ohos.wantAgent';

// WantAgent object
let wantAgentObj1: _WantAgent;
let wantAgentObj2: _WantAgent;

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
    wantAgentObj1 = data;
    wantAgentObj2 = data;
    if (data) {
        wantAgent.equal(wantAgentObj1, wantAgentObj2).then((data) => {
            console.info('==========================>equalCallback=======================>');
        });
    }
});
```
