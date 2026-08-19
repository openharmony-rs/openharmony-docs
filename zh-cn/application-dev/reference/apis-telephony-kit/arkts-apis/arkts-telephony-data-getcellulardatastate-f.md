# getCellularDataState

## 导入模块

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## getCellularDataState

```TypeScript
function getCellularDataState(callback: AsyncCallback<DataConnectState>): void
```

获取蜂窝数据业务的连接状态，使用callback方式作为异步方法。

**起始版本：** 23

**需要权限：** 
- API版本22+：ohos.permission.GET_NETWORK_INFO

<!--Device-data-function getCellularDataState(callback: AsyncCallback<DataConnectState>): void--><!--Device-data-function getCellularDataState(callback: AsyncCallback<DataConnectState>): void-End-->

**系统能力：** SystemCapability.Telephony.CellularData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;DataConnectState&gt; | 是 | 以callback形式异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 22+ |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.getCellularDataState((err: BusinessError, contextData: data.DataConnectState) => {
    if(err) {
        console.error(`getCellularDataState fail. code: ${err.code}, message: ${err.message}, contextData: ${contextData}`);
    } else {
        console.info(`getCellularDataState success`);
    }
});
```


## getCellularDataState

```TypeScript
function getCellularDataState(): Promise<DataConnectState>
```

获取蜂窝数据业务的连接状态，使用Promise方式作为异步方法。

**起始版本：** 23

**需要权限：** 
- API版本22+：ohos.permission.GET_NETWORK_INFO

<!--Device-data-function getCellularDataState(): Promise<DataConnectState>--><!--Device-data-function getCellularDataState(): Promise<DataConnectState>-End-->

**系统能力：** SystemCapability.Telephony.CellularData

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataConnectState&gt; | 以Promise形式返回获取PS域的连接状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 22+ |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.getCellularDataState().then((contextData: data.DataConnectState) => {
    console.info(`getCellularDataState success, contextData: ${contextData}`);
}).catch((err: BusinessError) => {
    console.error(`getCellularDataState fail. code: ${err.code}, message: ${err.message}`);
});
```

