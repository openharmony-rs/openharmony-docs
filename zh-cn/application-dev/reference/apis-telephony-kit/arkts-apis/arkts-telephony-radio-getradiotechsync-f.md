# getRadioTechSync

## 导入模块

```TypeScript
```

## getRadioTechSync

```TypeScript
function getRadioTechSync(slotId: number): NetworkRadioTech
```

获取当前接入的CS域和PS域无线接入技术。CS域为电路交换域，PS为分组交换域。

**起始版本：** 18

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NetworkRadioTech](arkts-telephony-radio-networkradiotech-i.md) | 返回当前接入的CS域和PS域技术。CS域为电路交换域，PS为分组交换域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
let slotId: number = 0;
let networkRadioTech: radio.NetworkRadioTech = radio.getRadioTechSync(slotId);
console.info(`getRadioTechSync success, NetworkRadioTech->${JSON.stringify(networkRadioTech)}`);
```
