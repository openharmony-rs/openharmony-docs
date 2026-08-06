# onConnectionStateChange

## onConnectionStateChange

```TypeScript
function onConnectionStateChange(callback: Callback<ConnectionStateParam>): void
```

订阅星闪连接状态更改事件。 如果用户有ohos.permission.GET\_NEARLINK\_PEER\_MAC权限，则返回真实设备地址。否则返回一个随机的设备地址。 只有授予了ohos.permission.NEARLINK\_ACCESS权限的应用程序才能访问此事件。 如果应用被赋予了ohos.permission.GET\_NEARLINK\_PEER\_MAC权限。 回调返回真实设备地址，否则返回随机设备地址。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-remoteDevice-function onConnectionStateChange(callback: Callback<ConnectionStateParam>): void--><!--Device-remoteDevice-function onConnectionStateChange(callback: Callback<ConnectionStateParam>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ConnectionStateParam&gt; | 是 | 用于监听事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

