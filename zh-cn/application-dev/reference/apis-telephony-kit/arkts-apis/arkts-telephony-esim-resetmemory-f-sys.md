# resetMemory（系统接口）

## 导入模块

```TypeScript
```

## resetMemory

```TypeScript
function resetMemory(slotId: number, options?:ResetOption): Promise<ResultCode>
```

清除所有特定配置文件并重置eUICC。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.SET_TELEPHONY_ESIM_STATE

**系统能力：** SystemCapability.Telephony.CoreService.Esim

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| options | [ResetOption](arkts-telephony-esim-resetoption-e-sys.md) | 否 | 重置状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;ResultCode & gt; | Promise对象，返回重置的结果码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3120001](../errorcode-telephony.md#3120001-服务连接失败) | Service connection failed. |
| [3120002](../errorcode-telephony.md#3120002-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.resetMemory(1).then(() => {
    console.info(`resetMemory invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`resetMemory, ErrorState: err->${JSON.stringify(err)}`);
});
```
