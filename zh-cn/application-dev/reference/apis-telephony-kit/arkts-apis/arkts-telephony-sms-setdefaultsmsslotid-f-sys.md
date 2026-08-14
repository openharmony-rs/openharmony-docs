# setDefaultSmsSlotId（系统接口）

## setDefaultSmsSlotId

```TypeScript
function setDefaultSmsSlotId(slotId: int, callback: AsyncCallback<void>): void
```

设置发送短信的默认SIM卡槽ID。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-sms-function setDefaultSmsSlotId(slotId: int, callback: AsyncCallback<void>): void--><!--Device-sms-function setDefaultSmsSlotId(slotId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | SIM卡槽ID。&lt;br/&gt;- 0：卡槽1&lt;br/&gt;- 1：卡槽2&lt;br/&gt;- -1：清除默认配置 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 设置发送短信的默认SIM卡槽ID的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | Do not have sim card. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.setDefaultSmsSlotId(0, (err: BusinessError) => {
    console.info(`callback: err->${JSON.stringify(err)}.`);
});
```


## setDefaultSmsSlotId

```TypeScript
function setDefaultSmsSlotId(slotId: int): Promise<void>
```

设置发送短信的默认SIM卡槽ID。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-sms-function setDefaultSmsSlotId(slotId: int): Promise<void>--><!--Device-sms-function setDefaultSmsSlotId(slotId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | SIM卡槽ID。&lt;br/&gt;- 0：卡槽1&lt;br/&gt;- 1：卡槽2&lt;br/&gt;- -1：清除默认配置 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式异步返回设置结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | Do not have sim card. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.setDefaultSmsSlotId(0).then(() => {
    console.info(`setDefaultSmsSlotId success.`);
}).catch((err: BusinessError) => {
    console.error(`setDefaultSmsSlotId failed, promise: err->${JSON.stringify(err)}`);
});
```

