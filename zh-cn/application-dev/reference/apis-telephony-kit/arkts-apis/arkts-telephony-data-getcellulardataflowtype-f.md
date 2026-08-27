# getCellularDataFlowType

## 导入模块

```TypeScript
```

## getCellularDataFlowType

```TypeScript
function getCellularDataFlowType(callback: AsyncCallback<DataFlowType>): void
```

获取蜂窝网络的数据流类型（对应信号栏旁边的上下行箭头），使用callback方式作为异步方法。

**起始版本：** 7

**需要权限：** 
- API版本22+：ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CellularData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DataFlowType&gt; | 是 | 以callback形式异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 22+ |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.getCellularDataFlowType((err: BusinessError, contextData: data.DataFlowType) => {
    if(err) {
        console.error(`getCellularDataFlowType fail. code: ${err.code}, message: ${err.message}, contextData: ${contextData}`);
    } else {
        console.info(`getCellularDataFlowType success`);
    }
});
```


## getCellularDataFlowType

```TypeScript
function getCellularDataFlowType(): Promise<DataFlowType>
```

获取蜂窝网络的数据流类型（对应信号栏旁边的上下行箭头），使用Promise方式作为异步方法。

**起始版本：** 7

**需要权限：** 
- API版本22+：ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CellularData

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;DataFlowType & gt; | 以Promise形式返回蜂窝网络的数据流类型（对应信号栏旁边的上下行箭头）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 22+ |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.getCellularDataFlowType().then((contextData: data.DataFlowType) => {
    console.info(`getCellularDataFlowType success, contextData: ${contextData}`);
}).catch((err: BusinessError) => {
    console.error(`getCellularDataFlowType fail. code: ${err.code}, message: ${err.message}`);
});
```
