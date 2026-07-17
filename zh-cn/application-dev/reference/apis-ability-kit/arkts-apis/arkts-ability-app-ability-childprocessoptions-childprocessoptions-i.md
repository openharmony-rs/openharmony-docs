# ChildProcessOptions

子进程的启动配置选项。通过[childProcessManager](arkts-app-ability-childprocessmanager.md)启动子进程时，可以通过ChildProcessOptions配置子进程启动选项。

**起始版本：** 12

<!--Device-unnamed-export interface ChildProcessOptions--><!--Device-unnamed-export interface ChildProcessOptions-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { ChildProcessOptions } from '@kit.AbilityKit';
```

## isolationMode

```TypeScript
isolationMode?: boolean
```

控制子进程的沙箱隔离级别及网络访问权限。true表示子进程运行在独立沙箱环境中，且无法访问网络；false表示子进程与主进程共享沙箱和网络环境。默认为false。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChildProcessOptions-isolationMode?: boolean--><!--Device-ChildProcessOptions-isolationMode?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## isolationUid

```TypeScript
isolationUid?: boolean
```

控制子进程是否使用独立的uid。true表示子进程运行拥有独立的uid；false表示子进程与主进程拥有相同uid。默认为false。仅在isolationMode为true时生效。

**类型：** boolean

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChildProcessOptions-isolationUid?: boolean--><!--Device-ChildProcessOptions-isolationUid?: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

