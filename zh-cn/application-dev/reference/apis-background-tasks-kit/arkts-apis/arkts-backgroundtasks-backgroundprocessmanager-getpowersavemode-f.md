# getPowerSaveMode

## 导入模块

```TypeScript
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
```

<a id="getpowersavemode"></a>
## getPowerSaveMode

```TypeScript
function getPowerSaveMode(pid: number): Promise<PowerSaveMode>
```

获取进程能效模式。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.BACKGROUND_MANAGER_POWER_SAVE_MODE

<!--Device-backgroundProcessManager-function getPowerSaveMode(pid: int): Promise<PowerSaveMode>--><!--Device-backgroundProcessManager-function getPowerSaveMode(pid: int): Promise<PowerSaveMode>-End-->

**系统能力：** SystemCapability.Resourceschedule.BackgroundProcessManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pid | number | 是 | 进程号。<br>取值范围：大于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PowerSaveMode&gt; | Promise对象。返回进程能效模式状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [31800002](../../apis-backgroundtasks-kit/errorcode-backgroundProcessManager.md#31800002-参数错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
// 请开发者替换为实际的进程号
let pid = 33333;
try {
    backgroundProcessManager.getPowerSaveMode(pid).then((result: backgroundProcessManager.PowerSaveMode) => {
        console.info("getPowerSaveMode: " + result.toString());
    });
} catch (error) {
    console.error(`getPowerSaveMode failed, errCode: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}

```

