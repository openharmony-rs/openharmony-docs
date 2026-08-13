# onRttModifyInd（系统接口）

## onRttModifyInd

```TypeScript
function onRttModifyInd(callback: Callback<RttEventInfo>): void
```

订阅rtt通话变化

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-call-function onRttModifyInd(callback: Callback<RttEventInfo>): void--><!--Device-call-function onRttModifyInd(callback: Callback<RttEventInfo>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[RttEventInfo](arkts-telephony-call-rtteventinfo-i-sys.md)&gt; | 是 | Indicates the callback for getting the rtt event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 8400001 | Invalid parameter value. |
| 8400002 | Operation failed. Cannot connect to service. |
| 8400003 | System internal error. |
| 8400999 | Unknown error code. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

