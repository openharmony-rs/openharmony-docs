# startNativeChildProcess

## 导入模块

```TypeScript
import { childProcessManager } from '@kit.AbilityKit';
```

## startNativeChildProcess

```TypeScript
function startNativeChildProcess(entryPoint: string, args: ChildProcessArgs, options?: ChildProcessOptions): Promise<number>
```

启动[Native子进程](../../../../application-models/ability-terminology.md#native子进程)。使用Promise异步回调。该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回801错误码。

> **说明：**  
>  
> 调用该接口创建的子进程不会继承父进程资源，子进程创建成功会返回子进程pid，然后加载参数中指定的动态链接库文件并执行子进程的入口函数，入口函数执行完后子进程会自动销毁。调用该接口的进程销毁后，所创建的子进程也会一并销毁。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-childProcessManager-function startNativeChildProcess(entryPoint: string, args: ChildProcessArgs, options?: ChildProcessOptions): Promise<int>--><!--Device-childProcessManager-function startNativeChildProcess(entryPoint: string, args: ChildProcessArgs, options?: ChildProcessOptions): Promise<int>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entryPoint | string | 是 | 子进程中调用动态库的符号和入口函数，中间用“:”隔开（例如“libentry.so:Main”)。 |
| args | [ChildProcessArgs](arkts-ability-app-ability-childprocessargs-childprocessargs-i.md) | 是 | 传递到子进程的参数。 |
| options | [ChildProcessOptions](arkts-ability-app-ability-childprocessoptions-childprocessoptions-i.md) | 否 | 子进程的启动配置选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回子进程pid。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000061](../errorcode-ability.md#16000061-不支持的操作) | Operation not supported. |
| [16000062](../errorcode-ability.md#16000062-子进程数量超出上限) | The number of child processes exceeds the upper limit. |

**示例：**

子进程部分，详见[Native子进程开发指导（C/C++）- 创建支持参数传递的Native子进程](../../application-models/capi-nativechildprocess-development-guideline.md#创建支持参数传递的native子进程)：

```TypeScript
#include <AbilityKit/native_child_process.h>

extern "C" {

/**
 * 子进程的入口函数，实现子进程的业务逻辑
 * 函数名称可以自定义，在主进程调用OH_Ability_StartNativeChildProcess方法时指定，此示例中为Main
 * 函数返回后子进程退出
 */
void Main(NativeChildProcess_Args args)
{
    // 获取传入的entryPrams
    char *entryParams = args.entryParams;
    // 获取传入的fd列表，对应ChildProcessArgs中的args.fds
    NativeChildProcess_Fd *current = args.fdList.head;
    while (current != nullptr) {
        char *fdName = current->fdName;
        int32_t fd = current->fd;
        current = current->next;
        // 业务逻辑..
    }
}
} // extern "C"

```

主进程部分，示例中的context的获取方式请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)：

```TypeScript
// 主进程：
// 使用childProcessManager.startNativeChildProcess方法启动子进程:
import { common, ChildProcessArgs, ChildProcessOptions, childProcessManager } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
              let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
              let path = context.filesDir + "/test.txt";
              let file = fileIo.openSync(path, fileIo.OpenMode.READ_ONLY | fileIo.OpenMode.CREATE);
              let args: ChildProcessArgs = {
                entryParams: "testParam",
                fds: {
                  "key1": file.fd
                }
              };
              let options: ChildProcessOptions = {
                isolationMode: false
              };
              childProcessManager.startNativeChildProcess("libentry.so:Main", args, options)
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
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

