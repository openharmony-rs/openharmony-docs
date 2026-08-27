# unRegisterMissionListener（系统接口）

## 导入模块

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## unRegisterMissionListener

```TypeScript
function unRegisterMissionListener(parameter: MissionDeviceInfo, callback: AsyncCallback<void>): void
```

取消任务状态监听。使用callback异步回调。停止监听前，请确保已通过registerMissionListener完成注册，否则调用无效。成功调用后，系统将不再监听该设备上的任务状态变化。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | MissionDeviceInfo | 是 | 取消监听时指定的设备信息，deviceId为设备标识符。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，取消监听成功，err为undefined，否则为错误对象。 |

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
  // 取消任务状态监听
  distributedMissionManager.unRegisterMissionListener(
    { deviceId: "" },
    (error: BusinessError) => {
      if (error) {
          console.error(`unRegisterMissionListener failed. Code: ${error.code}, message: ${error.message}`);
          return;
      }
      console.info('unRegisterMissionListener finished');
  })
} catch (error) {
    console.error('unRegisterMissionListener failed, cause: ' + JSON.stringify(error));
}
```


## unRegisterMissionListener

```TypeScript
function unRegisterMissionListener(parameter: MissionDeviceInfo): Promise<void>
```

取消任务状态监听。使用promise异步回调。停止监听前，请确保已通过registerMissionListener完成注册，否则调用无效。成功调用后，系统将不再监听该设备上的任务状态变化。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | MissionDeviceInfo | 是 | 取消监听时的设备信息，deviceId为设备标识符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 返回的Promise对象，操作成功时表示任务状态监听已成功取消，失败时返回错误信息。 |

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
  distributedMissionManager.unRegisterMissionListener({deviceId: ""}).then(() => {
    console.info('unRegisterMissionListener finished successfully');
  }).catch((error: BusinessError) => {
      console.error(`unRegisterMissionListener failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
    console.error('unRegisterMissionListener failed, cause: ' + JSON.stringify(error));
}
```
