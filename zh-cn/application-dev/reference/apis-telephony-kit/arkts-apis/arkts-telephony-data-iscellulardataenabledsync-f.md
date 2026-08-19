# isCellularDataEnabledSync

## 导入模块

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## isCellularDataEnabledSync

```TypeScript
function isCellularDataEnabledSync(): boolean
```

检查蜂窝数据业务是否启用，调用此API返回结果。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-data-function isCellularDataEnabledSync(): boolean--><!--Device-data-function isCellularDataEnabledSync(): boolean-End-->

**系统能力：** SystemCapability.Telephony.CellularData

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 用来返回检查蜂窝数据业务是否启用。&lt;br /&gt;true：蜂窝数据业务已启用。&lt;br /&gt;false：蜂窝数据业务已禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { data } from '@kit.TelephonyKit';

try {
    let isEnabled: boolean = data.isCellularDataEnabledSync();
    console.info(`isCellularDataEnabledSync success : ${isEnabled}`);
} catch (err) {
    console.error(`isCellularDataEnabledSync fail. code: ${err.code}, message: ${err.message}`);  
}
```

