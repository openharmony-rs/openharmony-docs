# @ohos.app.ability.hyperSnapManager(应用快启管理)

应用启动过程中的初始化流程可以提前进行快启初始化，快启启动的应用不再重复执行初始化流程，从而起到加速启动的作用。hyperSnapManager模块提供应用快启管理的能力，包括启用或禁用应用的快启功能、请求重新初始化应用快启等。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace hyperSnapManager--><!--Device-unnamed-declare namespace hyperSnapManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [requestRebuildHyperSnap(应用快启管理)](arkts-ability-hypersnapmanager-requestrebuildhypersnap-f.md) | 请求重新初始化应用快启。 此方法会销毁当前进程已经初始化的快启数据，系统将在合适的时机重新进行快启初始化。 |
| [setHyperSnapEnabled(应用快启管理)](arkts-ability-hypersnapmanager-sethypersnapenabled-f.md) | 启用或禁用应用的快启功能。 |

