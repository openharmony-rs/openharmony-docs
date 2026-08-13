# getProcessMemoryByPid（系统接口）

## getProcessMemoryByPid

```TypeScript
function getProcessMemoryByPid(pid: int): Promise<int>
```

通过pid查询对应进程占用的内存大小。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-appManager-function getProcessMemoryByPid(pid: int): Promise<int>--><!--Device-appManager-function getProcessMemoryByPid(pid: int): Promise<int>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pid | int | 是 | 表示进程id，详情参考 [getRunningProcessInfoByBundleName](arkts-ability-appmanager-getrunningprocessinfobybundlename-f-sys.md#getRunningProcessInfoByBundleName（系统接口）) 。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 以Promise方式返回接口运行结果及进程占用的内存大小（单位KB），可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let pid = 0;

try {
  appManager.getProcessMemoryByPid(pid).then((data) => {
    console.info('getProcessMemoryByPid success.');
  }).catch((e: Error) => {
    let err = e as BusinessError;
    console.error(`getProcessMemoryByPid fail, err: ${err.code},  ${err.message}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```


## getProcessMemoryByPid

```TypeScript
function getProcessMemoryByPid(pid: int, callback: AsyncCallback<int>): void
```

通过pid查询对应进程占用的内存大小。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-appManager-function getProcessMemoryByPid(pid: int, callback: AsyncCallback<int>): void--><!--Device-appManager-function getProcessMemoryByPid(pid: int, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pid | int | 是 | 表示进程id，详情参考 [getRunningProcessInfoByBundleName](arkts-ability-appmanager-getrunningprocessinfobybundlename-f-sys.md#getRunningProcessInfoByBundleName（系统接口）) 。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 以回调方式返回接口运行结果及进程占用的内存大小（单位KB），可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let pid = 0;
function getProcessMemoryByPidCallback(err: BusinessError, data: number) {
  if (err) {
    console.error(`getProcessMemoryByPidCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('getProcessMemoryByPidCallback success.');
  }
}

try {
  appManager.getProcessMemoryByPid(pid, getProcessMemoryByPidCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let pid: int = 0;

function getProcessMemoryByPidCallback(err: BusinessError | null, data: int | undefined) {
  if (err) {
    console.error(`getProcessMemoryByPidCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('getProcessMemoryByPidCallback success.');
  }
}

try {
  appManager.getProcessMemoryByPid(pid, getProcessMemoryByPidCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

