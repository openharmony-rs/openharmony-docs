# off

## 导入模块

```TypeScript
import { continueManager } from '@kit.AbilityKit';
```

## off('prepareContinue')

```TypeScript
function off(type: 'prepareContinue', context: Context, callback?: AsyncCallback<ContinueResultInfo>): void
```

在应用快速拉起时，注销回调函数，不再获取快速拉起结果。使用callback异步回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continueManager-function off(type: 'prepareContinue', context: Context, callback?: AsyncCallback<ContinueResultInfo>): void--><!--Device-continueManager-function off(type: 'prepareContinue', context: Context, callback?: AsyncCallback<ContinueResultInfo>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'prepareContinue' | 是 | 固定值：prepareContinue。 |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | Ability的Context。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ContinueResultInfo&gt; | 否 | 回调函数。当回调函数注销成功，err为undefined，ContinueResultInfo为获回调函数注销结果。否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16300501](../errorcode-DistributedSchedule.md#16300501-系统服务工作异常) | the system ability work abnormally. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want, continueManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[MigrationAbility]';
const DOMAIN_NUMBER: number = 0xFF00;

export default class MigrationAbility extends UIAbility {
    
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        hilog.info(DOMAIN_NUMBER, TAG, '%{public}s', 'Ability onCreate');

        // 1.已配置快速拉起功能，应用立即启动时触发应用生命周期回调
        if (launchParam.launchReason === AbilityConstant.LaunchReason.PREPARE_CONTINUATION) {
            // 注销快速拉起结果通知的回调函数
            try {
              continueManager.off('prepareContinue', this.context, (err, continueResultInfo) => {
                if (err.code != 0) {
                  hilog.error(DOMAIN_NUMBER, TAG, 'unregister failed, cause: %{public}s', JSON.stringify(err));
                  return;
                }
                hilog.info(DOMAIN_NUMBER, TAG, 'unregister finished, %{public}s', JSON.stringify(continueResultInfo));
              });
            } catch (e) {
              hilog.error(DOMAIN_NUMBER, TAG, 'unregister failed, cause: %{public}s', JSON.stringify(e));
            }
            // 若应用迁移数据较大，可在此处添加加载页面(页面中显示loading等)
            // 可处理应用自定义跳转、时序等问题
            // ...
        }
    }
}

```

