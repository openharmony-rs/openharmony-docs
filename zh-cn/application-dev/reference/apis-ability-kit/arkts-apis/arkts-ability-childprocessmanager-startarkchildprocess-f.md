# startArkChildProcess

## startArkChildProcess

```TypeScript
function startArkChildProcess(srcEntry: string, args: ChildProcessArgs, options?: ChildProcessOptions): Promise<int>
```

启动\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。使用Promise异步回调。 该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回801错误码。 > **说明：** > > 调用该接口创建的子进程不会继承父进程资源，子进程创建成功会返回子进程pid，然后执行子进程的 > [ChildProcess.onStart]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_函数。 > [ChildProcess.onStart]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_函数执行完后子进程不会自动销毁，需要子进程调用 > [process.abort]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_销毁。调用该接口的进程销毁后，所创建的子进程也会一并销毁。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-childProcessManager-function startArkChildProcess(srcEntry: string, args: ChildProcessArgs, options?: ChildProcessOptions): Promise<int>--><!--Device-childProcessManager-function startArkChildProcess(srcEntry: string, args: ChildProcessArgs, options?: ChildProcessOptions): Promise<int>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcEntry | string | 是 | 子进程源文件路径，不支持源文件放在HAR类型的模块中。由“模块名” + “/” + “文件路径”组成，文件路径以src/main为根目录。例如子进程文件在module1模块下src/main/ets/process/DemoProcess.ets，则srcEntry为"module1/ets/process/DemoProcess.ets"。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_另外，需要确保子进程源文件被其它文件引用到，防止被构建工具优化掉。（详见下方示例代码） |
| args | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 传递到子进程的参数。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 子进程的启动配置选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;int&gt; | Promise对象，返回子进程pid。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000061](../errorcode-ability.md#16000061-不支持的操作) | Operation not supported. |
| [16000062](../errorcode-ability.md#16000062-子进程数量超出上限) | The number of child processes exceeds the upper limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 13+ |

**示例：**

ArkTS-Dyn示例：

```TypeScript
// 在module1模块的src/main/ets/process下创建DemoProcess.ets子进程类:
// module1/src/main/ets/process/DemoProcess.ets
import { ChildProcess, ChildProcessArgs } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {
  onStart(args?: ChildProcessArgs): void {
    let entryParams = args?.entryParams;
    let fd = args?.fds?.key1;
    // ..
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
// 在module1模块的src/main/ets/process下创建StaticDemoProcess.ets子进程类:
// module1/src/main/ets/process/StaticDemoProcess.ets
import { ChildProcess, ChildProcessArgs } from '@kit.AbilityKit';

export default class StaticDemoProcess extends ChildProcess {
  onStart(args?: ChildProcessArgs): void {
    console.info('StaticDemoProcess OnStart() called');
  }
}
```

ArkTS-Dyn示例：

```TypeScript
// 使用childProcessManager.startArkChildProcess方法启动子进程:
// module1/src/main/ets/pages/Index.ets
import { common, ChildProcessArgs, ChildProcessOptions, childProcessManager } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
import DemoProcess from '../process/DemoProcess';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('拉起ArkTS-Dyn类型子进程')
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            try {
              DemoProcess.toString(); // 这里要调用下DemoProcess类的任意方法，防止没有引用到而被构建工具优化掉
              let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
              let path = context.filesDir + '/test.txt';
              let file = fileIo.openSync(path, fileIo.OpenMode.READ_ONLY | fileIo.OpenMode.CREATE);
              let args: ChildProcessArgs = {
                entryParams: 'testParam',
                fds: {
                  'key1': file.fd
                }
              };
              let options: ChildProcessOptions = {
                isolationMode: false
              };
              childProcessManager.startArkChildProcess('module1/ets/process/DemoProcess.ets', args, options)
                .then((pid) => {
                  console.info(`startChildProcess success, pid: ${pid}`);
                })
                .catch((err: BusinessError) => {
                  console.error(`startChildProcess business error, errorCode: ${err.code}, errorMsg:${err.message}`);
                })
            } catch (err: BusinessError) {
              console.error(`startChildProcess error, errorCode: ${err.code}, errorMsg:${err.message}`);
            }
          });

        Button('拉起ArkTS-Sta类型子进程')
        .onClick(() => {
           try {
              let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
              let path = context.filesDir + '/test.txt';
              let file = fileIo.openSync(path, fileIo.OpenMode.READ_ONLY | fileIo.OpenMode.CREATE);
              let args: ChildProcessArgs = {
                entryParams: 'testParam',
                fds: {
                  'key1': file.fd
                }
              };
              let options: ChildProcessOptions = {
                isolationMode: false
              };
              childProcessManager.startArkChildProcess('module1/src/main/ets/process/StaticDemoProcess', args, options)
                .then((pid) => {
                  console.info(`startChildProcess success, pid: ${pid}`);
                })
                .catch((err: BusinessError) => {
                  console.error(`startChildProcess business error, errorCode: ${err.code}, errorMsg:${err.message}`);
                })
            } catch (err: BusinessError) {
              console.error(`startChildProcess error, errorCode: ${err.code}, errorMsg:${err.message}`);
            }
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
// 使用childProcessManager.startArkChildProcess方法启动子进程:
// module1/src/main/ets/pages/Index.ets
import { Entry, Text, Column, Component, Button } from '@ohos.arkui.component';
import { ChildProcessArgs, ChildProcessOptions, childProcessManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import DemoProcess from '../process/DemoProcess';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('拉起ArkTS-Dyn类型子进程')
        .onClick(() => {
          try {
            let args: ChildProcessArgs = {
              entryParams: 'testParam',
            };
            let options: ChildProcessOptions = {
              isolationMode: false
            };
            childProcessManager.startArkChildProcess('module1/ets/process/DemoProcess.ets', args, options)
              .then((pid) => {
                console.info(`startChildProcess success, pid: ${pid}`);
              })
              .catch((err: BusinessError) => {
                console.error(`startChildProcess business error, errorCode: ${(err as BusinessError).code}, errorMsg:${(err as BusinessError).message}`);
              })
          } catch (err: BusinessError) {
            console.error(`startChildProcess error, errorCode: ${(err as BusinessError).code}, errorMsg:${(err as BusinessError).message}`);
          }
        });

      Button('拉起ArkTS-Sta类型子进程')
      .onClick(() => {
         try {
            let args: ChildProcessArgs = {
              entryParams: 'testParam',
            };
            let options: ChildProcessOptions = {
              isolationMode: false
            };
            childProcessManager.startArkChildProcess('module1/src/main/ets/process/StaticDemoProcess', args, options)
              .then((pid) => {
                console.info(`startChildProcess success, pid: ${pid}`);
              })
              .catch((err: BusinessError) => {
                console.error(`startChildProcess business error, errorCode: ${(err as BusinessError).code}, errorMsg:${(err as BusinessError).message}`);
              })
          } catch (err: BusinessError) {
            console.error(`startChildProcess error, errorCode: ${(err as BusinessError).code}, errorMsg:${(err as BusinessError).message}`);
          }
      })
    }
    .width('100%')
  }
}
```

