# offAcbStateChange

## offAcbStateChange

```TypeScript
function offAcbStateChange(callback?: Callback<AcbStateParam>): void
```

取消订阅星闪 ACB连接状态更改事件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-remoteDevice-function offAcbStateChange(callback?: Callback<AcbStateParam>): void--><!--Device-remoteDevice-function offAcbStateChange(callback?: Callback<AcbStateParam>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AcbStateParam](arkts-connectivity-remotedevice-acbstateparam-i.md)&gt; | 否 | 要监听的事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |

