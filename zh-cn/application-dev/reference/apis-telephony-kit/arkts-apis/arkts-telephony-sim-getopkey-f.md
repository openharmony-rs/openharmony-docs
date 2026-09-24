# getOpKey

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getOpKey

```TypeScript
function getOpKey(slotId: number, callback: AsyncCallback<string>): void
```

获取指定卡槽中SIM卡的opkey。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。<br>- 0：卡槽1。<br>- 1：卡槽2。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

try {
    sim.getOpKey(0, (err: BusinessError, data: string) => {
    if (err) {
      console.error("getOpKey failed, err: " + JSON.stringify(err));
    } else {
      console.info('getOpKey successfully, data: ' + JSON.stringify(data));
    }
  });
} catch (err) {
  console.error('getOpKey err: ' + JSON.stringify(err));
}
```


<a id="getopkey-1"></a>

## getOpKey

```TypeScript
function getOpKey(slotId: number): Promise<string>
```

获取指定卡槽中SIM卡的opkey。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。<br>- 0：卡槽1。<br>- 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 以Promise形式返回指定卡槽中SIM卡的opkey。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getOpKey(0).then((data: string) => {
    console.info(`getOpKey success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getOpKey failed, promise: err->${JSON.stringify(err)}`);
});
```
