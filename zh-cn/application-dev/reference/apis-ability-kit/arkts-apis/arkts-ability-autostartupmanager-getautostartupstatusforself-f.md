# getAutoStartupStatusForSelf

## 导入模块

```TypeScript
import { autoStartupManager } from '@kit.AbilityKit';
```

<a id="getautostartupstatusforself"></a>
## getAutoStartupStatusForSelf

```TypeScript
function getAutoStartupStatusForSelf(): Promise<boolean>
```

获取当前应用的开机自启动状态。使用Promise异步回调。该接口仅在Phone、PC/2in1、Tablet和Wearable设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-autoStartupManager-function getAutoStartupStatusForSelf(): Promise<boolean>--><!--Device-autoStartupManager-function getAutoStartupStatusForSelf(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前应用已被用户设置为开机自启动，false表示当前应用未被用户设置为开机自启动。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Connect to system service failed;2.System service failed to communicate with dependency module. |

**示例：**

```TypeScript
import { autoStartupManager, UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
      // 获取当前应用的开机自启动状态
      autoStartupManager.getAutoStartupStatusForSelf().then((isAutoStartup: boolean) => {
        console.info(`getAutoStartupStatusForSelf success, isAutoStartup: ${JSON.stringify(isAutoStartup)}.`);
      }).catch((err: BusinessError) => {
        console.error(`getAutoStartupStatusForSelf failed, err code: ${err.code}, err msg: ${err.message}.`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let msg = (err as BusinessError).message;
      console.error(`getAutoStartupStatusForSelf failed, err code: ${code}, err msg: ${msg}.`);
    }
  }
}

```

