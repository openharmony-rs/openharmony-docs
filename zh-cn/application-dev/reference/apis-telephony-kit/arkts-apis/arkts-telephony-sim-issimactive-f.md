# isSimActive

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

<a id="issimactive"></a>
## isSimActive

```TypeScript
function isSimActive(slotId: number, callback: AsyncCallback<boolean>): void
```

Checks whether the SIM card in a specified slot is activated.

**起始版本：** 7

<!--Device-sim-function isSimActive(slotId: int, callback: AsyncCallback<boolean>): void--><!--Device-sim-function isSimActive(slotId: int, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from {@code 0} to the maximum card slot index number supported by the device. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | Indicates the callback for checking whether the SIM card in a specified slot is activated.Returns {@code true} if the SIM card is activated; returns {@code false} otherwise. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.isSimActive(0, (err: BusinessError, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});

```


<a id="issimactive-1"></a>
## isSimActive

```TypeScript
function isSimActive(slotId: number): Promise<boolean>
```

Checks whether the SIM card in a specified slot is activated.

**起始版本：** 7

<!--Device-sim-function isSimActive(slotId: int): Promise<boolean>--><!--Device-sim-function isSimActive(slotId: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from {@code 0} to the maximum card slot index number supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Returns {@code true} if the SIM card is activated; returns {@code false} otherwise. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.isSimActive(0).then((data: boolean) => {
    console.info(`isSimActive success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`isSimActive failed, promise: err->${JSON.stringify(err)}`);
});

```

