# onPairingRequest（系统接口）

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## onPairingRequest

```TypeScript
function onPairingRequest(callback: Callback<PairingRequestParam>): void
```

订阅来自远程NearLink设备的配对请求事件。如果用户被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。回调返回真实设备地址，否则返回随机设备地址

只有授予了ohos.permission.NEARLINK_ACCESS权限的系统应用程序才能访问此事件。如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。回调返回真实设备地址，否则返回随机设备地址。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-remoteDevice-function onPairingRequest(callback: Callback<PairingRequestParam>): void--><!--Device-remoteDevice-function onPairingRequest(callback: Callback<PairingRequestParam>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<PairingRequestParam> | 是 | 用于监听配对请求事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| 36100099 | Operation failed. |

