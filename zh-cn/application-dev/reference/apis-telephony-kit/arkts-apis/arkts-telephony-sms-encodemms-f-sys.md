# encodeMms（系统接口）

## encodeMms

```TypeScript
function encodeMms(mms: MmsInformation, callback: AsyncCallback<Array<int>>): void
```

彩信编码。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sms-function encodeMms(mms: MmsInformation, callback: AsyncCallback<Array<int>>): void--><!--Device-sms-function encodeMms(mms: MmsInformation, callback: AsyncCallback<Array<int>>): void-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mms | [MmsInformation](arkts-telephony-sms-mmsinformation-i-sys.md) | 是 | 彩信信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;int&gt;&gt; | 是 | 指示用于获取MMS编码结果的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let mmsAcknowledgeInd: sms.MmsAcknowledgeInd = {
    transactionId: "100",
    version: sms.MmsVersionType.MMS_VERSION_1_0,
    reportAllowed: sms.ReportType.MMS_YES
};
let mmsInformation: sms.MmsInformation = {
    messageType: sms.MessageType.TYPE_MMS_ACKNOWLEDGE_IND,
    mmsType: mmsAcknowledgeInd
};
sms.encodeMms(mmsInformation, (err: BusinessError, data: number[]) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## encodeMms

```TypeScript
function encodeMms(mms: MmsInformation): Promise<Array<int>>
```

彩信编码。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sms-function encodeMms(mms: MmsInformation): Promise<Array<int>>--><!--Device-sms-function encodeMms(mms: MmsInformation): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mms | [MmsInformation](arkts-telephony-sms-mmsinformation-i-sys.md) | 是 | 彩信信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;int&gt;&gt; | 以Promise形式返回彩信编码后的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let mmsAcknowledgeInd: sms.MmsAcknowledgeInd = {
    transactionId: "100",
    version: sms.MmsVersionType.MMS_VERSION_1_0,
    reportAllowed: sms.ReportType.MMS_YES
};
let mmsInformation: sms.MmsInformation = {
    messageType: sms.MessageType.TYPE_MMS_ACKNOWLEDGE_IND,
    mmsType: mmsAcknowledgeInd
};
sms.encodeMms(mmsInformation).then((data: number[]) => {
    console.info(`encodeMms success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`encodeMms failed, promise: err->${JSON.stringify(err)}`);
});
```

