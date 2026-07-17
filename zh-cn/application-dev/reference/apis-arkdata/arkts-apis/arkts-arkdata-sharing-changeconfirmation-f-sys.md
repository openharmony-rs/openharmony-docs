# changeConfirmation（系统接口）

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## changeConfirmation

```TypeScript
function changeConfirmation(sharingResource: string, state: State, callback: AsyncCallback<Result<void>>): void
```

根据共享资源标识更改共享邀请的状态，使用callback异步回调。

**起始版本：** 11

<!--Device-sharing-function changeConfirmation(sharingResource: string, state: State, callback: AsyncCallback<Result<void>>): void--><!--Device-sharing-function changeConfirmation(sharingResource: string, state: State, callback: AsyncCallback<Result<void>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sharingResource | string | 是 | 端云共享数据的资源标识。 |
| state | [State](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-state-e.md) | 是 | 更改邀请的状态。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Result<void>> | 是 | 回调函数。返回更改邀请状态的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudData.sharing.changeConfirmation('sharing_resource_test', cloudData.sharing.State.STATE_REJECTED, ((err: BusinessError, result) => {
  if (err) {
    console.error(`change confirmation failed, code is ${err.code},message is ${err.message}`);
    return;
  }
  console.info(`change confirmation succeeded, result: ${result}`);
}))

```


## changeConfirmation

```TypeScript
function changeConfirmation(sharingResource: string, state: State): Promise<Result<void>>
```

根据共享资源标识更改共享邀请的状态，使用Promise异步回调。

**起始版本：** 11

<!--Device-sharing-function changeConfirmation(sharingResource: string, state: State): Promise<Result<void>>--><!--Device-sharing-function changeConfirmation(sharingResource: string, state: State): Promise<Result<void>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sharingResource | string | 是 | 端云共享数据的资源标识。 |
| state | [State](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-state-e.md) | 是 | 更改邀请的状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Result<void>> | Promise对象，返回更改共享邀请状态的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed,application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudData.sharing.changeConfirmation('sharing_resource_test', cloudData.sharing.State.STATE_REJECTED).then((result) => {
  console.info(`change confirmation succeeded, result: ${result}`);
}).catch((err: BusinessError) => {
  console.error(`change confirmation failed, code is ${err.code},message is ${err.message}`);
})

```

