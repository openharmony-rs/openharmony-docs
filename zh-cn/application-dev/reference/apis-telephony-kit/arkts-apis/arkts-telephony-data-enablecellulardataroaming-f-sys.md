# enableCellularDataRoaming（系统接口）

## 导入模块

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## enableCellularDataRoaming

```TypeScript
function enableCellularDataRoaming(slotId: int, callback: AsyncCallback<void>): void
```

启用蜂窝数据漫游，使用callback方式作为异步方法。

**起始版本：** 23

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-data-function enableCellularDataRoaming(slotId: int, callback: AsyncCallback<void>): void--><!--Device-data-function enableCellularDataRoaming(slotId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Telephony.CellularData

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | 卡槽ID。<br/>- 0：卡槽1。 <br/>- 1：卡槽2。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 以callback形式异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.enableCellularDataRoaming(0, (err: BusinessError) => {
    if(err) {
        console.error(`enableCellularDataRoaming fail. code: ${err.code}, message: ${err.message}`);
    } else {
        console.info(`enableCellularDataRoaming success`);
    }
});
```


## enableCellularDataRoaming

```TypeScript
function enableCellularDataRoaming(slotId: int): Promise<void>
```

启用蜂窝数据漫游，使用Promise方式作为异步方法。

**起始版本：** 23

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-data-function enableCellularDataRoaming(slotId: int): Promise<void>--><!--Device-data-function enableCellularDataRoaming(slotId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Telephony.CellularData

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | 卡槽ID。<br/>- 0：卡槽1。 <br/>- 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回启用结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.enableCellularDataRoaming(0).then(() => {
    console.info(`enableCellularDataRoaming success.`);
}).catch((err: BusinessError) => {
    console.error(`enableCellularDataRoaming fail. code: ${err.code}, message: ${err.message}`);
});
```

