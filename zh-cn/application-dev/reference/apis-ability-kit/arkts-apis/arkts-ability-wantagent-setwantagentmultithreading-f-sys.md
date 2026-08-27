# setWantAgentMultithreading（系统接口）

## 导入模块

```TypeScript
import { wantAgent, WantAgent } from '@kit.AbilityKit';
```

## setWantAgentMultithreading

```TypeScript
function setWantAgentMultithreading(isMultithreadingSupported: boolean) : void
```

开启或者关闭WantAgent多线程传递功能。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isMultithreadingSupported | boolean | 是 | 表示是否开启多线程传递功能。true表示开启，false表示关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例**

```TypeScript
import { wantAgent, WantAgent as _WantAgent, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 定义wantAgent对象
let wantAgentData: _WantAgent;
// 定义WantAgentInfo对象
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
  wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

// 定义getWantAgent回调
let getWantAgentCallback = (err: BusinessError, data: _WantAgent) => {
  if (err) {
    console.error(`Failed to call getWantAgentCallback. Code is ${err.code}. Message is ${err.message}.`);
  } else {
    wantAgentData = data;
  }

  try {
    // 开启WantAgent多线程传递功能
    wantAgent.setWantAgentMultithreading(true);
  } catch (err) {
    let code = (err as BusinessError).code;
    let msg = (err as BusinessError).message;
    console.error(`Failed to set wantAgentMultithreading. Code: ${code}, message: ${msg}`);
  }
}

try {
  // 创建WantAgent实例
  wantAgent.getWantAgent(wantAgentInfo, getWantAgentCallback);
} catch (err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`Failed to get wantAgent. Code: ${code}, message: ${msg}`);
}
```
