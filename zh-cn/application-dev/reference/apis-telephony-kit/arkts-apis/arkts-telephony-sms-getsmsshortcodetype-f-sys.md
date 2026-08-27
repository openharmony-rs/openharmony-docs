# getSmsShortCodeType（系统接口）

## 导入模块

```TypeScript
```

## getSmsShortCodeType

```TypeScript
function getSmsShortCodeType(slotId: number, destAddr: string): Promise<SmsShortCodeType>
```

获取拟发送短信的目标地址短码类型

**起始版本：** 23

**需要权限：** ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the ID of the slot holding the SIM card for sending SMS messages. The value {@code 0} indicates card slot 1, and the value {@code 1} indicates card slot 2. |
| destAddr | string | 是 | Indicates the destination address of the sending SMS. 取值范围:[0,+∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SmsShortCodeType](arkts-telephony-sms-smsshortcodetype-e-sys.md)&gt; | 返回发送目标地址的短信短码类型 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Nonsystem applications use system APIs. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | Do not have sim card. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
