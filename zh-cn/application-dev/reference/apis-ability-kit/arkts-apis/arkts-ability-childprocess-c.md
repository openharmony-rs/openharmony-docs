# ChildProcess

开发者自定义子进程的基类。通过[childProcessManager](arkts-app-ability-childprocessmanager.md)启动子进程时，需要继承此类并重写
入口方法。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onStart

```TypeScript
onStart(args?: ChildProcessArgs): void
```

子进程的入口方法，通过[childProcessManager](arkts-app-ability-childprocessmanager.md)启动子进程后调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| args | ChildProcessArgs | 否 | 传递到子进程的参数。 |

**示例：**

```TypeScript
import { ChildProcess, ChildProcessArgs } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {

  onStart(args?: ChildProcessArgs) {
    let entryParams = args?.entryParams;
    let fd = args?.fds?.key1;
    // ..
  }
}

```

