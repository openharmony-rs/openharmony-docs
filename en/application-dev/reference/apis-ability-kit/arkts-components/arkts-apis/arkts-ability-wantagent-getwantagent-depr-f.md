# getWantAgent

## Modules to Import

```TypeScript
```

## getWantAgent

```TypeScript
function getWantAgent(info: WantAgentInfo, callback: AsyncCallback<WantAgent>): void
```

Obtains a WantAgent object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getWantAgent](arkts-ability-wantagent-getwantagent-f.md)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [WantAgentInfo](arkts-ability-wantagentinfo-wantagentinfo-i.md) | Yes | about the WantAgent object to obtain. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WantAgent](arkts-ability-wantagent-depr-t.md)&gt; | Yes | Callback method for obtaining the user ID of WantAgent instance. |

**Examples**

```TypeScript
import wantAgent, { WantAgent as _WantAgent } from '@ohos.wantAgent';
import { BusinessError } from '@ohos.base';

// getWantAgent callback
function getWantAgentCallback(err: BusinessError, data: _WantAgent) {
    if (err.code) {
        console.error('getWantAgent Callback err:' + JSON.stringify(err));
    } else { 
        console.info('getWantAgent Callback success');
    }
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


<a id="getwantagent-1"></a>

## getWantAgent

```TypeScript
function getWantAgent(info: WantAgentInfo): Promise<WantAgent>
```

Obtains a WantAgent object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getWantAgent](arkts-ability-wantagent-getwantagent-f.md)

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [WantAgentInfo](arkts-ability-wantagentinfo-wantagentinfo-i.md) | Yes | about the WantAgent object to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[WantAgent](arkts-ability-wantagent-depr-t.md)&gt; | Returns the created [WantAgent](arkts-ability-wantagent-depr-t.md#wantagent) object. |

**Examples**

```TypeScript
import wantAgent, { WantAgent as _WantAgent } from '@ohos.wantAgent';

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
}).then((data: _WantAgent) => {
    console.info('==========================>getWantAgentCallback=======================>');
});
```
