# isAutoStartupSupported

## 导入模块

```TypeScript
import { autoStartupManager } from '@kit.AbilityKit';
```

## isAutoStartupSupported

```TypeScript
function isAutoStartupSupported(): boolean
```

检查当前设备是否支持开机自启动。
> **说明：**  
>  
> 建议在调用[autoStartupManager.getAutoStartupStatusForSelf](arkts-ability-autostartupmanager-getautostartupstatusforself-f.md#getautostartupstatusforself) 之前，先调  
> 用该接口检查设备能力。如果返回false，则表明当前设备不支持开机自启动。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-autoStartupManager-function isAutoStartupSupported(): boolean--><!--Device-autoStartupManager-function isAutoStartupSupported(): boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当前设备是否支持开机自启动。true：支持，false：不支持。 |

**示例：**

```TypeScript
import { autoStartupManager, UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    // 检查当前设备是否支持开机自启动
    const isSupported: boolean = autoStartupManager.isAutoStartupSupported();
    console.info(`isAutoStartupSupported: ${isSupported}.`);
  }
}

```

