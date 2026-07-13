# startChildProcess

## startChildProcess

```TypeScript
function startChildProcess(srcEntry: string, startMode: StartMode): Promise<number>
```

启动[ArkTS子进程](../../../../application-models/ability-terminology.md#arkts子进程)。使用Promise异步回调。
该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回16000061错误码。

> **说明：**
>
> 调用该接口创建子进程成功会返回子进程pid，然后执行子进程的[ChildProcess.onStart](arkts-ability-childprocess-c.md#onstart-1)函数
> ，[ChildProcess.onStart](arkts-ability-childprocess-c.md#onstart-1)函数执行完后子进程会自动销毁。
>
> 调用该接口创建的子进程不支持异步ArkTS API调用，仅支持同步ArkTS API调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcEntry | string | 是 | 子进程源文件路径，只支持源文件放在entry类型的模块中，以src/main为根目录。例如子进程文件在entry模块下src/main/ets/process/DemoProcess.ets，则srcEntry为"./ets/process/DemoProcess.ets"。<br/>另外，需要确保子进程源文件被其它文件引用到，防止被构建工具优化掉。（详见下方示例代码） |
| startMode | StartMode | 是 | 子进程启动模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回子进程pid。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000061](../errorcode-ability.md#16000061-不支持的操作) | Operation not supported. |
| [16000062](../errorcode-ability.md#16000062-子进程数量超出上限) | The number of child processes exceeds the upper limit. |

**示例：**

```TypeScript
// 在entry模块的src/main/ets/process下创建DemoProcess.ets子进程类:
// entry/src/main/ets/process/DemoProcess.ets
import { ChildProcess } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {
  onStart() {
    console.info('DemoProcess OnStart() called');
  }
}

```

```TypeScript
// 使用childProcessManager.startChildProcess方法启动子进程:
// entry/src/main/ets/tool/Tool.ets
import { childProcessManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import DemoProcess from '../process/DemoProcess';

try {
  DemoProcess.toString(); // 这里要调用下DemoProcess类的任意方法，防止没有引用到而被构建工具优化掉
  childProcessManager.startChildProcess("./ets/process/DemoProcess.ets", childProcessManager.StartMode.SELF_FORK)
    .then((data) => {
      console.info(`startChildProcess success, pid: ${data}`);
    }, (err: BusinessError) => {
      console.error(`startChildProcess error, errorCode: ${err.code}`);
    })
} catch (err) {
  console.error(`startChildProcess error, errorCode: ${(err as BusinessError).code}, errorMsg: ${(err as BusinessError).message}.`);
}

```


## startChildProcess

```TypeScript
function startChildProcess(srcEntry: string, startMode: StartMode, callback: AsyncCallback<number>): void
```

启动[ArkTS子进程](../../../../application-models/ability-terminology.md#arkts子进程)。使用callback异步回调。
该接口在Tablet、PC/2in1中可正常调用，在其他设备类型中返回16000061错误码。

> **说明：**
>
> 调用该接口创建子进程成功会返回子进程pid，然后执行子进程的[ChildProcess.onStart](arkts-ability-childprocess-c.md#onstart-1)函数
> ，[ChildProcess.onStart](arkts-ability-childprocess-c.md#onstart-1)函数执行完后子进程会自动销毁。
>
> 调用该接口创建的子进程不支持异步ArkTS API调用，仅支持同步ArkTS API调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcEntry | string | 是 | 子进程源文件路径，只支持源文件放在entry类型的模块中，以src/main为根目录。例如子进程文件在entry模块下src/main/ets/process/DemoProcess.ets，则srcEntry为"./ets/process/DemoProcess.ets"。<br/>另外，需要确保子进程源文件被其它文件引用到，防止被构建工具优化掉。（详见下方示例代码） |
| startMode | StartMode | 是 | 子进程启动模式。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 回调函数。当子进程启动成功，err为undefined，data为获取到的子进程pid；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000061](../errorcode-ability.md#16000061-不支持的操作) | Operation not supported. |
| [16000062](../errorcode-ability.md#16000062-子进程数量超出上限) | The number of child processes exceeds the upper limit. |

**示例：**

```TypeScript
// 在entry模块的src/main/ets/process下创建DemoProcess.ets子进程类:
// entry/src/main/ets/process/DemoProcess.ets
import { ChildProcess } from '@kit.AbilityKit';

export default class DemoProcess extends ChildProcess {
  onStart() {
    console.info('DemoProcess OnStart() called');
  }
}

```

```TypeScript
// 使用childProcessManager.startChildProcess方法启动子进程:
// entry/src/main/ets/tool/Tool.ets
import { childProcessManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import DemoProcess from '../process/DemoProcess';

try {
  DemoProcess.toString(); // 这里要调用下DemoProcess类的任意方法，防止没有引用到而被构建工具优化掉
  childProcessManager.startChildProcess("./ets/process/DemoProcess.ets", childProcessManager.StartMode.SELF_FORK, (err, data) => {
    if (data) {
      console.info(`startChildProcess success, pid: ${data}`);
    } else {
      console.error(`startChildProcess error, errorCode: ${err.code}`);
    }
  });
} catch (err) {
  console.error(`startChildProcess error, errorCode: ${(err as BusinessError).code}, errorMsg: ${(err as BusinessError).message}.`);
}

```

