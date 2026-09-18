# downloadMms（系统接口）

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## downloadMms

```TypeScript
function downloadMms(context: Context, mmsParams: MmsParams, callback: AsyncCallback<void>): void
```

下载彩信。使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.RECEIVE_MMS

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文。<br>FA模型的应用Context定义见Context。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md)。 |
| mmsParams | [MmsParams](arkts-telephony-sms-mmsparams-i-sys.md) | 是 | 下载彩信的参数和回调，参考[MmsParams](arkts-telephony-sms-mmsparams-i-sys.md)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 下载彩信的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
FA模型示例：
```

```TypeScript
Stage模型示例：
```


## downloadMms

```TypeScript
function downloadMms(context: Context, mmsParams: MmsParams): Promise<void>
```

下载彩信。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.RECEIVE_MMS

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文。<br>FA模型的应用Context定义见Context。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md)。 |
| mmsParams | [MmsParams](arkts-telephony-sms-mmsparams-i-sys.md) | 是 | 发送彩信的参数和回调，参考[MmsParams](arkts-telephony-sms-mmsparams-i-sys.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回发送彩信的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

参见 [downloadMms](#downloadmms)
