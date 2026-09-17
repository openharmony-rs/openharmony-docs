# @ohos.app.ability.hyperSnapManager(应用快启管理)

应用启动过程中的初始化流程可以提前进行快启初始化，快启启动的应用不再重复执行初始化流程，从而起到加速启动的作用。hyperSnapManager模块提供应用快启管理的能力，包括启用或禁用应用的快启功能、请求重新初始化应用快启等。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getLastError](arkts-ability-hypersnapmanager-getlasterror-f.md) | 获取指定场景下当前应用的最后一次Hyper Snap错误信息。每个场景的错误信息独立存储，并在请求成功后清除。设备重启后，所有错误信息都会被清除。 |
| [requestRebuildHyperSnap](arkts-ability-hypersnapmanager-requestrebuildhypersnap-f.md) | 请求重新初始化应用快启。 |
| [setHyperSnapEnabled](arkts-ability-hypersnapmanager-sethypersnapenabled-f.md) | 启用或禁用应用的快启功能。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [HyperSnapErrorInfo](arkts-ability-hypersnapmanager-hypersnaperrorinfo-i.md) | 描述Hyper Snap的错误信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HyperSnapErrorCode](arkts-ability-hypersnapmanager-hypersnaperrorcode-e.md) | 枚举Hyper Snap错误码。 |
| [HyperSnapErrorType](arkts-ability-hypersnapmanager-hypersnaperrortype-e.md) | 枚举Hyper Snap错误类型。 |
