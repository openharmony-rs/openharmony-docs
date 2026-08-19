# trigger

## 导入模块

```TypeScript
import { wantAgent, WantAgent } from '@kit.AbilityKit';
```

## trigger

```TypeScript
function trigger(agent: WantAgent, triggerInfo: TriggerInfo, callback?: AsyncCallback<CompleteData>): void
```

触发WantAgent实例，执行指定的操作（启动Ability、发送公共事件等）。使用callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-wantAgent-function trigger(agent: WantAgent, triggerInfo: TriggerInfo, callback?: AsyncCallback<CompleteData>): void--><!--Device-wantAgent-function trigger(agent: WantAgent, triggerInfo: TriggerInfo, callback?: AsyncCallback<CompleteData>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-t.md) | 是 | WantAgent对象。 |
| triggerInfo | TriggerInfo | 是 | 表示触发WantAgent实例时携带的信息，如自定义的extraInfos。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;CompleteData&gt; | 否 | 主动激发WantAgent实例的回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { wantAgent, Want } from '@kit.AbilityKit';
import type { WantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// wantAgent对象
let wantAgentData: WantAgent;
// triggerInfo
let triggerInfo: wantAgent.TriggerInfo = {
  code: 0 // 自定义结果码
};
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
let getWantAgentCallback = (err: BusinessError, data: WantAgent) => {
  if (err) {
    console.error(`getWantAgent failed, code: ${err.code}, message: ${err.message}`);
  } else {
    // 创建WantAgent成功，保存返回的WantAgent对象
    wantAgentData = data;
  }
  // trigger回调
  let triggerCallback = (err: BusinessError, data: wantAgent.CompleteData) => {
    if (err) {
      console.error(`trigger failed, code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`trigger success, data: ${JSON.stringify(data)}`);
    }
  }
  try {
    // 调用trigger接口触发WantAgent实例执行指定操作
    wantAgent.trigger(wantAgentData, triggerInfo, triggerCallback);
  } catch (err) {
    let code = (err as BusinessError).code;
    let msg = (err as BusinessError).message;
    console.error(`trigger failed, code: ${code}, message: ${msg}.`);
  }
}

try {
  // 调用getWantAgent接口创建WantAgent对象
  wantAgent.getWantAgent(wantAgentInfo, getWantAgentCallback);
} catch (err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`getWantAgent failed, code: ${code}, message: ${msg}.`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { wantAgent, Want } from '@kit.AbilityKit';
import type { WantAgent } from '@kit.AbilityKit';
import { BusinessError, RecordData } from '@kit.BasicServicesKit';

// wantAgent对象
let wantAgentData: WantAgent;
// triggerInfo
let triggerInfo: wantAgent.TriggerInfo = {
  code: 0 // 自定义结果码
};
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
      parameters: {
        'mykey0': 2222,
        'mykey1': [1, 2, 3],
        'mykey2': '[1, 2, 3]',
        'mykey3': 'ssssssssssssssssssssssssss',
        'mykey4': [false, true, false],
        'mykey5': ['qqqqq', 'wwwwww', 'aaaaaaaaaaaaaaaaa'],
        'mykey6': true,
      } as Record<string, RecordData>
    } as Want
  ],
  actionType: wantAgent.OperationType.START_ABILITIES,
  requestCode: 0,
};

try {
  wantAgent.getWantAgent(wantAgentInfo, (err, data) => {
    if (err) {
      console.error(`getWantAgent failed, code: ${err.code}, message: ${err.message}`);
      return;
    }
    if (!data) {
      console.error('getWantAgent failed: data is undefined');
      return;
    }
    wantAgentData = data;
    try {
      wantAgent.trigger(wantAgentData, triggerInfo, (err, data) => {
        if (err) {
          console.error(`trigger failed, code: ${err.code}, message: ${err.message}`);
        } else {
          console.info(`trigger success, data: ${JSON.stringify(data)}`);
        }
      });
    } catch (error) {
      let err = error as BusinessError;
      console.error(`trigger failed, code: ${err.code}, message: ${err.message}`);
    }
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`getWantAgent failed! ${err.code} ${err.message}`);
}
```

