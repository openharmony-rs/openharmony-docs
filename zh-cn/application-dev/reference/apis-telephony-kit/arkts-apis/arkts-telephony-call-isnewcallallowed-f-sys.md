# isNewCallAllowed（系统接口）

## 导入模块

```TypeScript
```

## isNewCallAllowed

```TypeScript
function isNewCallAllowed(callback: AsyncCallback<boolean>): void
```

判断是否允许再拨打一通新电话。使用callback异步回调。

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 以回调函数的方式返回结果。true表示允许拨打，false表示不可拨打。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.isNewCallAllowed((err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`isNewCallAllowed fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`isNewCallAllowed success, data->${JSON.stringify(data)}`);
    }
});
```


## isNewCallAllowed

```TypeScript
function isNewCallAllowed(): Promise<boolean>
```

判断是否允许再拨打一通新电话。使用Promise异步回调。

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | 以Promise形式异步返回结果。true表示允许拨打，false表示不可拨打。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.isNewCallAllowed().then((data: boolean) => {
    console.info(`isNewCallAllowed success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`isNewCallAllowed fail, promise: err->${JSON.stringify(err)}`);
});
```
