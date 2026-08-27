# on（系统接口）

## 导入模块

```TypeScript
import { autoStartupManager } from '@kit.AbilityKit';
```

## on('systemAutoStartup')

```TypeScript
function on(type: 'systemAutoStartup', callback: AutoStartupCallback): void
```

注册监听应用组件开机自启动状态变化的回调函数。 从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。 对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_APP_BOOT

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'systemAutoStartup' | 是 | 固定取值“systemAutoStartup”，表示为系统应用所调用。 |
| callback | [AutoStartupCallback](arkts-ability-autostartupcallback-i-sys.md) | 是 | 监听应用组件开机自启动状态变化的回调对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, interface caller does not have permission"ohos.permission.MANAGE_APP_BOOT". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes: 1. Mandatory parameters are lef unspecified; 2. Incorrect parameters types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Failed to connect to the system service. |

**示例**

```TypeScript
import { autoStartupManager, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 注册监听应用组件开机自启动状态变化
  autoStartupManager.on('systemAutoStartup', {
    // 应用开机自启动成功回调
    onAutoStartupOn(data: common.AutoStartupInfo) {
      console.info(`autostartupmanager onAutoStartupOn, data: ${JSON.stringify(data)}.`);
    },
    // 应用取消开机自启动回调
    onAutoStartupOff(data: common.AutoStartupInfo) {
      console.info(`autostartupmanager onAutoStartupOff, data: ${JSON.stringify(data)}.`);
    }
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`autostartupmanager on failed, err code: ${code}, err msg: ${msg}.`);
}
```
