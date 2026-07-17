# setUserOperation（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## setUserOperation

```TypeScript
function setUserOperation(operation: Operation, mac: string, params: string): void
```

Sets a user operation.

**起始版本：** 20

**需要权限：** ohos.permission.CONNECT_MECHANIC_HARDWARE

<!--Device-mechanicManager-function setUserOperation(operation: Operation, mac: string, params: string): void--><!--Device-mechanicManager-function setUserOperation(operation: Operation, mac: string, params: string): void-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| operation | [Operation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-ssap-operation-e.md) | 是 | Operation type. |
| mac | string | 是 | MAC address. |
| params | string | 是 | Operation parameters. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |

**示例：**

```TypeScript
console.info('User operate');
mechanicManager.setUserOperation(mechanicManager.Operation.CONNECT, "58:51:9e:e7:79:6d", "operatingParams");
console.info('User operation was successful');

```

