# registerMissionListener（系统接口）

## registerMissionListener

```TypeScript
function registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback, callback: AsyncCallback<void>): void
```

注册任务状态监听。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback, callback: AsyncCallback<void>): void--><!--Device-distributedMissionManager-function registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | MissionDeviceInfo | 是 | 注册监听时的设备信息。 |
| options | MissionCallback | 是 | 注册的回调方法。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，注册监听成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 实现回调函数
function NotifyMissionsChanged(deviceId: string): void {
  console.info('NotifyMissionsChanged deviceId ' + JSON.stringify(deviceId));
}
function NotifySnapshot(deviceId: string, missionId: number): void {
  console.info('NotifySnapshot deviceId ' + JSON.stringify(deviceId));
  console.info('NotifySnapshot missionId ' + JSON.stringify(missionId));
}
function NotifyNetDisconnect(deviceId: string, state: number): void {
  console.info('NotifyNetDisconnect deviceId ' + JSON.stringify(deviceId));
  console.info('NotifyNetDisconnect state ' + JSON.stringify(state));
}
try {
  // 调用registerMissionListener接口
  distributedMissionManager.registerMissionListener(
    { deviceId: "" },
    {
      notifyMissionsChanged: NotifyMissionsChanged,
      notifySnapshot: NotifySnapshot,
      notifyNetDisconnect: NotifyNetDisconnect
    },
    (error: BusinessError) => {
      if (error) {
        console.error(`Failed to register mission listener. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info('registerMissionListener finished');
    });
} catch (error) {
  console.error(`Failed to register mission listener. Code: ${error.code}, message: ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import distributedMissionManager from '@ohos.distributedMissionManager';
import { BusinessError } from '@ohos.base';
// 实现回调函数
function NotifyMissionsChanged(deviceId: string): void {
  console.info('NotifyMissionsChanged deviceId ' + JSON.stringify(deviceId));
}
function NotifySnapshot(deviceId: string, missionId: int): void {
  console.info('NotifySnapshot deviceId ' + JSON.stringify(deviceId));
  console.info('NotifySnapshot missionId ' + JSON.stringify(missionId));
}
function NotifyNetDisconnect(deviceId: string, state: int): void {
  console.info('NotifyNetDisconnect deviceId ' + JSON.stringify(deviceId));
  console.info('NotifyNetDisconnect state ' + JSON.stringify(state));
}

let deviceId: distributedMissionManager.MissionDeviceInfo = { deviceId: "" }

let parm:distributedMissionManager.MissionCallback = {
  notifyMissionsChanged: NotifyMissionsChanged,
  notifySnapshot: NotifySnapshot,
  notifyNetDisconnect: NotifyNetDisconnect
}
try {
  // 调用registerMissionListener接口
  distributedMissionManager.registerMissionListener(
    deviceId,
    parm,
    (error: BusinessError|null,data:string[]|undefined) => {
      if (error) {
        console.error('registerMissionListener failed, cause: ' + JSON.stringify(error));
        return;
      }
      console.info('registerMissionListener finished');
    });
} catch (error) {
  console.error('registerMissionListener failed, cause: ' + JSON.stringify(error));
}
```


## registerMissionListener

```TypeScript
function registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback): Promise<void>
```

注册任务状态监听。使用promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback): Promise<void>--><!--Device-distributedMissionManager-function registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | MissionDeviceInfo | 是 | 注册监听时的设备信息。 |
| options | MissionCallback | 是 | 注册的回调方法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 实现回调函数
function NotifyMissionsChanged(deviceId: string): void {
  console.info('NotifyMissionsChanged deviceId ' + JSON.stringify(deviceId));
}
function NotifySnapshot(deviceId: string, missionId: number): void {
  console.info('NotifySnapshot deviceId ' + JSON.stringify(deviceId));
  console.info('NotifySnapshot missionId ' + JSON.stringify(missionId));
}
function NotifyNetDisconnect(deviceId: string, state: number): void {
  console.info('NotifyNetDisconnect deviceId ' + JSON.stringify(deviceId));
  console.info('NotifyNetDisconnect state ' + JSON.stringify(state));
}
try {
    // 调用registerMissionListener接口
    distributedMissionManager.registerMissionListener(
      { deviceId: "" },
      {
        notifyMissionsChanged: NotifyMissionsChanged,
        notifySnapshot: NotifySnapshot,
        notifyNetDisconnect: NotifyNetDisconnect
      }).then(() => {
        console.info('registerMissionListener finished. ');
    }).catch((error: BusinessError) => {
        console.error('registerMissionListener failed, cause: ' + JSON.stringify(error));
    })
} catch (error) {
    console.error('registerMissionListener failed, cause: ' + JSON.stringify(error));
}
```

ArkTS-Sta示例：

```TypeScript
import distributedMissionManager from '@ohos.distributedMissionManager';
import { BusinessError } from '@ohos.base';
// 实现回调函数
function NotifyMissionsChanged(deviceId: string): void {
  console.info('NotifyMissionsChanged deviceId ' + JSON.stringify(deviceId));
}
function NotifySnapshot(deviceId: string, missionId: int): void {
  console.info('NotifySnapshot deviceId ' + JSON.stringify(deviceId));
  console.info('NotifySnapshot missionId ' + JSON.stringify(missionId));
}
function NotifyNetDisconnect(deviceId: string, state: int): void {
  console.info('NotifyNetDisconnect deviceId ' + JSON.stringify(deviceId));
  console.info('NotifyNetDisconnect state ' + JSON.stringify(state));
}

let deviceId: distributedMissionManager.MissionDeviceInfo = { deviceId: "" }

let parm:distributedMissionManager.MissionCallback = {
  notifyMissionsChanged: NotifyMissionsChanged,
  notifySnapshot: NotifySnapshot,
  notifyNetDisconnect: NotifyNetDisconnect
}
try {
  // 调用registerMissionListener接口
  distributedMissionManager.registerMissionListener(
    deviceId,
    parm).then(() => {
    console.info('registerMissionListener finished. ');
  }).catch((error) :void=> {
    console.error('registerMissionListener failed, cause: ' + JSON.stringify(error));
  })
} catch (error) {
  console.error('registerMissionListener failed, cause: ' + JSON.stringify(error));
}
```

