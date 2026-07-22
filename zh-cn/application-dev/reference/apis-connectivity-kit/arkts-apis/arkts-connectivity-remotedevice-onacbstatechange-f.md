# onAcbStateChange

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## onAcbStateChange

```TypeScript
function onAcbStateChange(callback: Callback<AcbStateParam>): void
```

订阅NearLink ACB连接状态变化事件。ACB采用异步双向链路。  
> **说明**  
> 如果该用户具有ohos.permission.GET_NEARLINK_PEER_MAC权限，则真实设备地址为  
> 返回。  
> 否则，将返回一个随机的设备地址。

只有授予了ohos.permission.NEARLINK_ACCESS权限的应用程序才能访问此事件。如果应用被赋予了ohos.permission.GET_NEARLINK_PEER_MAC权限。回调返回真实设备地址，否则返回随机设备地址。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-remoteDevice-function onAcbStateChange(callback: Callback<AcbStateParam>): void--><!--Device-remoteDevice-function onAcbStateChange(callback: Callback<AcbStateParam>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;AcbStateParam&gt; | 是 | 要监听的事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

