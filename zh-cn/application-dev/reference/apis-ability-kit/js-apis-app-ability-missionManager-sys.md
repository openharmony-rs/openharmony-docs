# @ohos.app.ability.missionManager (missionManager)(系统接口)

missionManager模块提供系统任务管理能力，包括对系统任务执行锁定、解锁、清理、切换到前台等操作。

> **说明：**
>
> - 本模块同时支持ArkTs-Dyn、ArkTs-Sta。
>
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口均为系统接口，三方应用不支持调用。

## 导入模块

```ts
import { missionManager } from '@kit.AbilityKit';
```

## 权限列表

ohos.permission.MANAGE_MISSIONS

## missionManager.on('mission')

on(type:'mission', listener: MissionListener): number

注册系统任务状态监听器。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTs-Dyn起始版本：** 9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type     | string   | 是       | 监听的任务名称。固定值：'mission'，表示系统任务状态监听器。 |
| listener | [MissionListener](js-apis-inner-application-missionListener-sys.md) | 是 | 系统任务监听器。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 监听器的index值，由系统创建，在注册系统任务状态监听时分配，和监听器一一对应&nbsp;。 |

**示例：**

```ts
import { missionManager, UIAbility, AbilityConstant, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

let listener: missionManager.MissionListener = {
  onMissionCreated: (mission: number) => {console.info('--------onMissionCreated-------');},
  onMissionDestroyed: (mission: number) => {console.info('--------onMissionDestroyed-------');},
  onMissionSnapshotChanged: (mission: number) => {console.info('--------onMissionSnapshotChanged-------');},
  onMissionMovedToFront: (mission: number) => {console.info('--------onMissionMovedToFront-------');},
  onMissionIconUpdated: (mission: number, icon: image.PixelMap) => {console.info('--------onMissionIconUpdated-------');},
  onMissionClosed: (mission: number) => {console.info('--------onMissionClosed-------');},
  onMissionLabelUpdated: (mission: number) => {console.info('--------onMissionLabelUpdated-------');}
};

let listenerId = -1;
let abilityWant: Want;
let context: common.UIAbilityContext;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('[Demo] EntryAbility onCreate');
    abilityWant = want;
    context = this.context;
  }

  onDestroy() {
    try {
      if (listenerId !== -1) {
        missionManager.off('mission', listenerId).catch((err: BusinessError) => {
          console.info(`err ${JSON.stringify(err)}`);
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
      listenerId = missionManager.on('mission', listener);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }

    windowStage.loadContent('pages/index', (err, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause: ${JSON.stringify(err)}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}
```

## missionManager.onMission<sup>23+</sup>

onMission(listener: MissionListener): long

注册系统任务状态监听器。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明             |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| listener | [MissionListener](js-apis-inner-application-missionListener-sys.md) | 是   | 系统任务监听器。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                |
| -------- | ----------------------- |
| 201      | Permission denied.      |
| 202      | Not system application. |

**返回值：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| long | 监听器的index值，由系统创建，在注册系统任务状态监听时分配，和监听器一一对应&nbsp;。 |

**示例：**

