# onCallStateChange

## onCallStateChange

```TypeScript
function onCallStateChange(callback: Callback<CallStateInfo>): void
```

Callback when the call state corresponding to the default sim card is updated.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-observer-function onCallStateChange(callback: Callback<CallStateInfo>): void--><!--Device-observer-function onCallStateChange(callback: Callback<CallStateInfo>): void-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CallStateInfo](arkts-telephony-observer-callstateinfo-i.md)&gt; | 是 | Indicates the callback for getting the call state and the called number. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |


## onCallStateChange

```TypeScript
function onCallStateChange(options: ObserverOptions, callback: Callback<CallStateInfo>): void
```

Callback when the call state corresponding to the monitored {@code slotId} is updated.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-observer-function onCallStateChange(options: ObserverOptions, callback: Callback<CallStateInfo>): void--><!--Device-observer-function onCallStateChange(options: ObserverOptions, callback: Callback<CallStateInfo>): void-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ObserverOptions | 是 | Indicates the options for observer. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CallStateInfo](arkts-telephony-observer-callstateinfo-i.md)&gt; | 是 | Indicates the callback for getting the call state and the called number. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

