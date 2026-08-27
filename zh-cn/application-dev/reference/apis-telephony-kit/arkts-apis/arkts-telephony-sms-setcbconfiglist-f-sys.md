# setCBConfigList（系统接口）

## 导入模块

```TypeScript
```

## setCBConfigList

```TypeScript
function setCBConfigList(configs: CBConfigListConfigs): Promise<void>
```

打开小区广播列表

**起始版本：** 23

**需要权限：** ohos.permission.RECEIVE_SMS

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configs | [CBConfigListConfigs](arkts-telephony-sms-cbconfiglistconfigs-i-sys.md) | 是 | Indicates cell broadcast configuration list configs. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | The promise returned by the setCBConfigList. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
