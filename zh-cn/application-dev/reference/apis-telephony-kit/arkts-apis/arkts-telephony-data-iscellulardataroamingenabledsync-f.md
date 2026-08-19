# isCellularDataRoamingEnabledSync

## 导入模块

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## isCellularDataRoamingEnabledSync

```TypeScript
function isCellularDataRoamingEnabledSync(slotId: int): boolean
```

检查蜂窝数据业务是否启用漫游，调用此API返回结果。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-data-function isCellularDataRoamingEnabledSync(slotId: int): boolean--><!--Device-data-function isCellularDataRoamingEnabledSync(slotId: int): boolean-End-->

**系统能力：** SystemCapability.Telephony.CellularData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | 卡槽ID。&lt;br /&gt;- 0：卡槽1。&lt;br /&gt;- 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 用来返回检查蜂窝数据业务是否启用漫游。&lt;br /&gt;true：蜂窝数据业务已启用漫游。&lt;br /&gt;false：蜂窝数据业务已禁用漫游。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';

try {
    let isEnabled: boolean = data.isCellularDataRoamingEnabledSync(0);
    console.info(`isCellularDataRoamingEnabledSync success : ${isEnabled}`);
} catch (err) {
    console.error(`isCellularDataRoamingEnabledSync fail. code: ${err.code}, message: ${err.message}`);  
}
```

