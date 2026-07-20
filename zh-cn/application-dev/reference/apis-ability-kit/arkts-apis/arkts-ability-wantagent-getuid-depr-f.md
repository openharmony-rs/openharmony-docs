# getUid

<a id="getuid"></a>
## getUid

```TypeScript
function getUid(agent: WantAgent, callback: AsyncCallback<number>): void
```

获取WantAgent实例的用户ID。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getUid

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-wantAgent-function getUid(agent: WantAgent, callback: AsyncCallback<number>): void--><!--Device-wantAgent-function getUid(agent: WantAgent, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | WantAgent对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 获取WantAgent实例的用户ID的回调方法。 |

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

    // getUid回调
    let getUidCallback = (err: BusinessError, data: number) => {
        console.info('==========================>getUidCallback=======================>');
    }
    wantAgent.getUid(wantAgentObj, getUidCallback);
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


<a id="getuid-1"></a>
## getUid

```TypeScript
function getUid(agent: WantAgent): Promise<number>
```

获取WantAgent实例的用户ID。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getUid

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-wantAgent-function getUid(agent: WantAgent): Promise<number>--><!--Device-wantAgent-function getUid(agent: WantAgent): Promise<number>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | WantAgent对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 以Promise形式返回获取WantAgent实例的用户ID。 |

**示例：**

```TypeScript
import wantAgent, { WantAgent as _WantAgent } from '@ohos.wantAgent';

// wantAgent对象
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
        wantAgent.getUid(wantAgentObj).then((data) => {
        console.info('==========================>getUidCallback=======================>');
    });
    }
});

```

