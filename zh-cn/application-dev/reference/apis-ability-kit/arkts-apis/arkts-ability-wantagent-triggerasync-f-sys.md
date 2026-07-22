# triggerAsync（系统接口）

## 导入模块

```TypeScript
import { WantAgent } from '@kit.AbilityKit';
```

## triggerAsync

```TypeScript
function triggerAsync(agent: WantAgent, triggerInfo: TriggerInfo, context: Context): Promise<CompleteData>
```

主动触发WantAgent实例，即按照WantAgent实例中已封装的指定操作和参数等信息执行。使用Promise异步回调。仅当入参agent为本地WantAgent实例时需要申请: ohos.permission.TRIGGER_LOCAL_WANTAGENT permission.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wantAgent-function triggerAsync(agent: WantAgent, triggerInfo: TriggerInfo, context: Context): Promise<CompleteData>--><!--Device-wantAgent-function triggerAsync(agent: WantAgent, triggerInfo: TriggerInfo, context: Context): Promise<CompleteData>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agent | [WantAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent-wantagent-i.md) | 是 | WantAgent对象。 |
| triggerInfo | [TriggerInfo](arkts-ability-wantagent-triggerinfo-t.md) | 是 | TriggerInfo对象。 |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 请求触发WantAgent的UIAbility/ExtensionAbility的Context。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CompleteData&gt; | Promise对象，返回主动激发WantAgent获得的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [16000020](../errorcode-ability.md#16000020-传入的context对象不是ability级别context) | The context is not ability context. |
| [16000151](../errorcode-ability.md#16000151-无效wantagent对象) | Invalid wantagent object. |
| [16000153](../errorcode-ability.md#16000153-wantagent对象已被取消) | The Wantagent has been canceled. |

**示例：**

```TypeScript
import { wantAgent, Want, UIAbility, AbilityConstant } from '@kit.AbilityKit';
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
  // 自定义参数
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
  // 指定的操作
  actionType: wantAgent.OperationType.START_ABILITY,
  requestCode: 0,
  // wantagent对象类型
  wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    try {
      // 创建wantAgent对象
      wantAgent.getWantAgent(wantAgentInfo, (err: BusinessError, data: WantAgent) => {
        if (err) {
          console.info(`getWantAgent failed, code: ${err.code}, message: ${err.message}`);
        } else {
          wantAgentData = data;
        }

        try {
          // 主动触发WantAgent实例
          wantAgent.triggerAsync(wantAgentData, triggerInfo, this.context).then((data) => {
            console.info(`trigger success, data: ${JSON.stringify(data)}`);
          }).catch((err: BusinessError) => {
            console.error(`triggerAsync failed! ${err.code} ${err.message}`);
          });
        } catch (err) {
          console.error(`triggerAsync failed! ${err.code} ${err.message}`);
         }
       });
     } catch (err) {
       let code = (err as BusinessError).code;
       let msg = (err as BusinessError).message;
       console.error(`getWantAgent failed, code: ${code}, message: ${msg}.`);
     }
   }
 }

```

