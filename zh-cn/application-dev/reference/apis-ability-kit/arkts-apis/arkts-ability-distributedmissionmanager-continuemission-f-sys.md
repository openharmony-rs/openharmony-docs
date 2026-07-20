# continueMission（系统接口）

## 导入模块

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

<a id="continuemission"></a>
## continueMission

```TypeScript
function continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback, callback: AsyncCallback<void>): void
```

通过指定任务ID（missionId）的方式进行迁移任务。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback, callback: AsyncCallback<void>): void--><!--Device-distributedMissionManager-function continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [ContinueDeviceInfo](arkts-ability-continuedeviceinfo-i-sys.md) | 是 | 迁移信息。 |
| options | [ContinueCallback](arkts-ability-continuecallback-i-sys.md) | 是 | 迁移任务完成回调函数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，迁移任务完成时，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-系统服务工作异常) | The system ability work abnormally. |
| [16300502](../errorcode-DistributedSchedule.md#16300502-获取指定的missionid的missioninfo失败) | Failed to get the missionInfo of the specified missionId. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-远端未安装应用且不支持免安装) | The application is not installed on the remote end and installation-free isnot supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-远端未安装应用但支持免安装需使用免安装标识重试) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-操作设备必须是迁移的应用所在的设备或需迁移到的目标设备) | The operation device must be the device where the application to be continuedis located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-本地迁移任务已在进行中) | The local continuation task is already in progress. |

**示例：**

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


<a id="continuemission-1"></a>
## continueMission

```TypeScript
function continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback): Promise<void>
```

通过指定任务ID（missionId）的方式进行迁移任务。使用promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback): Promise<void>--><!--Device-distributedMissionManager-function continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [ContinueDeviceInfo](arkts-ability-continuedeviceinfo-i-sys.md) | 是 | 迁移信息。 |
| options | [ContinueCallback](arkts-ability-continuecallback-i-sys.md) | 是 | 迁移任务完成回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-系统服务工作异常) | The system ability work abnormally. |
| [16300502](../errorcode-DistributedSchedule.md#16300502-获取指定的missionid的missioninfo失败) | Failed to get the missionInfo of the specified missionId. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-远端未安装应用且不支持免安装) | The application is not installed on the remote end and installation-free isnot supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-远端未安装应用但支持免安装需使用免安装标识重试) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-操作设备必须是迁移的应用所在的设备或需迁移到的目标设备) | The operation device must be the device where the application to be continuedis located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-本地迁移任务已在进行中) | The local continuation task is already in progress. |

**示例：**

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


<a id="continuemission-2"></a>
## continueMission

```TypeScript
function continueMission(parameter: ContinueMissionInfo, callback: AsyncCallback<void>): void
```

通过指定包名（bundleName）的方式进行迁移任务。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function continueMission(parameter: ContinueMissionInfo, callback: AsyncCallback<void>): void--><!--Device-distributedMissionManager-function continueMission(parameter: ContinueMissionInfo, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [ContinueMissionInfo](arkts-ability-continuemissioninfo-i-sys.md) | 是 | 迁移信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，通过指定包名迁移任务完成时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-系统服务工作异常) | The system ability work abnormally. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-远端未安装应用且不支持免安装) | The application is not installed on the remote end and installation-free isnot supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-远端未安装应用但支持免安装需使用免安装标识重试) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-操作设备必须是迁移的应用所在的设备或需迁移到的目标设备) | The operation device must be the device where the application to be continuedis located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-本地迁移任务已在进行中) | The local continuation task is already in progress. |
| [16300507](../errorcode-DistributedSchedule.md#16300507-获取指定的bundlename的missioninfo失败) | Failed to get the missionInfo of the specified bundle name. |

**示例：**

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


<a id="continuemission-3"></a>
## continueMission

```TypeScript
function continueMission(parameter: ContinueMissionInfo): Promise<void>
```

通过指定包名（bundleName）的方式进行迁移任务。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-distributedMissionManager-function continueMission(parameter: ContinueMissionInfo): Promise<void>--><!--Device-distributedMissionManager-function continueMission(parameter: ContinueMissionInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Mission

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| parameter | [ContinueMissionInfo](arkts-ability-continuemissioninfo-i-sys.md) | 是 | 迁移信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-系统服务工作异常) | The system ability work abnormally. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-远端未安装应用且不支持免安装) | The application is not installed on the remote end and installation-free isnot supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-远端未安装应用但支持免安装需使用免安装标识重试) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-操作设备必须是迁移的应用所在的设备或需迁移到的目标设备) | The operation device must be the device where the application to be continuedis located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-本地迁移任务已在进行中) | The local continuation task is already in progress. |
| [16300507](../errorcode-DistributedSchedule.md#16300507-获取指定的bundlename的missioninfo失败) | Failed to get the missionInfo of the specified bundle name. |

**示例：**

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

