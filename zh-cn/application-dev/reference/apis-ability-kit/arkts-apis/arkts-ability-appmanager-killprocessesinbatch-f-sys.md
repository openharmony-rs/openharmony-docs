# killProcessesInBatch（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## killProcessesInBatch

```TypeScript
function killProcessesInBatch(pids: Array<number>): Promise<void>
```

批量终止进程。使用Promise异步回调。该接口在PC/2in1中可正常调用，在其他设备类型中返回801错误码。**需要权限**：ohos.permission.KILL_APP_PROCESSES

**起始版本：** 14

**需要权限：** ohos.permission.KILL_APP_PROCESSES

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pids | Array&lt;number&gt; | 是 | 要终止的进程ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not system application. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let pids: Array<number> = [100, 101, 102];
  appManager.killProcessesInBatch(pids).then(() => {
    console.info(`killProcessesInBatch success`);
  }).catch((err: BusinessError) => {
    console.error(`killProcessesInBatch fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] killProcessesInBatch error: ${code}, ${message}`);
}
```
