# setVoiceMailInfo（系统接口）

## setVoiceMailInfo

```TypeScript
function setVoiceMailInfo(slotId: int, mailName: string, mailNumber: string, callback: AsyncCallback<void>): void
```

Sets the voice mail information.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-sim-function setVoiceMailInfo(slotId: int, mailName: string, mailNumber: string, callback: AsyncCallback<void>): void--><!--Device-sim-function setVoiceMailInfo(slotId: int, mailName: string, mailNumber: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | Indicates the card slot index number, ranging from {@code 0} to the maximum card slot index number supported by the device. |
| mailName | string | 是 | Indicates the name of voice mail. |
| mailNumber | string | 是 | Indicates the number of voice mail. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | The callback of setVoiceMailInfo. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8301002](../errorcode-telephony.md#8301002-sim卡读取数据或者更新数据失败) | The SIM card failed to read or update data. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.setVoiceMailInfo(0, "mail", "xxx@xxx.com", (err: BusinessError) => {
    console.info(`callback: err->${JSON.stringify(err)}`);
});
```


## setVoiceMailInfo

```TypeScript
function setVoiceMailInfo(slotId: int, mailName: string, mailNumber: string): Promise<void>
```

Sets the voice mail information.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-sim-function setVoiceMailInfo(slotId: int, mailName: string, mailNumber: string): Promise<void>--><!--Device-sim-function setVoiceMailInfo(slotId: int, mailName: string, mailNumber: string): Promise<void>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | Indicates the card slot index number, ranging from {@code 0} to the maximum card slot index number supported by the device. |
| mailName | string | 是 | Indicates the name of voice mail. |
| mailNumber | string | 是 | Indicates the number of voice mail. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the setVoiceMailInfo. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8301002](../errorcode-telephony.md#8301002-sim卡读取数据或者更新数据失败) | The SIM card failed to read or update data. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.setVoiceMailInfo(0, "mail", "xxx@xxx.com").then(() => {
    console.info(`setVoiceMailInfo success.`);
}).catch((err: BusinessError) => {
    console.error(`setVoiceMailInfo failed, promise: err->${JSON.stringify(err)}`);
});
```

