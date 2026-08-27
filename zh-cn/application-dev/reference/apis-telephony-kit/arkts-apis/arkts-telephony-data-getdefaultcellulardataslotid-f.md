# getDefaultCellularDataSlotId

## 导入模块

```TypeScript
```

## getDefaultCellularDataSlotId

```TypeScript
function getDefaultCellularDataSlotId(callback: AsyncCallback<number>): void
```

获取默认移动数据的SIM卡，使用callback方式作为异步方法。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CellularData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 以callback形式异步返回结果。   - 0：卡槽1。    - 1：卡槽2。   - 2：esim和天际通场景下，默认移动数 据的slotId为2。 |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.getDefaultCellularDataSlotId((err: BusinessError, contextData: number) => {
    if(err) {
        console.error(`getDefaultCellularDataSlotId fail. code: ${err.code}, message: ${err.message}, contextData: ${contextData}`);
    } else {
        console.info(`getDefaultCellularDataSlotId success`);
    }
});
```


## getDefaultCellularDataSlotId

```TypeScript
function getDefaultCellularDataSlotId(): Promise<number>
```

获取默认移动数据的SIM卡，使用Promise方式作为异步方法。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CellularData

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | 以Promise形式返回获取默认移动数据的SIM卡。 |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.getDefaultCellularDataSlotId().then((contextData: number) => {
    console.info(`getDefaultCellularDataSlotId success, contextData: ${contextData}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultCellularDataSlotId fail. code: ${err.code}, message: ${err.message}`);
});
```
