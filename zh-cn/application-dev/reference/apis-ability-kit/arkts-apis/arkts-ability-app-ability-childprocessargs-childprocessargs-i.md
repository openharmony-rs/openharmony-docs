# ChildProcessArgs

传递到子进程的参数。[childProcessManager](arkts-app-ability-childprocessmanager.md)启动子进程时，可以通过 ChildProcessArgs传递参数到子进程中。

**起始版本：** 12

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { ChildProcessArgs } from '@kit.AbilityKit';
```

## entryParams

```TypeScript
entryParams?: string
```

开发者自定义参数，透传到子进程中。可以在[ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart)方法中通过 args.entryParams获取，不传入时子进程无法获取开发者自定义参数。entryParams通过IPC传输，IPC传输的数据量最大为200KB，其中部分由系统占用， 建议entryParams传入数据量不超过150KB，否则可能导致创建子进程失败。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## fds

```TypeScript
fds?: Record<string, number>
```

文件描述符句柄集合，用于主进程和子进程通信，不传入时子进程无法获取主进程传递的文件句柄。 该参数通过key-value的形式传入到子进程中，其中key为自定义字符串，value为文件描述符句柄。可以在 [ChildProcess.onStart](arkts-ability-app-ability-childprocess-childprocess-c.md#onstart)方法中通过args.fds获取fd句柄。&lt;b&gt;说明：&lt;/b&gt;  
- fds最多支持16组，每组key的最大长度为20字符。  
- 传递到子进程中的句柄数字可能会变，但是指向的文件是一致的。

**类型：** Record&lt;string, number&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例**

示例中的context的获取方式请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
// 主进程中:
import { common, ChildProcessArgs, childProcessManager } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';

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
            let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
            let path = context.filesDir + '/test.txt';
            let file = fileIo.openSync(path, fileIo.OpenMode.READ_ONLY | fileIo.OpenMode.CREATE);
            let args: ChildProcessArgs = {
              entryParams: 'testParam',
              fds: {
                'key1': file.fd
              }
            };
            childProcessManager.startArkChildProcess('entry/./ets/process/DemoProcess.ets', args);
          });
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

```TypeScript
// 子进程中:
import { ChildProcess, ChildProcessArgs } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {

  onStart(args?: ChildProcessArgs) {
    let entryParams = args?.entryParams;
    let fd = args?.fds?.key1;
    // ...
  }
}
```
