# queryParticipants（系统接口）

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## queryParticipants

```TypeScript
function queryParticipants(sharingResource: string, callback: AsyncCallback<Result<Array<Participant>>>): void
```

根据指定的共享资源标识查询当前共享的参与者，使用callback异步回调。

**起始版本：** 11

<!--Device-sharing-function queryParticipants(sharingResource: string, callback: AsyncCallback<Result<Array<Participant>>>): void--><!--Device-sharing-function queryParticipants(sharingResource: string, callback: AsyncCallback<Result<Array<Participant>>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sharingResource | string | 是 | 端云共享数据的资源标识。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Result<Array<Participant>>> | 是 | 回调函数。返回查找共享参与者的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudData.sharing.queryParticipants('sharing_resource_test', ((err: BusinessError, result) => {
  if (err) {
    console.error(`query participants failed, code is ${err.code},message is ${err.message}`);
    return;
  }
  console.info(`query participants succeeded, result: ${result}`);
}))

```


## queryParticipants

```TypeScript
function queryParticipants(sharingResource: string): Promise<Result<Array<Participant>>>
```

根据指定的共享资源标识查询当前共享的参与者，使用Promise异步回调。

**起始版本：** 11

<!--Device-sharing-function queryParticipants(sharingResource: string): Promise<Result<Array<Participant>>>--><!--Device-sharing-function queryParticipants(sharingResource: string): Promise<Result<Array<Participant>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sharingResource | string | 是 | 端云共享数据的资源标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Result<Array<Participant>>> | Promise对象，返回查询共享参与者的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudData.sharing.queryParticipants('sharing_resource_test').then((result) => {
  console.info(`query participants succeeded, result: ${result}`);
}).catch((err: BusinessError) => {
  console.error(`query participants failed, code is ${err.code},message is ${err.message}`);
})

```

