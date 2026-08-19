# isImsSwitchEnabledSync（系统接口）

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## isImsSwitchEnabledSync

```TypeScript
function isImsSwitchEnabledSync(slotId: int): boolean
```

判断Ims开关是否启用。调用此API返回结果。

**起始版本：** 23

<!--Device-call-function isImsSwitchEnabledSync(slotId: int): boolean--><!--Device-call-function isImsSwitchEnabledSync(slotId: int): boolean-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | 卡槽ID。<br/>- 0：卡槽1。<br/>- 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 用来返回结果。true表示Ims开关启用，false表示未启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

**示例**

```TypeScript
let slotId: number = 0;
try {
    let isEnabled: boolean = call.isImsSwitchEnabledSync(slotId);
    console.info(`isImsSwitchEnabledSync success : ${isEnabled}`);
} catch (error) {
    console.error(`isImsSwitchEnabledSync fail : err->${JSON.stringify(error)}`);  
}
```

