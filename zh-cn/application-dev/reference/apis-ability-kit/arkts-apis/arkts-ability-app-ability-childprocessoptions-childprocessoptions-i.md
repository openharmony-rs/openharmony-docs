# ChildProcessOptions

子进程的启动配置选项。通过[childProcessManager](arkts-app-ability-childprocessmanager.md)启动子进程时，可以通过 ChildProcessOptions配置子进程启动选项。

**起始版本：** 12

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

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## isolationUid

```TypeScript
isolationUid?: boolean
```

控制子进程是否使用独立的uid。true表示子进程运行拥有独立的uid；false表示子进程与主进程拥有相同uid。默认为false。仅在isolationMode为true时生效。

**类型：** boolean

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

子进程部分：

```TypeScript
// 在entry模块的src/main/ets/process下创建DemoProcess.ets子进程类:
// entry/src/main/ets/process/DemoProcess.ets
import { ChildProcess, ChildProcessArgs } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {
  onStart(args?: ChildProcessArgs) {
    let entryParams = args?.entryParams;
    let fd = args?.fds?.key1;
    // 子进程代码逻辑
  }
}
```

主进程部分：

```TypeScript
// 使用childProcessManager.startArkChildProcess方法启动子进程:
// entry/src/main/ets/pages/Index.ets
import { ChildProcessArgs, ChildProcessOptions, childProcessManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import DemoProcess from '../process/DemoProcess';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('Click')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            try {
              DemoProcess.toString(); // 这里调用DemoProcess类的任意方法，防止没有引用到而被构建工具优化掉
              let options: ChildProcessOptions = {
                isolationMode: true,
                isolationUid: false
              };
              let args: ChildProcessArgs = {
                entryParams: 'testParam',
              };
              childProcessManager.startArkChildProcess("entry/ets/process/DemoProcess.ets", args, options)
                .then((pid) => {
                  console.info(`startChildProcess success, pid: ${pid}`);
                })
                .catch((err: BusinessError) => {
                  console.error(`startChildProcess business error, errorCode: ${err.code}, errorMsg:${err.message}`);
                });
            } catch (err) {
              console.error(`startChildProcess error, errorCode: ${err.code}, errorMsg:${err.message}`);
            }
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
