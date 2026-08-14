# stopSyncRemoteMissions（系统接口）

## stopSyncRemoteMissions

```TypeScript
function stopSyncRemoteMissions(parameter: MissionDeviceInfo, callback: AsyncCallback<void>): void
```

停止同步远端设备的任务列表。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function stopSyncRemoteMissions(parameter: MissionDeviceInfo, callback: AsyncCallback<void>): void--><!--Device-distributedMissionManager-function stopSyncRemoteMissions(parameter: MissionDeviceInfo, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | MissionDeviceInfo | 是 | 同步信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，停止同步远端任务列表成功时，err为undefined，否则为错误对象。 |

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

try {
  // 停止同步远端设备的任务列表
  distributedMissionManager.stopSyncRemoteMissions(
    {
      deviceId: ""
    },
    (error: BusinessError) => {
      if (error) {
        console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info('stopSyncRemoteMissions finished');}
  )
} catch (error) {
  console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import distributedMissionManager from '@ohos.distributedMissionManager';
import { BusinessError } from '@ohos.base';
let deviceId: distributedMissionManager.MissionDeviceInfo = { deviceId: "" }
try {
  // 停止同步远端设备的任务列表
  distributedMissionManager.stopSyncRemoteMissions(
    deviceId,
    (error: BusinessError|null,data:string[]|undefined) => {
      if (error) {
        console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info('stopSyncRemoteMissions finished');}
  )
} catch (error) {
  console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
}
```


## stopSyncRemoteMissions

```TypeScript
function stopSyncRemoteMissions(parameter: MissionDeviceInfo): Promise<void>
```

停止同步远端设备的任务列表。使用promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function stopSyncRemoteMissions(parameter: MissionDeviceInfo): Promise<void>--><!--Device-distributedMissionManager-function stopSyncRemoteMissions(parameter: MissionDeviceInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | MissionDeviceInfo | 是 | 同步信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  distributedMissionManager.stopSyncRemoteMissions(
    {
      deviceId: ""
    }).then(() => {
      console.info('stopSyncRemoteMissions finished successfully');
    }).catch((error: BusinessError) => {
    console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import distributedMissionManager from '@ohos.distributedMissionManager';
import { BusinessError } from '@ohos.base';
let deviceId: distributedMissionManager.MissionDeviceInfo = { deviceId: "" }
try {
  distributedMissionManager.stopSyncRemoteMissions(deviceId).then(() => {
    console.info('stopSyncRemoteMissions finished successfully');
  }).catch((error) => {
    console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
  })
} catch (error) {
  console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
}
```

