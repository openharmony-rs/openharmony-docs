# getDefaultSmsSimId

## getDefaultSmsSimId

```TypeScript
function getDefaultSmsSimId(callback: AsyncCallback<int>): void
```

获取发送短信的默认SIM卡ID。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sms-function getDefaultSmsSimId(callback: AsyncCallback<int>): void--><!--Device-sms-function getDefaultSmsSimId(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 获取默认短信SIM的SIM ID的回调函数。&lt;br/&gt;与SIM卡绑定，从1开始递增。&lt;br/&gt;无卡时返回值为-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8301001](../errorcode-telephony.md#8301001-sim卡未激活) | SIM card is not activated. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | Do not have sim card. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getDefaultSmsSimId((err: BusinessError, data: number) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## getDefaultSmsSimId

```TypeScript
function getDefaultSmsSimId(): Promise<int>
```

获取发送短信的默认SIM卡ID。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sms-function getDefaultSmsSimId(): Promise<int>--><!--Device-sms-function getDefaultSmsSimId(): Promise<int>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 以Promise形式返回发送短信的默认SIM卡ID：&lt;br/&gt;与SIM卡绑定，从1开始递增。&lt;br/&gt;无卡时返回值为-1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8301001](../errorcode-telephony.md#8301001-sim卡未激活) | SIM card is not activated. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | Do not have sim card. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let promise = sms.getDefaultSmsSimId();
promise.then((data: number) => {
    console.info(`getDefaultSmsSimId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultSmsSimId failed, promise: err->${JSON.stringify(err)}`);
});
```

