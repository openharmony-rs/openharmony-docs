# hangUpCall

## 导入模块

```TypeScript
```

## hangUpCall

```TypeScript
function hangUpCall(callback: AsyncCallback<void>): void
```

挂断电话。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ANSWER_CALL or ohos.permission.SET_TELEPHONY_STATE or ohos.permission.MANAGE_CALL_FOR_DEVICES

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当挂断电话成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs.<br>**适用版本：** 9 - 22 |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.hangUpCall((err: BusinessError) => {
    if (err) {
        console.error(`hangUpCall fail, err->Code${err.code}, message:${err.message}`);
    } else {
        console.info(`hangUpCall success.`);
    }
});
```
