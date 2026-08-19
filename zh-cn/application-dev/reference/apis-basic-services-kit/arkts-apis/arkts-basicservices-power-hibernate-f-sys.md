# hibernate（系统接口）

## 导入模块

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## hibernate

```TypeScript
function hibernate(clearMemory: boolean): void
```

休眠设备。<br><br>与suspend方法的区别：hibernate为更深的休眠状态（休眠前可选择清理内存），suspend为较浅的低功耗睡眠状态（灭屏后进入睡眠）。 需最大程度节省电量时选择hibernate，需快速恢复设备活动时选择suspend。适用于设备长时间闲置需要深度节能的场景。

**起始版本：** 23

**需要权限：** 
- API版本19+：ohos.permission.POWER_MANAGER

<!--Device-power-function hibernate(clearMemory: boolean): void--><!--Device-power-function hibernate(clearMemory: boolean): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clearMemory | boolean | 是 | 是否在进入休眠之前清理内存。true表示清理内存，false表示不清理内存。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 19+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |

**示例**

```TypeScript
try {
    power.hibernate(true);
} catch(err) {
    console.error('hibernate failed, err: ' + err);
}
```

