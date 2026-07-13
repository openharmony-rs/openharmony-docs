# cancel

## cancel

```TypeScript
function cancel(agent: WantAgent, callback: AsyncCallback<void>): void
```

取消WantAgent实例，使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | WantAgent | 是 | WantAgent对象。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 取消WantAgent实例的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000007](../errorcode-ability.md#16000007-服务未响应) | Service busy. There are concurrent tasks. Try again later. |
| [16000151](../errorcode-ability.md#16000151-无效wantagent对象) | Invalid wantAgent object. |

**示例：**

```TypeScript
import { wantAgent, Want } from '@kit.AbilityKit';
import type { WantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// wantAgent对象
let wantAgentData: WantAgent;
// WantAgentInfo对象
let wantAgentInfo: wantAgent.WantAgentInfo = {
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
  actionType: wantAgent.OperationType.START_ABILITY,
  requestCode: 0,
  wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

// getWantAgent回调
function getWantAgentCallback(err: BusinessError, data: WantAgent) {
  if (err) {
    console.error(`getWantAgent failed, err code: ${err.code}, err msg: ${err.message}.`);
  } else {
    wantAgentData = data;
  }
  // cancel回调
  let cancelCallback = (err: BusinessError, data: void) => {
    if (err) {
      console.error(`cancel failed, err code: ${err.code}, err msg: ${err.message}.`);
    } else {
      console.info(`cancel success.`);
    }
  }
  try {
    wantAgent.cancel(wantAgentData, cancelCallback);
  } catch (err) {
    let code = (err as BusinessError).code;
    let msg = (err as BusinessError).message;
    console.error(`cancel failed, err code: ${code}, err msg: ${msg}.`);
  }
}

try {
  wantAgent.getWantAgent(wantAgentInfo, getWantAgentCallback);
} catch (err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`getWantAgent failed, err code: ${code}, err msg: ${msg}.`);
}

```


## cancel

```TypeScript
function cancel(agent: WantAgent): Promise<void>
```

取消WantAgent实例。使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | WantAgent | 是 | WantAgent对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [16000007](../errorcode-ability.md#16000007-服务未响应) | Service busy. There are concurrent tasks. Try again later. |
| [16000151](../errorcode-ability.md#16000151-无效wantagent对象) | Invalid wantAgent object. |

**示例：**

```TypeScript
import { wantAgent, Want } from '@kit.AbilityKit';
import type { WantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// wantAgent对象
let wantAgentData: WantAgent;
// WantAgentInfo对象
let wantAgentInfo: wantAgent.WantAgentInfo = {
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
  actionType: wantAgent.OperationType.START_ABILITY,
  requestCode: 0,
  wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

// getWantAgent回调
function getWantAgentCallback(err: BusinessError, data: WantAgent) {
  if (err) {
    console.error(`getWantAgent failed, err code: ${err.code}, err msg: ${err.message}.`);
  } else {
    wantAgentData = data;
  }
  try {
    wantAgent.cancel(wantAgentData).then((data) => {
      console.info('cancel success.');
    }).catch((err: BusinessError) => {
      console.error(`cancel failed, err code: ${err.code}, err msg: ${err.message}.`);
    });
  } catch (err) {
    let code = (err as BusinessError).code;
    let msg = (err as BusinessError).message;
    console.error(`cancel failed, err code: ${code}, err msg: ${msg}.`);
  }
}

try {
  wantAgent.getWantAgent(wantAgentInfo, getWantAgentCallback);
} catch (err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`getWantAgent failed, err code: ${code}, err msg: ${msg}.`);
}

```

