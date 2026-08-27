# getWant（系统接口）

## 导入模块

```TypeScript
import { wantAgent, WantAgent } from '@kit.AbilityKit';
```

## getWant

```TypeScript
function getWant(agent: WantAgent, callback: AsyncCallback<Want>): void
```

获取WantAgent对象的want。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-t.md) | 是 | WantAgent对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | 是 | 回调函数。当获取WantAgent对象want成功，err中code为0，data为获取到的Want数据；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000007](../errorcode-ability.md#16000007-服务未响应) | Service busy. There are concurrent tasks. Try again later. |
| [16000015](../errorcode-ability.md#16000015-服务超时) | Service timeout. |
| [16000151](../errorcode-ability.md#16000151-无效wantagent对象) | Invalid wantAgent object. |

**示例**

```TypeScript
import { wantAgent, WantAgent as _WantAgent, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 用于存储创建的WantAgent实例
let wantAgentData: _WantAgent;
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
  actionType: wantAgent.OperationType.START_ABILITIES,
  requestCode: 0,
  wantAgentFlags:[wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

// 创建WantAgent实例的回调函数
let getWantAgentCallback = (err: BusinessError, data: _WantAgent) => {
  if (err) {
    console.error(`getWantAgent failed, code: ${err.code}, message: ${err.message}`);
  } else {
    wantAgentData = data;
  }
  // 获取Want数据的回调函数
  let getWantCallback = (err: BusinessError, data: Want) => {
    if (err.code) {
      console.error(`Failed to getWant. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`getWant success, data: ${JSON.stringify(data)}.`);
    }
  }
  try {
    // 获取WantAgent对象的Want数据
    wantAgent.getWant(wantAgentData, getWantCallback);
  } catch(err) {
    let code = (err as BusinessError).code;
    let msg = (err as BusinessError).message;
    console.error(`getWant failed, code: ${code}, message: ${msg}.`);
  }
}

try {
  // 创建WantAgent实例
  wantAgent.getWantAgent(wantAgentInfo, getWantAgentCallback);
} catch(err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`getWantAgent failed, code: ${code}, message: ${msg}.`);
}
```


## getWant

```TypeScript
function getWant(agent: WantAgent): Promise<Want>
```

获取WantAgent对象的want。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-t.md) | 是 | WantAgent对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | Promise对象，返回WantAgent对象的want。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000007](../errorcode-ability.md#16000007-服务未响应) | Service busy. There are concurrent tasks. Try again later. |
| [16000015](../errorcode-ability.md#16000015-服务超时) | Service timeout. |
| [16000151](../errorcode-ability.md#16000151-无效wantagent对象) | Invalid wantAgent object. |

**示例**

```TypeScript
import { wantAgent, WantAgent as _WantAgent, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 用于存储创建的WantAgent实例
let wantAgentData: _WantAgent;
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
  actionType: wantAgent.OperationType.START_ABILITIES,
  requestCode: 0,
  wantAgentFlags:[wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

// 创建WantAgent实例的回调函数
let getWantAgentCallback = (err: BusinessError, data: _WantAgent) => {
  if (err) {
    console.error(`getWantAgent failed, code: ${err.code}, message: ${err.message}`);
  } else {
    wantAgentData = data;
  }
  try {
    // 获取WantAgent对象的Want数据
    wantAgent.getWant(wantAgentData).then((data)=>{
      console.info(`getWant success, data: ${JSON.stringify(data)}`);
    }).catch((err: BusinessError)=>{
      console.error(`getWant failed, code: ${err.code}, message: ${err.message}.`);
    });
  } catch(err){
    let code = (err as BusinessError).code;
    let msg = (err as BusinessError).message;
    console.error(`getWant failed, code: ${code}, message: ${msg}.`);
  }
}

try {
  // 创建WantAgent实例
  wantAgent.getWantAgent(wantAgentInfo, getWantAgentCallback);
} catch(err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`getWantAgent failed, code: ${code}, message: ${msg}.`);
}
```
