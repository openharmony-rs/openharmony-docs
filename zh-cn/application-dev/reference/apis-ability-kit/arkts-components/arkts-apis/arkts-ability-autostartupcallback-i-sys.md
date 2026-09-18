# AutoStartupCallback（系统接口）

应用设置为开机自启动时的回调函数。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onAutoStartupOff

```TypeScript
onAutoStartupOff(info: AutoStartupInfo): void
```

取消应用开机自启动时调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [AutoStartupInfo](arkts-ability-autostartupinfo-i-sys.md) | 是 | 取消开机自启动的应用组件信息。 |

**示例**

```TypeScript
import { autoStartupManager, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 定义开机自启动回调对象
let autoStartupCallback: common.AutoStartupCallback = {
  onAutoStartupOn(info: common.AutoStartupInfo) {
    console.info(`autostartupmanager onAutoStartupOn, info: ${JSON.stringify(info)}.`);
  },
  onAutoStartupOff(info: common.AutoStartupInfo) {
    console.info(`autostartupmanager onAutoStartupOff, info: ${JSON.stringify(info)}.`);
  }
};

// 订阅系统开机自启动事件
try {
  autoStartupManager.on('systemAutoStartup', autoStartupCallback);
} catch (err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`autoStartupManager.on failed, err code: ${code}, err msg: ${msg}.`);
}
```

## onAutoStartupOn

```TypeScript
onAutoStartupOn(info: AutoStartupInfo): void
```

应用设置为开机自启动时调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [AutoStartupInfo](arkts-ability-autostartupinfo-i-sys.md) | 是 | 设置为开机自启动的应用组件信息。 |

**示例**

```TypeScript
import { autoStartupManager, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 定义开机自启动回调对象
let autoStartupCallback: common.AutoStartupCallback = {
  onAutoStartupOn(info: common.AutoStartupInfo) {
    console.info(`autostartupmanager onAutoStartupOn, info: ${JSON.stringify(info)}.`);
  },
  onAutoStartupOff(info: common.AutoStartupInfo) {
    console.info(`autostartupmanager onAutoStartupOff, info: ${JSON.stringify(info)}.`);
  }
};

// 订阅系统开机自启动事件
try {
  autoStartupManager.on('systemAutoStartup', autoStartupCallback);
} catch (err) {
  let code = (err as BusinessError).code;
  let msg = (err as BusinessError).message;
  console.error(`autoStartupManager.on failed, err code: ${code}, err msg: ${msg}.`);
}
```
