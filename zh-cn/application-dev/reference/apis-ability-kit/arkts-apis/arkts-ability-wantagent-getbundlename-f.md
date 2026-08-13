# getBundleName

## getBundleName

```TypeScript
function getBundleName(agent: WantAgent, callback: AsyncCallback<string>): void
```

获取WantAgent实例所属应用的包名，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-wantAgent-function getBundleName(agent: WantAgent, callback: AsyncCallback<string>): void--><!--Device-wantAgent-function getBundleName(agent: WantAgent, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-t.md) | 是 | WantAgent对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数。当获取包名成功，err为undefined，data为创建的WantAgent；否则err会返回对应的错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000007](../errorcode-ability.md#16000007-服务未响应) | Service busy. There are concurrent tasks. Try again later. |
| [16000151](../errorcode-ability.md#16000151-无效wantagent对象) | Invalid wantAgent object. |

## 示例

ArkTS-Dyn示例：

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
let getWantAgentCallback = (err: BusinessError, data: WantAgent) => {
  if (err) {
    console.error(`getWantAgent failed, code: ${JSON.stringify(err.code)}, message: ${JSON.stringify(err.message)}`);
  } else {
    // 创建WantAgent成功，保存返回的WantAgent对象
    wantAgentData = data;
  }
  // getBundleName回调
  let getBundleNameCallback = (err: BusinessError, data: string) => {
    if (err) {
      console.error(`getBundleName failed! ${err.code} ${err.message}`);
    } else {
      console.info(`getBundleName ok! ${JSON.stringify(data)}`);
    }
  }
  try {
    // 调用getBundleName接口获取WantAgent实例的包名
    wantAgent.getBundleName(wantAgentData, getBundleNameCallback);
  } catch (err) {
    console.error(`getBundleName failed! ${err.code} ${err.message}`);
  }
}

try {
  // 调用getWantAgent接口创建WantAgent对象
  wantAgent.getWantAgent(wantAgentInfo, getWantAgentCallback);
} catch (err) {
  console.error(`getWantAgent failed! ${err.code} ${err.message}`);
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
      wantAgent.getBundleName(wantAgentData, (err, data) => {
        if (err) {
          console.error(`getBundleName failed! ${err.code} ${err.message}`);
        } else {
          console.info(`getBundleName ok! ${JSON.stringify(data)}`);
        }
      });
    } catch (error) {
      let err = error as BusinessError;
      console.error(`getBundleName failed! ${err.code} ${err.message}`);
    }
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`getWantAgent failed! ${err.code} ${err.message}`);
}
```


## getBundleName

```TypeScript
function getBundleName(agent: WantAgent): Promise<string>
```

获取WantAgent实例所属应用的包名。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-wantAgent-function getBundleName(agent: WantAgent): Promise<string>--><!--Device-wantAgent-function getBundleName(agent: WantAgent): Promise<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](arkts-ability-wantagent-t.md) | 是 | WantAgent对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回获取WantAgent实例的包名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [16000007](../errorcode-ability.md#16000007-服务未响应) | Service busy. There are concurrent tasks. Try again later. |
| [16000151](../errorcode-ability.md#16000151-无效wantagent对象) | Invalid wantAgent object. |

## 示例

ArkTS-Dyn示例：

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
  wantAgentFlags:[wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

// getWantAgent回调
let getWantAgentCallback = (err: BusinessError, data: WantAgent) => {
  if (err) {
    console.error(`getWantAgent failed, code: ${JSON.stringify(err.code)}, message: ${JSON.stringify(err.message)}`);
  } else {
    // 创建WantAgent成功，保存返回的WantAgent对象
    wantAgentData = data;
  }
  try {
    // 使用Promise方式获取WantAgent实例的包名
    wantAgent.getBundleName(wantAgentData).then((data) => {
      console.info(`getBundleName ok! ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`getBundleName failed! ${err.code} ${err.message}`);
    });
  } catch(err){
    console.error(`getBundleName failed! ${err.code} ${err.message}`);
  }
}
try {
  // 调用getWantAgent接口创建WantAgent对象
  wantAgent.getWantAgent(wantAgentInfo, getWantAgentCallback);
} catch(err) {
  console.error(`getWantAgent failed! ${err.code} ${err.message}`);
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
      wantAgent.getBundleName(wantAgentData).then((data) => {
        console.info(`getBundleName ok! ${JSON.stringify(data)}`);
      }).catch((error) => {
        let err = error as BusinessError;
        console.error(`getBundleName failed! ${err.code} ${err.message}`);
      });
    } catch (error) {
      let err = error as BusinessError;
      console.error(`getBundleName failed! ${err.code} ${err.message}`);
    }
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`getWantAgent failed! ${err.code} ${err.message}`);
}
```

