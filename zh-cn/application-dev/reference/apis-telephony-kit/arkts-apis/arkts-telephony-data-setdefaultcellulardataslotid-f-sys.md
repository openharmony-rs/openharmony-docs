# setDefaultCellularDataSlotId（系统接口）

## 导入模块

```TypeScript
```

## setDefaultCellularDataSlotId

```TypeScript
function setDefaultCellularDataSlotId(slotId: number, callback: AsyncCallback<void>): void
```

设置默认移动数据的SIM卡，使用callback方式作为异步方法。

**起始版本：** 7

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CellularData

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | SIM卡槽ID。   - 0：卡槽1。    - 1：卡槽2。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 以callback形式异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8301001](../errorcode-telephony.md#8301001-sim卡未激活) | SIM card is not activated. |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.setDefaultCellularDataSlotId(0, (err: BusinessError) => {
    if(err) {
        console.error(`setDefaultCellularDataSlotId fail. code: ${err.code}, message: ${err.message}`);
    } else {
        console.info(`setDefaultCellularDataSlotId success`);
    }
});
```


## setDefaultCellularDataSlotId

```TypeScript
function setDefaultCellularDataSlotId(slotId: number): Promise<void>
```

设置默认移动数据的SIM卡，使用Promise方式作为异步方法。

**起始版本：** 7

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CellularData

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | SIM卡槽ID。   - 0：卡槽1。    - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式异步返回设置结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8301001](../errorcode-telephony.md#8301001-sim卡未激活) | SIM card is not activated. |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.setDefaultCellularDataSlotId(0).then(() => {
    console.info(`setDefaultCellularDataSlotId success.`);
}).catch((err: BusinessError) => {
    console.error(`setDefaultCellularDataSlotId fail. code: ${err.code}, message: ${err.message}`);
});
```
