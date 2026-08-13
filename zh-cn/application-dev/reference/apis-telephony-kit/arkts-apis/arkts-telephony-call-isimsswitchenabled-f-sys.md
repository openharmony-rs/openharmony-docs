# isImsSwitchEnabled（系统接口）

## isImsSwitchEnabled

```TypeScript
function isImsSwitchEnabled(slotId: int, callback: AsyncCallback<boolean>): void
```

判断Ims开关是否启用。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-function isImsSwitchEnabled(slotId: int, callback: AsyncCallback<boolean>): void--><!--Device-call-function isImsSwitchEnabled(slotId: int, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | 卡槽ID。&lt;br/&gt;- 0：卡槽1。&lt;br/&gt;- 1：卡槽2。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 以回调函数的方式返回判断Ims开关是否启用的结果。true表示Ims开关启用，false表示未启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.isImsSwitchEnabled(0, (err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`isImsSwitchEnabled fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`isImsSwitchEnabled success, data->${JSON.stringify(data)}`);
    }
});
```


## isImsSwitchEnabled

```TypeScript
function isImsSwitchEnabled(slotId: int): Promise<boolean>
```

判断Ims开关是否启用。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-function isImsSwitchEnabled(slotId: int): Promise<boolean>--><!--Device-call-function isImsSwitchEnabled(slotId: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | 卡槽ID。&lt;br/&gt;- 0：卡槽1。&lt;br/&gt;- 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 以Promise形式异步返回结果。true表示Ims开关启用，false表示未启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.isImsSwitchEnabled(0).then((data: boolean) => {
    console.info(`isImsSwitchEnabled success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`isImsSwitchEnabled fail, promise: err->${JSON.stringify(err)}`);
});
```

