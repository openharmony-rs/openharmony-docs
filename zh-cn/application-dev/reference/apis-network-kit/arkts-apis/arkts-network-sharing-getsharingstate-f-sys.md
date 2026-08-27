# getSharingState（系统接口）

## 导入模块

```TypeScript
```

## getSharingState

```TypeScript
function getSharingState(type: SharingIfaceType, callback: AsyncCallback<SharingIfaceState>): void
```

获取指定类型网络共享状态，使用 callback 异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md) | 是 | 共享类型，0：Wi-Fi 1：USB 2：BLUETOOTH。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SharingIfaceState](arkts-network-sharing-sharingifacestate-e-sys.md)&gt; | 是 | 回调函数，返回指定类型网络共享状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let SHARING_WIFI = 0;
sharing.getSharingState(SHARING_WIFI, (error: BusinessError, data: sharing.SharingIfaceState) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```


## getSharingState

```TypeScript
function getSharingState(type: SharingIfaceType): Promise<SharingIfaceState>
```

获取指定类型网络共享状态，使用 Promise 异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md) | 是 | 共享类型，0：Wi-Fi 1：USB 2：BLUETOOTH。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SharingIfaceState](arkts-network-sharing-sharingifacestate-e-sys.md)&gt; | 以 Promise 形式返回定类型网络共共享状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let SHARING_WIFI = 0;
sharing
  .getSharingState(SHARING_WIFI)
  .then((data: sharing.SharingIfaceState) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```
