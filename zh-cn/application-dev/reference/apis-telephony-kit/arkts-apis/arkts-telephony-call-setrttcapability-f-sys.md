# setRttCapability（系统接口）

## 导入模块

```TypeScript
```

## setRttCapability

```TypeScript
function setRttCapability(accountId: number, isEnable: boolean): Promise<void>
```

设置rtt功能

**起始版本：** 22

**需要权限：** ohos.permission.PLACE_CALL

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 是 | Indicates the identifier of the account to set rtt capability. |
| isEnable | boolean | 是 | Indicates whether Rtt capability is enabled. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | The promise returned by the setRttCapability. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| 8400001 | Invalid parameter value. |
| 8400002 | Operation failed. Cannot connect to service. |
| 8400003 | System internal error. |
| 8400999 | Unknown error code. |
