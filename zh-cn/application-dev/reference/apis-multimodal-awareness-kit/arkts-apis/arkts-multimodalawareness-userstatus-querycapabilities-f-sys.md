# queryCapabilities（系统接口）

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## queryCapabilities

```TypeScript
function queryCapabilities(capabilities: UserStatusAtomicCap[]): UserStatusAtomicCap[]
```

查询设备支持的原子化服务能力。该方法通过底层接口判断是否支持指定的原子化服务能力，返回设备实际支持的能力列表。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capabilities | [UserStatusAtomicCap](arkts-multimodalawareness-userstatus-userstatusatomiccap-e-sys.md)[] | 是 | 表示要查询的原子化服务能力列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UserStatusAtomicCap](arkts-multimodalawareness-userstatus-userstatusatomiccap-e-sys.md)[] | 返回设备支持的原子化服务能力列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [33900001](../errorcode-userStatus.md#33900001-服务异常) | Service exception. Possible causes:  1. System error, such as a null pointer and container-related exception.  2. Node-API invocation exception, such as invalid Node-API status. |
