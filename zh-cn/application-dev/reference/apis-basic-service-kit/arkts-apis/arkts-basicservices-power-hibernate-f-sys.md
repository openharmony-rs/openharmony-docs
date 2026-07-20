# hibernate（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

<a id="hibernate"></a>
## hibernate

```TypeScript
function hibernate(clearMemory: boolean): void
```

休眠设备。

**起始版本：** 12

**需要权限：** 
- API版本19+：ohos.permission.POWER_MANAGER

<!--Device-power-function hibernate(clearMemory: boolean): void--><!--Device-power-function hibernate(clearMemory: boolean): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clearMemory | boolean | 是 | true 代表在进入休眠之前清理内存，否则为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4900101](../../apis-basic-services-kit/errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 19+ |

**示例：**

```TypeScript
try {
    power.hibernate(true);
} catch (err) {
    console.error(`Failed to hibernate device. Code: ${err.code}, message: ${err.message}`);
}

```

