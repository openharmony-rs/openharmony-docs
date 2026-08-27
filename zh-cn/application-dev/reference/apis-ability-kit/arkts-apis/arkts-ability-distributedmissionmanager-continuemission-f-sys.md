# continueMission（系统接口）

## 导入模块

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## continueMission

```TypeScript
function continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback, callback: AsyncCallback<void>): void
```

通过指定任务ID（missionId）的方式进行迁移任务。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | ContinueDeviceInfo | 是 | 通过任务ID方式迁移时的迁移信息，包含源设备ID、目标设备ID、任务ID等。 |
| options | ContinueCallback | 是 | 通过任务ID方式迁移任务完成时的回调函数，用于接收迁移结果。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，迁移任务完成时，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-系统服务工作异常) | The system ability work abnormally. |
| [16300502](../errorcode-DistributedSchedule.md#16300502-获取指定的missionid的missioninfo失败) | Failed to get the missionInfo of the specified missionId. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-远端未安装应用且不支持免安装) | The application is not installed on the remote end and installation-free is not supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-远端未安装应用但支持免安装需使用免安装标识重试) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-操作设备必须是迁移的应用所在的设备或需迁移到的目标设备) | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-本地迁移任务已在进行中) | The local continuation task is already in progress. |

**示例**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 实现回调函数
function onContinueDone(resultCode: number): void {
  console.info('onContinueDone resultCode: ' + JSON.stringify(resultCode));
};
try {
  // 通过任务ID方式迁移任务
  // missionId需通过系统API获取实际任务ID
  distributedMissionManager.continueMission(
    {
      srcDeviceId: '',
      dstDeviceId: '',
      missionId: 1,
      wantParam: {'key': 'value'}
    },
    { onContinueDone: onContinueDone },
    (error: BusinessError) => {
      if (error) {
        console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info('continueMission finished');
  })
} catch (error) {
  console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
}
```


## continueMission

```TypeScript
function continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback): Promise<void>
```

通过指定任务ID（missionId）的方式进行迁移任务。使用promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | ContinueDeviceInfo | 是 | 迁移信息，包含源设备ID、目标设备ID、任务ID和自定义参数等字段。 |
| options | ContinueCallback | 是 | 迁移任务完成回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 返回的Promise对象，操作成功时表示通过任务ID方式迁移任务已完成，失败时返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-系统服务工作异常) | The system ability work abnormally. |
| [16300502](../errorcode-DistributedSchedule.md#16300502-获取指定的missionid的missioninfo失败) | Failed to get the missionInfo of the specified missionId. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-远端未安装应用且不支持免安装) | The application is not installed on the remote end and installation-free is not supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-远端未安装应用但支持免安装需使用免安装标识重试) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-操作设备必须是迁移的应用所在的设备或需迁移到的目标设备) | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-本地迁移任务已在进行中) | The local continuation task is already in progress. |

**示例**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 实现回调函数
function onContinueDone(resultCode: number): void {
  console.info('onContinueDone resultCode: ' + JSON.stringify(resultCode));
};
try {
  // 通过任务ID方式迁移任务
  // missionId需通过系统API获取实际任务ID
  distributedMissionManager.continueMission(
    {
      srcDeviceId: '',
      dstDeviceId: '',
      missionId: 1,
      wantParam: {'key': 'value'}
    },
    { onContinueDone: onContinueDone }).then(() => {
      console.info('continueMission finished successfully');
    }).catch((error: BusinessError) => {
    console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
}
```


## continueMission

```TypeScript
function continueMission(parameter: ContinueMissionInfo, callback: AsyncCallback<void>): void
```

通过指定包名（bundleName）的方式进行迁移任务。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | ContinueMissionInfo | 是 | 迁移信息，包含源设备ID、目标设备ID、应用包名和自定义参数等字段。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，通过指定包名迁移任务完成时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-系统服务工作异常) | The system ability work abnormally. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-远端未安装应用且不支持免安装) | The application is not installed on the remote end and installation-free is not supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-远端未安装应用但支持免安装需使用免安装标识重试) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-操作设备必须是迁移的应用所在的设备或需迁移到的目标设备) | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-本地迁移任务已在进行中) | The local continuation task is already in progress. |
| [16300507](../errorcode-DistributedSchedule.md#16300507-获取指定的bundlename的missioninfo失败) | Failed to get the missionInfo of the specified bundle name. |

**示例**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  distributedMissionManager.continueMission(
    {
      srcDeviceId: '',
      dstDeviceId: '',
      bundleName: 'ohos.test.continueapp',
      wantParam: {'key': 'value'}
    },
    (error: BusinessError) => {
      if (error) {
        console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info('continueMission finished');
  })
} catch (error) {
  console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
}
```


## continueMission

```TypeScript
function continueMission(parameter: ContinueMissionInfo): Promise<void>
```

通过指定包名（bundleName）的方式进行迁移任务。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | ContinueMissionInfo | 是 | 迁移信息，包含源设备ID、目标设备ID、应用包名和自定义参数等字段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 返回的Promise对象，操作成功时表示通过包名方式迁移任务已完成，失败时返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-系统服务工作异常) | The system ability work abnormally. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-远端未安装应用且不支持免安装) | The application is not installed on the remote end and installation-free is not supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-远端未安装应用但支持免安装需使用免安装标识重试) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-操作设备必须是迁移的应用所在的设备或需迁移到的目标设备) | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-本地迁移任务已在进行中) | The local continuation task is already in progress. |
| [16300507](../errorcode-DistributedSchedule.md#16300507-获取指定的bundlename的missioninfo失败) | Failed to get the missionInfo of the specified bundle name. |

**示例**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    distributedMissionManager.continueMission(
      {
        srcDeviceId: '',
        dstDeviceId: '',
        bundleName: 'ohos.test.continueapp',
        wantParam: {"key": "value"}
      }
    ).then(() => {
        console.info('continueMission finished successfully');
    }).catch((error: BusinessError) => {
        console.error(`Failed to continue mission. Code: ${error.code}, message: ${error.message}`);
    });
} catch (error) {
    console.error(`Failed to continue mission. Code: ${error.code}, message: ${error.message}`);
}
```
