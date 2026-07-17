# trigger

## trigger

```TypeScript
function trigger(agent: WantAgent, triggerInfo: TriggerInfo, callback?: Callback<CompleteData>): void
```

主动激发WantAgent实例。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** trigger

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-wantAgent-function trigger(agent: WantAgent, triggerInfo: TriggerInfo, callback?: Callback<CompleteData>): void--><!--Device-wantAgent-function trigger(agent: WantAgent, triggerInfo: TriggerInfo, callback?: Callback<CompleteData>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | WantAgent对象。 |
| triggerInfo | [TriggerInfo](arkts-ability-wantagent-triggerinfo-t.md) | 是 | TriggerInfo对象。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<CompleteData> | 否 | 主动激发WantAgent实例的回调方法。 |

**示例：**

```TypeScript
import wantAgent, { WantAgent as _WantAgent } from '@ohos.wantAgent';
import { BusinessError } from '@ohos.base';

// wantAgent对象
let wantAgentObj: _WantAgent;

// getWantAgent回调
function getWantAgentCallback(err: BusinessError, data: _WantAgent) {
    console.info('==========================>getWantAgentCallback=======================>');
    if (err.code == 0) {
        wantAgentObj = data;
    } else {
        console.error('getWantAgent failed, error: ' + JSON.stringify(err));
        return;
    }

    // trigger回调
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

