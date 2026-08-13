# requestExemptionResource（系统接口）

## requestExemptionResource

```TypeScript
function requestExemptionResource(request: ResourceRequest): void
```

应用订阅申请豁免，使应用临时不进入待机管控。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.DEVICE_STANDBY_EXEMPTION

<!--Device-deviceStandby-function requestExemptionResource(request: ResourceRequest): void--><!--Device-deviceStandby-function requestExemptionResource(request: ResourceRequest): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.DeviceStandby

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [ResourceRequest](arkts-backgroundtasks-devicestandby-resourcerequest-i-sys.md) | 是 | 资源请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [9800004](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800004-系统服务失败) | Failed to get device standby service. Possible cause: A necessary system service is not ready. |
| [9800001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800001-内存操作失败) | Memory operation failed. |
| [9800003](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800003-ipc通信失败) | Failed to complete inner transaction. |
| [9800002](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#9800002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [18700001](../../apis-backgroundtasks-kit/errorcode-backgroundTaskMgr.md#18700001-资源申请接口信息校验失败) | Caller information verification failed. |

## 示例

```TypeScript
import { deviceStandby } from '@kit.BackgroundTasksKit';

let resRequest: deviceStandby.ResourceRequest = {
  resourceTypes: deviceStandby.ResourceType.TIMER,
  uid:10003,
  name:"com.example.app",
  duration:10,
  reason:"apply",
};
deviceStandby.requestExemptionResource(resRequest);
```

