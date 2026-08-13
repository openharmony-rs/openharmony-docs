# offMission（系统接口）

## offMission

```TypeScript
function offMission(listenerId: long, callback: AsyncCallback<void>): void
```

解注册任务状态监听器。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function offMission(listenerId: long, callback: AsyncCallback<void>): void--><!--Device-missionManager-function offMission(listenerId: long, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listenerId | long | 是 | 系统任务状态监器法的index值，和监听器一一对应，由on方法返回。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16300002](../errorcode-ability.md#16300002-指定的任务监听器不存在) | The specified mission listener does not exist. |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { missionManager, UIAbility, AbilityConstant, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

class ListenerCustom implements missionManager.MissionListener {
  onMissionCreated(mission: int) {
    console.info('--------onMissionCreated-------');
  }

  onMissionDestroyed(mission: int) {
    console.info('--------onMissionDestroyed-------');
  }

  onMissionSnapshotChanged(mission: int) {
    console.info('--------onMissionSnapshotChanged-------');
  }

  onMissionMovedToFront(mission: int) {
    console.info('--------onMissionMovedToFront-------');
  }

  onMissionIconUpdated(mission: int, icon: image.PixelMap) {
    console.info('--------onMissionIconUpdated-------');
  }

  onMissionClosed(mission: int) {
    console.info('--------onMissionClosed-------');
  }

  onMissionLabelUpdated(mission: int) {
    console.info('--------onMissionLabelUpdated-------');
  }
}

let listenerId: long = -1;
let abilityWant: Want;
let context: common.UIAbilityContext;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('[Demo] EntryAbility onCreate');
    abilityWant = want;
    context = this.context;
  }

  onDestroy(): Promise<void> {
    try {
      if (listenerId !== -1) {
        missionManager.offMission(listenerId, (err: BusinessError | null) => {
          if (err?.code) {
            console.info(`error: ${err} `);
          }
        });
      }
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }
    console.info('[Demo] EntryAbility onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    // 主窗口创建后，为此Ability设置主页面
    console.info('[Demo] EntryAbility onWindowStageCreate');
    try {
      let listener = new ListenerCustom();
      listenerId = missionManager.onMission(listener);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }

    windowStage.loadContent('pages/index', (err: BusinessError | null, data) => {
      if (err?.code) {
        console.error(`Failed to load the content. Cause: ${JSON.stringify(err)}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}
```


## offMission

```TypeScript
function offMission(listenerId: long): Promise<void>
```

解注册任务状态监听。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MISSIONS

<!--Device-missionManager-function offMission(listenerId: long): Promise<void>--><!--Device-missionManager-function offMission(listenerId: long): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listenerId | long | 是 | 系统任务状态监听器的index值，和监听器一一对应，由on方法返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16300002](../errorcode-ability.md#16300002-指定的任务监听器不存在) | The specified mission listener does not exist. |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { missionManager, UIAbility, AbilityConstant, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

class ListenerCustom implements missionManager.MissionListener {
  onMissionCreated(mission: int) {
    console.info('--------onMissionCreated-------');
  }

  onMissionDestroyed(mission: int) {
    console.info('--------onMissionDestroyed-------');
  }

  onMissionSnapshotChanged(mission: int) {
    console.info('--------onMissionSnapshotChanged-------');
  }

  onMissionMovedToFront(mission: int) {
    console.info('--------onMissionMovedToFront-------');
  }

  onMissionIconUpdated(mission: int, icon: image.PixelMap) {
    console.info('--------onMissionIconUpdated-------');
  }

  onMissionClosed(mission: int) {
    console.info('--------onMissionClosed-------');
  }

  onMissionLabelUpdated(mission: int) {
    console.info('--------onMissionLabelUpdated-------');
  }
}

let listenerId: long = -1;
let abilityWant: Want;
let context: common.UIAbilityContext;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('[Demo] EntryAbility onCreate');
    abilityWant = want;
    context = this.context;
  }

  onDestroy(): Promise<void> {
    try {
      if (listenerId !== -1) {
        missionManager.offMission(listenerId).catch((err: Error) => {
          let code = (err as BusinessError).code;
          let message = (err as BusinessError).message;
          console.info(`error: ${code}, ${message} `);
        });
      }
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }
    console.info('[Demo] EntryAbility onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage) {
    // 主窗口创建后，为此Ability设置主页面
    console.info('[Demo] EntryAbility onWindowStageCreate');
    try {
      let listener = new ListenerCustom();
      listenerId = missionManager.onMission(listener);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }

    windowStage.loadContent('pages/index', (err: BusinessError | null, data) => {
      if (err?.code) {
        console.error(`Failed to load the content. Cause: ${JSON.stringify(err)}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}
```

