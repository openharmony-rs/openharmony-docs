# offCellInfoChange（系统接口）

## offCellInfoChange

```TypeScript
function offCellInfoChange(callback?: Callback<Array<CellInformation>>): void
```

Cancel callback when the cell information is updated.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-observer-function offCellInfoChange(callback?: Callback<Array<CellInformation>>): void--><!--Device-observer-function offCellInfoChange(callback?: Callback<Array<CellInformation>>): void-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;[CellInformation](arkts-telephony-observer-cellinformation-t-sys.md)&gt;&gt; | 否 | Indicates the callback to unsubscribe from the cellInfoChange event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

