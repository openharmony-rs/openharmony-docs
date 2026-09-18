# isManualNetworkScanning（系统接口）

## 导入模块

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## isManualNetworkScanning

```TypeScript
function isManualNetworkScanning(slotId: number): Promise<boolean>
```

确定当前手动网络扫描是否正在进行

**起始版本：** 23

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 承诺返回 ManualNetworkScanState。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Nonsystem applications use system APIs. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
radio.isManualNetworkScanning(0).then((state: boolean) => {
    console.info(`isManualNetworkScanning success, state->${JSON.stringify(state)}`);
}).catch((err: BusinessError) => {
    console.error(`isManualNetworkScanning failed, promise: err->${JSON.stringify(err)}`);
});
```
