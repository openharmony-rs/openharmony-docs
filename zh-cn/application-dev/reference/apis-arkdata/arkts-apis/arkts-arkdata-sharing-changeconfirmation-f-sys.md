# changeConfirmation（系统接口）

## changeConfirmation

```TypeScript
function changeConfirmation(sharingResource: string, state: State, callback: AsyncCallback<Result<void>>): void
```

根据共享资源标识更改共享邀请的状态，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sharing-function changeConfirmation(sharingResource: string, state: State, callback: AsyncCallback<Result<void>>): void--><!--Device-sharing-function changeConfirmation(sharingResource: string, state: State, callback: AsyncCallback<Result<void>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sharingResource | string | 是 | 端云共享数据的资源标识。 |
| state | State | 是 | 更改邀请的状态。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Result&lt;void&gt;&gt; | 是 | 回调函数。返回更改邀请状态的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudData.sharing.changeConfirmation('sharing_resource_test', cloudData.sharing.State.STATE_REJECTED, ((err: BusinessError|null, result) => {
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

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sharing-function changeConfirmation(sharingResource: string, state: State): Promise<Result<void>>--><!--Device-sharing-function changeConfirmation(sharingResource: string, state: State): Promise<Result<void>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sharingResource | string | 是 | 端云共享数据的资源标识。 |
| state | State | 是 | 更改邀请的状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;void&gt;&gt; | Promise对象，返回更改共享邀请状态的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

cloudData.sharing.changeConfirmation('sharing_resource_test', cloudData.sharing.State.STATE_REJECTED).then((result) => {
  console.info(`change confirmation succeeded, result: ${result}`);
}).catch((err) => {
  console.error(`change confirmation failed, code is ${err.code},message is ${err.message}`);
})
```

