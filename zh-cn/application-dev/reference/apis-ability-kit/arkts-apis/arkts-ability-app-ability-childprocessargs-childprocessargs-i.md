# ChildProcessArgs

传递到子进程的参数。[childProcessManager](arkts-app-ability-childprocessmanager.md)启动子进程时，可以通过ChildProcessArgs传递参数到子进程中。

**起始版本：** 12

<!--Device-unnamed-export interface ChildProcessArgs--><!--Device-unnamed-export interface ChildProcessArgs-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { ChildProcessArgs } from '@kit.AbilityKit';
```

## entryParams

```TypeScript
entryParams?: string
```

开发者自定义参数，透传到子进程中。可以在[ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart-1)方法中通过args.entryParams获取，entryParams支持传输的最大数据量为150KB。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChildProcessArgs-entryParams?: string--><!--Device-ChildProcessArgs-entryParams?: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## fds

```TypeScript
fds?: Record<string, number>
```

文件描述符句柄集合，用于主进程和子进程通信，通过key-value的形式传入到子进程中，其中key为自定义字符串，value为文件描述符句柄。可以在[ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart-1)方法中通过args.fds获取fd句柄。

<b>说明：</b>

- fds最多支持16组，每组key的最大长度为20字符。  
- 传递到子进程中句柄数字可能会变，但是指向的文件是一致的。

**类型：** Record<string, number>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChildProcessArgs-fds?: Record<string, int>--><!--Device-ChildProcessArgs-fds?: Record<string, int>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

