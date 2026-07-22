# createAtManager

## 导入模块

```TypeScript
import { Context, Permissions, PermissionRequestResult } from '@kit.AbilityKit';
```

## createAtManager

```TypeScript
function createAtManager(): AtManager
```

创建程序访问控制管理实例，用于权限校验、运行时权限申请、设置页授权引导和权限状态变化监听等场景。调用成功后返回AtManager实例，可用于后续的权限管理操作。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-abilityAccessCtrl-function createAtManager(): AtManager--><!--Device-abilityAccessCtrl-function createAtManager(): AtManager-End-->

**系统能力：** SystemCapability.Security.AccessToken

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AtManager](arkts-ability-abilityaccessctrl-atmanager-i.md) | 获取程序访问控制模块的实例。 |

**示例：**

```TypeScript
// 创建权限管理实例
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();

```

