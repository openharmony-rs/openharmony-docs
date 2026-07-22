# getSimLabel

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getSimLabel

```TypeScript
function getSimLabel(slotId: number, callback: AsyncCallback<SimLabel>): void
```

Obtains the SIM card label.

**起始版本：** 20

<!--Device-sim-function getSimLabel(slotId: int, callback: AsyncCallback<SimLabel>): void--><!--Device-sim-function getSimLabel(slotId: int, callback: AsyncCallback<SimLabel>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | SIM card slot ID. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;SimLabel&gt; | 是 | Callback used to return the SIM card label. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimLabel(0, (err: BusinessError, data: sim.SimLabel) => {
  console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});

```


## getSimLabel

```TypeScript
function getSimLabel(slotId: number): Promise<SimLabel>
```

获取SIM卡标签名称

**起始版本：** 20

<!--Device-sim-function getSimLabel(slotId: int): Promise<SimLabel>--><!--Device-sim-function getSimLabel(slotId: int): Promise<SimLabel>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽索引号 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SimLabel&gt; | 返回SIM卡标签： |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimLabel(0).then((data: sim.SimLabel) => {
  console.info(`getSimLabel success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getSimState failed, promise: err->${JSON.stringify(err)}`);
});

```

