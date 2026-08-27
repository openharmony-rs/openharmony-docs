# startSyncRemoteMissions（系统接口）

## 导入模块

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## startSyncRemoteMissions

```TypeScript
function startSyncRemoteMissions(parameter: MissionParameter, callback: AsyncCallback<void>): void
```

开始同步远端设备的任务列表。使用callback异步回调。使用时须与stopSyncRemoteMissions严格配对，按"先启动、后停止"的顺序执行，同步完成后应立即停止以释放系统资源。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | MissionParameter | 是 | 同步信息，包含deviceId、fixConflict和tag字段。tag为同步标识，用于区分不同同步会话，取值需满足场景需求。fixConflict表示是否解决冲突，建议在可能存在任务冲突的场景下设置为true。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，同步远端任务列表成功时，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

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


## startSyncRemoteMissions

```TypeScript
function startSyncRemoteMissions(parameter: MissionParameter): Promise<void>
```

开始同步远端设备的任务列表。使用promise异步回调。使用时须与stopSyncRemoteMissions严格配对，按"先启动、后停止"的顺序执行，同步完成后应立即停止以释放系统资源。设备行为差异：该接口在不支持分布式业务的Wearable设备不生效。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | MissionParameter | 是 | 同步信息，包含deviceId、fixConflict和tag字段。tag为同步标识，用于区分不同同步会话，取值需满足场景需求。fixConflict表示是否解决冲突，建议在可能存在任务冲突的场景下设置为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 返回的Promise对象，操作成功时表示远端设备任务列表同步已成功启动，失败时返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

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
