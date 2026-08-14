# updateDataTransferProgress

## updateDataTransferProgress

```TypeScript
function updateDataTransferProgress(context: Context, progressInfo: DataTransferProgress): void
```

更新通知。仅支持数据传输类型长时任务。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**废弃版本：** -1

**需要权限：** ohos.permission.KEEP_BACKGROUND_RUNNING

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-backgroundTaskManager-function updateDataTransferProgress(context: Context, progressInfo: DataTransferProgress): void--><!--Device-backgroundTaskManager-function updateDataTransferProgress(context: Context, progressInfo: DataTransferProgress): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用运行的上下文。 |
| progressInfo | [DataTransferProgress](arkts-backgroundtasks-backgroundtaskmanager-datatransferprogress-i.md) | 是 | 长时任务通知进度信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9800005](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800005-长时任务校验失败) | Continuous task verification failed. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | System service operation failed. |
| [9800007](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800007-长时任务信息存储失败) | Continuous task storage failed. |
| [9800006](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800006-长时任务通知信息校验失败) | Notification verification failed for a continuous task. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { wantAgent, WantAgent } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  continuousTaskId : number = -1; // 保存长时任务Id
  onCreate() {
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      // 点击通知后，将要执行的动作列表
      wants: [
        {
          bundleName: 'com.example.myapplication',
          abilityName: 'EntryAbility'
        }
      ],
      // 点击通知后，动作类型
      actionType: wantAgent.OperationType.START_ABILITY,
      // 使用者自定义的一个私有值
      requestCode: 0,
      // 点击通知后，动作执行属性
      wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
    };
    let progress: backgroundTaskManager.ProgressInfo = {
      title: '通知标题', // 必填
      fileName: '通知内容', // 必填
      progressValue: 20, // 应用更新进度值，自定义
      isMute: false, // 通知进度达到100时是否静音，自定义
    };

    try {
      // 通过wantAgent模块下getWantAgent方法获取WantAgent对象
      wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: WantAgent) => {
        try {
          // 申请数据传输类型长时任务
          let list: Array<string> = ['dataTransfer'];
          backgroundTaskManager.startBackgroundRunning(this.context, list, wantAgentObj).then((res: backgroundTaskManager.ContinuousTaskNotification) => {
            console.info('Operation startBackgroundRunning succeeded');
            // 对于数据传输类的长时任务，应用可以使用res中返回的continuousTaskId来更新通知，比如发送带进度条的模板通知
            this.continuousTaskId = res.continuousTaskId;
            try {
              let progressInfo: backgroundTaskManager.DataTransferProgress = {
                continuousTaskId: this.continuousTaskId,
                wantAgent: wantAgentObj,
                progressInfo: progress,
              }
              // 更新通知
              backgroundTaskManager.updateDataTransferProgress(this.context, progressInfo);
              console.info('Operation updateDataTransferProgress succeeded');
            } catch(error) {
              console.error(`Operation updateDataTransferProgress failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
            }
          }).catch((error: BusinessError) => {
            console.error(`Operation startBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
          });
        } catch (error) {
          console.error(`Operation startBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
      });
    } catch (error) {
      console.error(`Operation getWantAgent failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```

ArkTS-Sta示例：

```TypeScript
import { backgroundTaskManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { UIAbility } from '@kit.AbilityKit';
import { wantAgent, WantAgent } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  continuousTaskId : int = -1; // 保存长时任务Id
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let wantAgentInfo: wantAgent.WantAgentInfo = {
      // 点击通知后，将要执行的动作列表
      wants: [
        {
          bundleName: 'com.example.myapplication',
          abilityName: 'EntryAbility'
        }
      ],
      // 点击通知后，动作类型
      actionType: wantAgent.OperationType.START_ABILITY,
      // 使用者自定义的一个私有值
      requestCode: 0,
      // 点击通知后，动作执行属性
      actionFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
    };
    let progress: backgroundTaskManager.ProgressInfo = {
      title: '通知标题', // 必填
      fileName: '通知内容', // 必填
      progressValue: 20, // 应用更新进度值，自定义
      isMute: false, // 通知进度达到100时是否静音，自定义
    };

    try {
      // 通过wantAgent模块下getWantAgent方法获取WantAgent对象
      wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj: WantAgent) => {
        try {
          // 申请数据传输类型长时任务
          let list: Array<string> = ['dataTransfer'];
          backgroundTaskManager.startBackgroundRunning(this.context, list, wantAgentObj).then((res: backgroundTaskManager.ContinuousTaskNotification) => {
            console.info('Operation startBackgroundRunning succeeded');
            // 对于数据传输类的长时任务，应用可以使用res中返回的continuousTaskId来更新通知，比如发送带进度条的模板通知
            this.continuousTaskId = res.continuousTaskId ?? -1;
            try {
              let progressInfo: backgroundTaskManager.DataTransferProgress = {
                continuousTaskId: this.continuousTaskId,
                wantAgent: wantAgentObj,
                progressInfo: progress,
              }
              // 更新通知
              backgroundTaskManager.updateDataTransferProgress(this.context, progressInfo);
              console.info('Operation updateDataTransferProgress succeeded');
            } catch(error) {
              console.error(`Operation updateDataTransferProgress failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
            }
          }).catch((error) => {
            console.error(`Operation startBackgroundRunning failed. code is ${error.code} message is ${error.message}`);
          });
        } catch (error) {
          console.error(`Operation startBackgroundRunning failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
        }
      });
    } catch (error) {
      console.error(`Operation getWantAgent failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
    }
  }
};
```

