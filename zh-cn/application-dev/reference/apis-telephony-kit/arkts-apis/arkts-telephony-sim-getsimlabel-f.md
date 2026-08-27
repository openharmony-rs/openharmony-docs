# getSimLabel

## 导入模块

```TypeScript
```

## getSimLabel

```TypeScript
function getSimLabel(slotId: number, callback: AsyncCallback<SimLabel>): void
```

查看卡槽ID和SIM卡的对应关系：  
- 卡槽1对应SIM卡1或SIM卡2  
- 卡槽2对应SIM卡2或ESIMX

**起始版本：** 20

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SimLabel](arkts-telephony-sim-simlabel-i.md)&gt; | 是 | 回调函数。获取SIM卡标签信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

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

获取SIM卡的标签信息。使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SimLabel](arkts-telephony-sim-simlabel-i.md)&gt; | 回调函数。获取SIM卡标签信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimLabel(0).then((data: sim.SimLabel) => {
  console.info(`getSimLabel success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getSimLabel failed, promise: err->${JSON.stringify(err)}`);
});
```
