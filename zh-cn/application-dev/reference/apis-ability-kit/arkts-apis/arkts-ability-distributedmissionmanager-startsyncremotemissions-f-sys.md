# startSyncRemoteMissions（系统接口）

## startSyncRemoteMissions

```TypeScript
function startSyncRemoteMissions(parameter: MissionParameter, callback: AsyncCallback<void>): void
```

开始同步远端设备的任务列表。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function startSyncRemoteMissions(parameter: MissionParameter, callback: AsyncCallback<void>): void--><!--Device-distributedMissionManager-function startSyncRemoteMissions(parameter: MissionParameter, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 同步信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数，同步远端任务列表成功时，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 开始同步远端设备的任务列表
  distributedMissionManager.startSyncRemoteMissions(
    {
      deviceId: "",
      fixConflict: false,
      tag: 0
    },
    (error: BusinessError) => {
      if (error) {
        console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info('startSyncRemoteMissions finished');}
  )
} catch (error) {
  console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import distributedMissionManager from '@ohos.distributedMissionManager';
import { BusinessError } from '@ohos.base';
let parm:distributedMissionManager.MissionParameter = {
  deviceId: "",
  fixConflict: false,
  tag: 0
}
try {
  // 开始同步远端设备的任务列表
  distributedMissionManager.startSyncRemoteMissions(
    parm,
    (error: BusinessError|null,data:string[]|undefined) => {
      if (error) {
        console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info('startSyncRemoteMissions finished');}
  )
} catch (error) {
  console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
}
```


## startSyncRemoteMissions

```TypeScript
function startSyncRemoteMissions(parameter: MissionParameter): Promise<void>
```

开始同步远端设备的任务列表。使用promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function startSyncRemoteMissions(parameter: MissionParameter): Promise<void>--><!--Device-distributedMissionManager-function startSyncRemoteMissions(parameter: MissionParameter): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 同步信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
try {
  distributedMissionManager.startSyncRemoteMissions(
    {
      deviceId: "",
      fixConflict: false,
      tag: 0
    }
  ).then(() => {
      console.info('startSyncRemoteMissions finished successfully');
    }).catch((error: BusinessError) => {
    console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import distributedMissionManager from '@ohos.distributedMissionManager';
import { BusinessError } from '@ohos.base';
let parm:distributedMissionManager.MissionParameter = {
  deviceId: "",
  fixConflict: false,
  tag: 0
}
try {
  distributedMissionManager.startSyncRemoteMissions(parm).then(() => {
    console.info('startSyncRemoteMissions finished successfully');
  }).catch((error) => {
    console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
  })
} catch (error) {
  console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
}
```

