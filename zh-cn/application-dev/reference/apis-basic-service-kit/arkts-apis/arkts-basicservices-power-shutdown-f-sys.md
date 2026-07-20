# shutdown（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

<a id="shutdown"></a>
## shutdown

```TypeScript
function shutdown(reason: string): void
```

系统关机。

**起始版本：** 7

**需要权限：** ohos.permission.REBOOT

<!--Device-power-function shutdown(reason: string): void--><!--Device-power-function shutdown(reason: string): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 关机原因；该参数必须为字符串类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [4900101](../../apis-basic-services-kit/errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
try {
    power.shutdown('shutdown_test');
} catch (err) {
    console.error(`Failed to shutdown. Code: ${err.code}, message: ${err.message}`);
}

```

