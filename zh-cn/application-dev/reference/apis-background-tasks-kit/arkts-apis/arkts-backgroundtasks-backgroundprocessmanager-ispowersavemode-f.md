# isPowerSaveMode

## 导入模块

```TypeScript
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
```

## isPowerSaveMode

```TypeScript
function isPowerSaveMode(pid: int): Promise<boolean>
```

查询进程是否处于能效模式，使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.BACKGROUND_MANAGER_POWER_SAVE_MODE

<!--Device-backgroundProcessManager-function isPowerSaveMode(pid: int): Promise<boolean>--><!--Device-backgroundProcessManager-function isPowerSaveMode(pid: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pid | int | 是 | 进程号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回进程PID是否处于能效模式，返回true表示进程处于能效模式，返回false表示进程未处于能效模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [31800002](../../apis-backgroundtasks-kit/errorcode-backgroundProcessManager.md#31800002-参数错误) | Parameter error. Possible causes: <br> 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';

let pid = 33333;  // 请开发者替换为实际的进程号
try {
  backgroundProcessManager.isPowerSaveMode(pid).then((result: boolean) => {
    console.info(`isPowerSaveMode: ${result}`);
  }).catch((err: BusinessError) => {
    console.error(`isPowerSaveMode failed, promise errCode: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  console.error(`isPowerSaveMode failed, errCode: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

