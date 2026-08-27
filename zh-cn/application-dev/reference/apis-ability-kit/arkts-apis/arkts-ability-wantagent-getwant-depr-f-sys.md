# getWant（系统接口）

## 导入模块

```TypeScript
```

## getWant

```TypeScript
function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void
```

获取WantAgent中的Want(callback形式)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getWant](arkts-ability-wantagent-getwant-f-sys.md)

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-depr-t.md) | 是 | Indicates the [WantAgent](arkts-ability-wantagent-depr-t.md#wantagent) WantAgent信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | 是 | 获取WantAgent中的Want的回调方法。 |

**示例**

```TypeScript
import WantAgent, { WantAgent as _WantAgent} from '@ohos.wantAgent';
import Want from '@ohos.app.ability.Want';
import { BusinessError } from '@ohos.base';

// wantAgent对象
let wantAgent: _WantAgent;

// getWantAgent回调
let getWantAgentCallback = (err: BusinessError, data: _WantAgent) => {
    console.info('==========================>getWantAgentCallback=======================>');
    if (err.code == 0) {
        wantAgent = data;
    } else {
        console.error('getWantAgent failed, error: ' + JSON.stringify(err));
        return;
    }

    // getWant回调
    let getWantCallback = (err: BusinessError, data: Want) => {
        console.info('==========================>getWantCallback=======================>');
    }
    WantAgent.getWant(wantAgent, getWantCallback);
}

WantAgent.getWantAgent({
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
    operationType: WantAgent.OperationType.START_ABILITIES,
    requestCode: 0,
    wantAgentFlags:[WantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
}, getWantAgentCallback);
```


## getWant

```TypeScript
function getWant(agent: WantAgent): Promise<Want>
```

获取WantAgent中的Want(Promise形式)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getWant](arkts-ability-wantagent-getwant-f-sys.md)

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-depr-t.md) | 是 | WantAgent信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | 以Promise形式返回Want。 |

**示例**

```TypeScript
import WantAgent, { WantAgent as _WantAgent} from '@ohos.wantAgent';
import { BusinessError } from '@ohos.base';

// wantAgent对象
let wantAgent: _WantAgent;

WantAgent.getWantAgent({
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
    operationType: WantAgent.OperationType.START_ABILITIES,
    requestCode: 0,
    wantAgentFlags:[WantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
}).then((data) => {
    console.info('==========================>getWantAgentCallback=======================>');
    wantAgent = data;
    if (wantAgent) {        
        WantAgent.getWant(wantAgent).then((data) => {
            console.info('==========================>getWantCallback=======================>');
        });
    }
});
```