```ts
// ArkTS-Sta示例
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

## missionManager.off('mission')

off(type: 'mission', listenerId: number, callback: AsyncCallback&lt;void&gt;): void

解注册任务状态监听器。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTs-Dyn起始版本：** 9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type     | string   | 是       | 取消监听的任务名称。固定值：'mission'，表示系统任务状态监听器。 |
| listenerId | number | 是 | 系统任务状态监器法的index值，和监听器一一对应，由on方法返回。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300002 | The specified mission listener does not exist. |

**示例：**

```ts
import { missionManager, UIAbility, AbilityConstant, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

let listener: missionManager.MissionListener = {
  onMissionCreated: (mission: number) => {console.info('--------onMissionCreated-------');},
  onMissionDestroyed: (mission: number) => {console.info('--------onMissionDestroyed-------');},
  onMissionSnapshotChanged: (mission: number) => {console.info('--------onMissionSnapshotChanged-------');},
  onMissionMovedToFront: (mission: number) => {console.info('--------onMissionMovedToFront-------');},
  onMissionIconUpdated: (mission: number, icon: image.PixelMap) => {console.info('--------onMissionIconUpdated-------');},
  onMissionClosed: (mission: number) => {console.info('--------onMissionClosed-------');},
  onMissionLabelUpdated: (mission: number) => {console.info('--------onMissionLabelUpdated-------');}
};

let listenerId = -1;
let abilityWant: Want;
let context: common.UIAbilityContext;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('[Demo] EntryAbility onCreate');
    abilityWant = want;
    context = this.context;
  }

  onDestroy() {
    try {
      if (listenerId !== -1) {
        missionManager.off('mission', listenerId, (err: BusinessError) => {
          console.info(`${err.code}`);
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
      listenerId = missionManager.on('mission', listener);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }

    windowStage.loadContent('pages/index', (err: BusinessError, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause: ${JSON.stringify(err)}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}
```

## missionManager.offMission<sup>23+</sup>

offMission(listenerId: long, callback: AsyncCallback\<void\>): void

解注册任务状态监听器。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTs-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                      | 必填 | 说明                                                         |
| ---------- | ------------------------- | ---- | ------------------------------------------------------------ |
| listenerId | long                      | 是   | 系统任务状态监器法的index值，和监听器一一对应，由on方法返回。 |
| callback   | AsyncCallback&lt;void&gt; | 是   | 执行结果回调函数。                                           |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 201      | Permission denied.                             |
| 202      | Not system application.                        |
| 16300002 | The specified mission listener does not exist. |

**示例：**

```ts
// ArkTS-Sta示例
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

## missionManager.off('mission')

off(type: 'mission', listenerId: number): Promise&lt;void&gt;

解注册任务状态监听，以promise方式返回执行结果。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTs-Dyn起始版本：** 9

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type     | string   | 是       | 取消监听的任务名称。固定值：'mission'，表示系统任务状态监听器。 |
| listenerId | number | 是 | 系统任务状态监听器的index值，和监听器一一对应，由on方法返回。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300002 | The specified mission listener does not exist. |

**示例：**

```ts
import { missionManager, UIAbility, AbilityConstant, common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

let listener: missionManager.MissionListener = {
  onMissionCreated: (mission: number) => {console.info('--------onMissionCreated-------');},
  onMissionDestroyed: (mission: number) => {console.info('--------onMissionDestroyed-------');},
  onMissionSnapshotChanged: (mission: number) => {console.info('--------onMissionSnapshotChanged-------');},
  onMissionMovedToFront: (mission: number) => {console.info('--------onMissionMovedToFront-------');},
  onMissionIconUpdated: (mission: number, icon: image.PixelMap) => {console.info('--------onMissionIconUpdated-------');},
  onMissionClosed: (mission: number) => {console.info('--------onMissionClosed-------');},
  onMissionLabelUpdated: (mission: number) => {console.info('--------onMissionLabelUpdated-------');}
};

let listenerId = -1;
let abilityWant: Want;
let context: common.UIAbilityContext;

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info('[Demo] EntryAbility onCreate');
    abilityWant = want;
    context = this.context;
  }

  onDestroy() {
    try {
      if (listenerId !== -1) {
        missionManager.off('mission', listenerId).catch((err: BusinessError) => {
          console.info(`${err.code}`);
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
      listenerId = missionManager.on('mission', listener);
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }

    windowStage.loadContent('pages/index', (err: BusinessError, data) => {
      if (err.code) {
        console.error(`Failed to load the content. Cause: ${JSON.stringify(err)}`);
        return;
      }
      console.info(`Succeeded in loading the content. Data: ${JSON.stringify(data)}`);
    });
  }
}
```

## missionManager.offMission<sup>23+</sup>

offMission(listenerId: long): Promise\<void>

解注册任务状态监听，以promise方式返回执行结果。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTs-Sta起始版本：** 23

**参数：**

| 参数名     | 类型 | 必填 | 说明                                                         |
| ---------- | ---- | ---- | ------------------------------------------------------------ |
| listenerId | long | 是   | 系统任务状态监听器的index值，和监听器一一对应，由on方法返回。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 201      | Permission denied.                             |
| 202      | Not system application.                        |
| 16300002 | The specified mission listener does not exist. |

**示例：**

```ts
// ArkTS-Sta示例
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

## missionManager.getMissionInfo

ArkTS-Dyn: getMissionInfo(deviceId: string, missionId: number, callback: AsyncCallback&lt;MissionInfo&gt;): void

ArkTS-Sta: getMissionInfo(deviceId: string, missionId: int, callback: AsyncCallback&lt;MissionInfo&gt;): void

获取任务信息，以异步回调的方式返回任务信息。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| missionId | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是 | 任务ID。 |
| callback | AsyncCallback&lt;[MissionInfo](js-apis-inner-application-missionInfo-sys.md)&gt; | 是 | 执行结果回调函数，返回任务信息。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 1;

missionManager.getMissionInfos('', 10)
  .then((allMissions: Array<missionManager.MissionInfo>) => {
    try {
      if (allMissions && allMissions.length > 0) {
        testMissionId = allMissions[0].missionId;
      }

      missionManager.getMissionInfo('', testMissionId,
        (error: BusinessError | null, mission: missionManager.MissionInfo | undefined) => {
          if (error) {
            console.error(`getMissionInfo failed, error.code: ${error.code}, error.message: ${error.message}`);
          } else {
            console.info(`mission.missionId = ${mission?.missionId}`);
            console.info(`mission.runningState = ${mission?.runningState}`);
            console.info(`mission.lockedState = ${mission?.lockedState}`);
            console.info(`mission.timestamp = ${mission?.timestamp}`);
            console.info(`mission.label = ${mission?.label}`);
            console.info(`mission.iconPath = ${mission?.iconPath}`);
          }
        });
    } catch (paramError) {
      let code = (paramError as BusinessError).code;
      let message = (paramError as BusinessError).message;
      console.error(`error: ${code}, ${message} `);
    }
  })
  .catch((err: Error) => {
    console.info(`${JSON.stringify(err)}`);
  });
```

## missionManager.getMissionInfo

ArkTS-Dyn: getMissionInfo(deviceId: string, missionId: number): Promise&lt;MissionInfo&gt;

ArkTS-Sta: getMissionInfo(deviceId: string, missionId: int): Promise&lt;MissionInfo&gt;

获取任务信息，以promise方式返回任务信息。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[MissionInfo](js-apis-inner-application-missionInfo-sys.md)&gt; | 任务信息。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 1;

try {
  missionManager.getMissionInfo('', testMissionId).then((data: missionManager.MissionInfo) => {
    console.info(`getMissionInfo successfully. Data: ${JSON.stringify(data)}`);
  }).catch((e: Error) => {
    let error = e as BusinessError;
    console.error(`getMissionInfo failed. Cause: ${error.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getMissionInfo failed. Cause: ${err.message}`);
}
```

## missionManager.getMissionInfos

ArkTS-Dyn: getMissionInfos(deviceId: string, numMax: number, callback: AsyncCallback&lt;Array&lt;MissionInfo&gt;&gt;): void

ArkTS-Sta: getMissionInfos(deviceId: string, numMax: int, callback: AsyncCallback&lt;Array&lt;MissionInfo&gt;&gt;): void

获取所有任务信息，以回调函数的方式返回任务信息数组。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| numMax | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务信息数量上限。 |
| callback | AsyncCallback&lt;Array&lt;[MissionInfo](js-apis-inner-application-missionInfo-sys.md)&gt;&gt; | 是 | 执行结果回调函数，返回任务信息数组。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10,
    (error: BusinessError | null, missions: Array<missionManager.MissionInfo> | undefined) => {
      if (error) {
        console.error(`getMissionInfos failed, error.code: ${error.code}, error.message: ${error.message}`);
      } else {
        console.info(`size = ${missions?.length}`);
        console.info(`missions = ${JSON.stringify(missions)}`);
      }
    });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

## missionManager.getMissionInfos

ArkTS-Dyn: getMissionInfos(deviceId: string, numMax: number): Promise&lt;Array&lt;MissionInfo&gt;&gt;

ArkTS-Sta: getMissionInfos(deviceId: string, numMax: int): Promise&lt;Array&lt;MissionInfo&gt;&gt;

获取所有任务信息，以promise的方式返回任务信息数组。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| numMax | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务信息数量上限。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;Array&lt;[MissionInfo](js-apis-inner-application-missionInfo-sys.md)&gt;&gt; | 任务信息数组。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10).then((data: Array<missionManager.MissionInfo>) => {
    console.info(`getMissionInfos successfully. Data: ${JSON.stringify(data)}`);
  }).catch((err: Error) => {
    let error: BusinessError = err as BusinessError;
    console.error(`getMissionInfos failed. Cause: ${error.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getMissionInfos failed. Cause: ${err.message}`);
}
```

## missionManager.getMissionSnapShot

ArkTS-Dyn: getMissionSnapShot(deviceId: string, missionId: number, callback: AsyncCallback&lt;MissionSnapshot&gt;): void

ArkTS-Sta: getMissionSnapShot(deviceId: string, missionId: int, callback: AsyncCallback&lt;MissionSnapshot&gt;): void

获取任务快照，以回调函数的方式返回快照内容。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |
| callback | AsyncCallback&lt;[MissionSnapshot](js-apis-inner-application-missionSnapshot-sys.md)&gt; | 是 | 执行结果回调函数，返回任务快照信息。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.getMissionSnapShot('', testMissionId,
    (err: BusinessError | null, data: missionManager.MissionSnapshot | undefined) => {
      if (err) {
        console.error(`getMissionSnapShot failed: ${err.message}`);
      } else {
        console.info(`getMissionSnapShot successfully: ${JSON.stringify(data)}`);
      }
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getMissionSnapShot failed: ${err.message}`);
}
```

## missionManager.getMissionSnapShot

ArkTS-Dyn: getMissionSnapShot(deviceId: string, missionId: number): Promise&lt;MissionSnapshot&gt;

ArkTS-Dyn: getMissionSnapShot(deviceId: string, missionId: int): Promise&lt;MissionSnapshot&gt;

获取任务快照，以promise的方式返回快照内容。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[MissionSnapshot](js-apis-inner-application-missionSnapshot-sys.md)&gt; | 任务快照信息。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.getMissionSnapShot('', testMissionId).then((data: missionManager.MissionSnapshot) => {
    console.info(`getMissionSnapShot successfully. Data: ${JSON.stringify(data)}`);
  }).catch((err: Error) => {
    let error: BusinessError = err as BusinessError;
    console.error(`getMissionSnapShot failed. Cause: ${error.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getMissionSnapShot failed. Cause: ${err.message}`);
}
```

## missionManager.getLowResolutionMissionSnapShot

ArkTS-Dyn: getLowResolutionMissionSnapShot(deviceId: string, missionId: number, callback: AsyncCallback\<MissionSnapshot>): void

ArkTS-Sta: getLowResolutionMissionSnapShot(deviceId: string, missionId: int, callback: AsyncCallback\<MissionSnapshot>): void

获取任务低分辨率快照。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |
| callback | AsyncCallback&lt;[MissionSnapshot](js-apis-inner-application-missionSnapshot-sys.md)&gt; | 是 | 执行结果回调函数，返回任务快照信息。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.getLowResolutionMissionSnapShot('', testMissionId,
    (err: BusinessError | null, data: missionManager.MissionSnapshot | undefined) => {
      if (err) {
        console.error(`getLowResolutionMissionSnapShot failed: ${err.message}`);
      } else {
        console.info(`getLowResolutionMissionSnapShot successfully: ${JSON.stringify(data)}`);
      }
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getLowResolutionMissionSnapShot failed: ${err.message}`);
}
```

## missionManager.getLowResolutionMissionSnapShot

ArkTS-Dyn: getLowResolutionMissionSnapShot(deviceId: string, missionId: number): Promise\<MissionSnapshot>

ArkTS-Sta: getLowResolutionMissionSnapShot(deviceId: string, missionId: int): Promise\<MissionSnapshot>

获取任务低分辨率快照。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| deviceId | string | 是 | 设备ID，本机默认为空字符串。 |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[MissionSnapshot](js-apis-inner-application-missionSnapshot-sys.md)&gt; | 任务快照信息。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.getLowResolutionMissionSnapShot('', testMissionId).then((data: missionManager.MissionSnapshot) => {
    console.info(`getLowResolutionMissionSnapShot successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: Error) => {
    let err: BusinessError = error as BusinessError;
    console.error(`getLowResolutionMissionSnapShot failed. Cause: ${err.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`getLowResolutionMissionSnapShot failed. Cause: ${err.message}`);
}
```

## missionManager.lockMission

ArkTS-Dyn: lockMission(missionId: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: lockMission(missionId: int, callback: AsyncCallback&lt;void&gt;): void

锁定指定任务id的任务，以回调函数的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300001 | Mission not found. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.lockMission(testMissionId, (err: BusinessError | null, data: undefined) => {
    if (err) {
      console.error(`lockMission failed: ${err.message}`);
    } else {
      console.info(`lockMission successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`lockMission failed: ${err.message}`);
}
```

## missionManager.lockMission

ArkTS-Dyn: lockMission(missionId: number): Promise&lt;void&gt;

ArkTS-Sta: lockMission(missionId: int): Promise&lt;void&gt;

锁定指定任务id的任务，以promise方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300001 | Mission not found. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.lockMission(testMissionId).then((data) => {
    console.info(`lockMission successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: Error) => {
    let err: BusinessError = error as BusinessError;
    console.error(`lockMission failed. Cause: ${err.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`lockMission failed. Cause: ${err.message}`);
}
```

## missionManager.unlockMission

ArkTS-Dyn: unlockMission(missionId: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: unlockMission(missionId: int, callback: AsyncCallback&lt;void&gt;): void

解锁指定任务id的任务，以回调函数的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300001 | Mission not found. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.unlockMission(testMissionId, (err: BusinessError | null, data: undefined) => {
    if (err) {
      console.error(`unlockMission failed: ${err.message}`);
    } else {
      console.info(`unlockMission successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`unlockMission failed: ${err.message}`);
}
```

## missionManager.unlockMission

ArkTS-Dyn: unlockMission(missionId: number): Promise&lt;void&gt;

ArkTS-Sta: unlockMission(missionId: int): Promise&lt;void&gt;

解锁指定任务id的任务，以promise的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300001 | Mission not found. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.unlockMission(testMissionId).then((data) => {
    console.info(`unlockMission successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: Error) => {
    let err: BusinessError = error as BusinessError;
    console.error(`unlockMission failed. Cause: ${error.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`unlockMission failed. Cause: ${err.message}`);
}
```

## missionManager.clearMission

ArkTS-Dyn: clearMission(missionId: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: clearMission(missionId: int, callback: AsyncCallback&lt;void&gt;): void

清理指定任务id的任务，无论该任务是否被锁定，以回调函数的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.clearMission(testMissionId, (err: BusinessError | null, data: undefined) => {
    if (err) {
      console.error(`clearMission failed: ${err.message}`);
    } else {
      console.info(`clearMission successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearMission failed: ${err.message}`);
}
```

## missionManager.clearMission

ArkTS-Dyn: clearMission(missionId: number): Promise&lt;void&gt;

ArkTS-Sta: clearMission(missionId: int): Promise&lt;void&gt;

清理指定任务id的任务，无论该任务是否被锁定，以promise的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.clearMission(testMissionId).then((data) => {
    console.info(`clearMission successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: Error) => {
    let err: BusinessError = error as BusinessError;
    console.error(`clearMission failed. Cause: ${err.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearMission failed. Cause: ${err.message}`);
}
```

## missionManager.clearAllMissions

clearAllMissions(callback: AsyncCallback&lt;void&gt;): void

清理所有未锁定的任务，以回调函数的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.clearAllMissions((error) => {
    if (error) {
      let err: BusinessError = error as BusinessError;
      console.error(`clearAllMissions failed: ${err.message}`);
    } else {
      console.info('clearAllMissions successfully.');
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearAllMissions failed: ${err.message}`);
}
```

## missionManager.clearAllMissions

clearAllMissions(): Promise&lt;void&gt;

清理所有未锁定的任务，以promise的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------------------------------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.clearAllMissions().then((data) => {
    console.info(`clearAllMissions successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: Error) => {
    let err: BusinessError = error as BusinessError;
    console.error(`clearAllMissions failed: ${err.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`clearAllMissions failed: ${err.message}`);
}
```

## missionManager.moveMissionToFront

ArkTS-Dyn: moveMissionToFront(missionId: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: moveMissionToFront(missionId: int, callback: AsyncCallback&lt;void&gt;): void

把指定任务id的任务切到前台，以回调函数的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId, (err: BusinessError | null, data: undefined) => {
    if (err) {
      console.error(`moveMissionToFront failed: ${err.message}`);
    } else {
      console.info(`moveMissionToFront successfully: ${JSON.stringify(data)}`);
    }
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed: ${err.message}`);
}
```

## missionManager.moveMissionToFront

ArkTS-Dyn: moveMissionToFront(missionId: number, options: StartOptions, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: moveMissionToFront(missionId: int, options: StartOptions, callback: AsyncCallback&lt;void&gt;): void

把指定任务id的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等，以回调函数的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |
| options | [StartOptions](js-apis-app-ability-startOptions.md) | 是 | 启动参数选项，用于指定任务切到前台时的窗口模式，设备ID等。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId, { windowMode: 101 },
    (err: BusinessError | null, data: undefined) => {
      if (err) {
        console.error(`moveMissionToFront failed: ${err.message}`);
      } else {
        console.info(`moveMissionToFront successfully: ${JSON.stringify(data)}`);
      }
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed: ${err.message}`);
}
```

## missionManager.moveMissionToFront

ArkTS-Dyn: moveMissionToFront(missionId: number, options?: StartOptions): Promise&lt;void&gt;

ArkTS-Sta: moveMissionToFront(missionId: int, options?: StartOptions): Promise&lt;void&gt;

把指定任务id的任务切到前台，同时指定任务切换到前台时的启动参数，例如窗口模式、设备ID等，以promise的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionId | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 任务ID。 |
| options | [StartOptions](js-apis-app-ability-startOptions.md) | 否 | 启动参数选项，用于指定任务切到前台时的窗口模式，设备ID等。默认为空，表示按照默认启动参数。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000009 | An ability cannot be started or stopped in Wukong mode. |

**示例：**

```ts
import { missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let testMissionId = 2;

try {
  missionManager.moveMissionToFront(testMissionId).then((data) => {
    console.info(`moveMissionToFront successfully. Data: ${JSON.stringify(data)}`);
  }).catch((error: Error) => {
    let err: BusinessError = error as BusinessError;
    console.error(`moveMissionToFront failed. Cause: ${err.message}`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`moveMissionToFront failed. Cause: ${err.message}`);
}
```

## missionManager.moveMissionsToForeground<sup>10+</sup>

ArkTS-Dyn: moveMissionsToForeground(missionIds: Array&lt;number&gt;, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: moveMissionsToForeground(missionIds: Array&lt;int&gt;, callback: AsyncCallback&lt;void&gt;): void

将指定任务批量切到前台，以回调函数的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionIds | ArkTS-Dyn: Array&lt;number&gt;<br>ArkTS-Sta: Array&lt;int> | 是 | 任务ID数组。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, error code: ${error.code}, error msg: ${error.message}.`);
      return;
    }
    if (missionInfos.length < 1) {
      return;
    }

    let toShows = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState == abilityManager.AbilityState.BACKGROUND) {
        toShows.push(missionInfo.missionId);
      }
    }
    missionManager.moveMissionsToForeground(toShows, (err: BusinessError, data: void) => {
      if (err) {
        console.error(`moveMissionsToForeground failed: ${err.message}`);
      } else {
        console.info(`moveMissionsToForeground successfully: ${JSON.stringify(data)}`);
      }
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

ArkTS-Sta示例：

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10,
    (error: BusinessError | null, missionInfos: Array<missionManager.MissionInfo> | undefined) => {
      if (error?.code) {
        console.error(`getMissionInfos failed, error  ${JSON.stringify(error)}.`);
        return;
      }
      if (!missionInfos || missionInfos.length < 1) {
        return;
      }

      let toShows = new Array<int>();
      for (let missionInfo of missionInfos) {
        if (missionInfo.abilityState == abilityManager.AbilityState.BACKGROUND) {
          toShows.push(missionInfo.missionId);
        }
      }
      missionManager.moveMissionsToForeground(toShows, (err: BusinessError | null, data: undefined) => {
        if (err) {
          console.error(`moveMissionsToForeground failed: ${err.message}`);
        } else {
          console.info(`moveMissionsToForeground successfully: ${JSON.stringify(data)}`);
        }
      });
    });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

## missionManager.moveMissionsToForeground<sup>10+</sup>

ArkTS-Dyn: moveMissionsToForeground(missionIds: Array&lt;number&gt;, topMission: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: moveMissionsToForeground(missionIds: Array&lt;int&gt;, topMission: int, callback: AsyncCallback&lt;void&gt;): void

将指定任务批量切换到前台，并将任务ID等于topMission的任务移动到最顶层，以回调函数的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionIds | ArkTS-Dyn: Array&lt;number&gt;<br/>ArkTS-Sta: Array&lt;int> | 是 | 任务ID数组。 |
| topMission | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是 | 待移动到最顶层的任务ID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 执行结果回调函数。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, error code: ${error.code}, error msg: ${error.message}.`);
      return;
    }
    if (missionInfos.length < 1) {
      return;
    }

    let toShows = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState == abilityManager.AbilityState.BACKGROUND) {
        toShows.push(missionInfo.missionId);
      }
    }
    missionManager.moveMissionsToForeground(toShows, toShows[0], (err: BusinessError, data: void) => {
      if (err) {
        console.error(`moveMissionsToForeground failed: ${err.message}`);
      } else {
        console.info(`moveMissionsToForeground successfully: ${JSON.stringify(data)}`);
      }
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

ArkTS-Sta示例：

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10,
    (error: BusinessError | null, missionInfos: Array<missionManager.MissionInfo> | undefined) => {
      if (error?.code) {
        console.error(`getMissionInfos failed, error ${error}.`);
        return;
      }
      if (!missionInfos || missionInfos.length < 1) {
        return;
      }

      let toShows = new Array<int>();
      for (let missionInfo of missionInfos) {
        if (missionInfo.abilityState == abilityManager.AbilityState.BACKGROUND) {
          toShows.push(missionInfo.missionId);
        }
      }
      missionManager.moveMissionsToForeground(toShows, toShows[0], (err: BusinessError | null, data: undefined) => {
        if (err) {
          console.error(`moveMissionsToForeground failed: ${err.message}`);
        } else {
          console.info(`moveMissionsToForeground successfully: ${JSON.stringify(data)}`);
        }
      });
    });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

## missionManager.moveMissionsToForeground<sup>10+</sup>

ArkTS-Dyn: moveMissionsToForeground(missionIds: Array&lt;number&gt;, topMission?: number): Promise&lt;void&gt;

ArkTS-Sta: moveMissionsToForeground(missionIds: Array&lt;int&gt;, topMission?: int): Promise&lt;void&gt;

将指定任务批量切到前台，并将任务ID等于topMission的任务移动到最顶层，以promise的方式返回。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionIds | ArkTS-Dyn: Array&lt;number&gt;<br/>ArkTS-Sta: Array&lt;int> | 是 | 任务ID数组。 |
| topMission | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 否 | 待移动到最顶层的任务ID。默认值为-1，表示将默认任务移动到最顶层。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, error code: ${error.code}, error msg: ${error.message}`);
      return;
    }
    if (missionInfos.length < 1) {
      return;
    }

    let toShows = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState == abilityManager.AbilityState.BACKGROUND) {
        toShows.push(missionInfo.missionId);
      }
    }
    missionManager.moveMissionsToForeground(toShows, toShows[0]).then(() => {
      console.info(`moveMissionsToForeground is called`);
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

ArkTS-Sta示例：

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10,
    (error: BusinessError | null, missionInfos: Array<missionManager.MissionInfo> | undefined) => {
      if (error?.code) {
        console.error(`getMissionInfos failed, error ${JSON.stringify(error)}.`);
        return;
      }
      if (!missionInfos || missionInfos.length < 1) {
        return;
      }

      let toShows = new Array<int>();
      for (let missionInfo of missionInfos) {
        if (missionInfo.abilityState == abilityManager.AbilityState.BACKGROUND) {
          toShows.push(missionInfo.missionId);
        }
      }
      missionManager.moveMissionsToForeground(toShows, toShows[0]).then(() => {
        console.info(`moveMissionsToForeground is called`);
      });
    });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

## missionManager.moveMissionsToBackground<sup>10+</sup>

ArkTS-Dyn: moveMissionsToBackground(missionIds: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;): void

ArkTS-Sta: moveMissionsToBackground(missionIds: Array&lt;int&gt;, callback: AsyncCallback&lt;Array&lt;int&gt;&gt;): void

将指定任务批量切到后台，以回调函数的方式返回，返回的结果任务ID按被隐藏时的任务层级排序。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionIds | ArkTS-Dyn: Array&lt;number&gt;<br/>ArkTS-Sta: Array&lt;int> | 是 | 任务ID数组。 |
| callback | ArkTS-Dyn: AsyncCallback&lt;Array&lt;number&gt;&gt;<br>ArkTS-Sta: AsyncCallback&lt;Array&lt;int&gt;&gt; | 是 | 执行结果回调函数。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, error code: ${error.code}, error msg: ${error.message}`);
      return;
    }

    let toHides = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState ==  abilityManager.AbilityState.FOREGROUND) {
        toHides.push(missionInfo.missionId);
      }
    }
    missionManager.moveMissionsToBackground(toHides, (err: BusinessError, data: Array<number>) => {
      if (err) {
        console.error(`moveMissionsToBackground failed: ${err.message}`);
      } else {
        console.info(`moveMissionsToBackground successfully: ${JSON.stringify(data)}`);
      }
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

ArkTS-Sta示例：

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10,
    (error: BusinessError | null, missionInfos: Array<missionManager.MissionInfo> | undefined) => {
      if (error?.code) {
        console.error(`getMissionInfos failed, error ${JSON.stringify(error)}.`);
        return;
      }

      if (!missionInfos || missionInfos.length === 0) {
        console.info('No mission infos available or missionInfos is undefined');
        return;
      }

      let toHides = new Array<int>();
      for (let missionInfo of missionInfos) {
        if (missionInfo.abilityState == abilityManager.AbilityState.FOREGROUND) {
          toHides.push(missionInfo.missionId);
        }
      }
      missionManager.moveMissionsToBackground(toHides, (err: BusinessError | null, data: Array<int> | undefined) => {
        if (err) {
          console.error(`moveMissionsToBackground failed: ${err.message}`);
        } else {
          console.info(`moveMissionsToBackground successfully: ${JSON.stringify(data)}`);
        }
      });
    });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

## missionManager.moveMissionsToBackground<sup>10+</sup>

ArkTS-Dyn: moveMissionsToBackground(missionIds : Array&lt;number&gt;): Promise&lt;Array&lt;number&gt;&gt;

ArkTS-Sta: moveMissionsToBackground(missionIds : Array&lt;int&gt;): Promise&lt;Array&lt;int&gt;&gt;

将指定任务批量切到后台，以promise的方式返回，返回的结果按被隐藏时的任务层级排序。

**需要权限**：ohos.permission.MANAGE_MISSIONS

**系统能力**：SystemCapability.Ability.AbilityRuntime.Mission

**系统接口**：此接口为系统接口。

**ArkTs-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| missionIds | ArkTS-Dyn: Array&lt;number&gt;<br/>ArkTS-Sta: Array&lt;int> | 是 | 任务ID数组。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt;<br>ArkTS-Sta: Promise&lt;Array&lt;int&gt;&gt; | promise方式返回执行结果。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10, (error: BusinessError, missionInfos: Array<missionManager.MissionInfo>) => {
    if (error.code) {
      console.error(`getMissionInfos failed, error code: ${error.code}, error msg: ${error.message}`);
      return;
    }

    let toHides = new Array<number>();
    for (let missionInfo of missionInfos) {
      if (missionInfo.abilityState ==  abilityManager.AbilityState.FOREGROUND) {
        toHides.push(missionInfo.missionId);
      }
    }
    missionManager.moveMissionsToBackground(toHides).then((hideRes: Array<number>) => {
      console.info(`moveMissionsToBackground is called, res: ${hideRes}`);
    });
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

ArkTS-Sta示例：

```ts
import { abilityManager, missionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  missionManager.getMissionInfos('', 10,
    (error: BusinessError | null, missionInfos: Array<missionManager.MissionInfo> | undefined) => {
      if (error?.code) {
        console.error(`getMissionInfos failed, error ${JSON.stringify(error)}.`);
        return;
      }

      if (!missionInfos || missionInfos.length === 0) {
        console.info('No mission infos available or missionInfos is undefined');
        return;
      }

      let toHides = new Array<int>();
      for (let missionInfo of missionInfos) {
        if (missionInfo.abilityState == abilityManager.AbilityState.FOREGROUND) {
          toHides.push(missionInfo.missionId);
        }
      }
      missionManager.moveMissionsToBackground(toHides).then((hideRes: Array<int>) => {
        console.info(`moveMissionsToBackground is called, res: ${hideRes}`);
      });
    });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```