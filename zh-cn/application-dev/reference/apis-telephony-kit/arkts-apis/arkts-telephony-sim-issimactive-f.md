# isSimActive

## 导入模块

```TypeScript
```

## isSimActive

```TypeScript
function isSimActive(slotId: number, callback: AsyncCallback<boolean>): void
```

获取指定卡槽SIM卡是否激活。使用callback异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回指定卡槽是否激活。   - true:激活。   - false：未激活。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.isSimActive(0, (err: BusinessError, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## isSimActive

```TypeScript
function isSimActive(slotId: number): Promise<boolean>
```

获取指定卡槽SIM卡是否激活。使用Promise异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | 以Promise形式返回指定卡槽是否激活。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.isSimActive(0).then((data: boolean) => {
    console.info(`isSimActive success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`isSimActive failed, promise: err->${JSON.stringify(err)}`);
});
```
