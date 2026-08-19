# onPrepareContinue

## 导入模块

```TypeScript
import { continueManager } from '@kit.AbilityKit';
```

## onPrepareContinue

```TypeScript
function onPrepareContinue(context: Context, callback: AsyncCallback<ContinueResultInfo>): void
```

prepareContinue 事件，当在 continueType 中配置了“ContinueQuickStart”功能时，即可获取

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continueManager-function onPrepareContinue(context: Context, callback: AsyncCallback<ContinueResultInfo>): void--><!--Device-continueManager-function onPrepareContinue(context: Context, callback: AsyncCallback<ContinueResultInfo>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](arkts-ability-context-c.md) | 是 | the ability context. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ContinueResultInfo](arkts-ability-continuemanager-continueresultinfo-i.md)&gt; | 是 | Used to handle ('prepareContinue') command. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16300501](../errorcode-DistributedSchedule.md#16300501-系统服务工作异常) | the system ability work abnormally. |

**示例**

```TypeScript
import { BusinessError } from '@ohos.base';
import UIAbility from '@ohos.app.ability.UIAbility';
import AbilityConstant from '@ohos.app.ability.AbilityConstant';
import Want from '@ohos.app.ability.Want';
import hilog from '@ohos.hilog'
import continueManager from '@ohos.app.ability.continueManager'

let domain: int = 0x8888; // 日志标识,
let tag: string = 'Tonny'; // 日志标识字符串,作为tag标识当前runner类下的测试行为

const TAG: string = '[MigrationAbility]';
const DOMAIN_NUMBER: int = 0xFF00;
export default class MigrationAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(DOMAIN_NUMBER, TAG, '%{public}s', 'Ability onCreate');
    // 1.已配置快速拉起功能，应用立即启动时触发应用生命周期回调
    if (launchParam.launchReason === AbilityConstant.LaunchReason.PREPARE_CONTINUATION) {
      // 注册快速拉起结果通知的回调函数
      try {
        continueManager.onPrepareContinue(this.context,
          (err: BusinessError|null, continueResultInfo: continueManager.ContinueResultInfo|undefined) => {
            if (err!.code != 0) {
              console.error('register failed, cause: ' + JSON.stringify(err));
              return;
            }
            console.info('register finished, ' + JSON.stringify(continueResultInfo));
          });
      } catch (e) {
        console.error('register failed, cause: ' + JSON.stringify(e));
      }
      // 若应用迁移数据较大，可在此处添加加载页面(页面中显示loading等)
      // 可处理应用自定义跳转、时序等问题
      // ...
    }
  }
}
```

