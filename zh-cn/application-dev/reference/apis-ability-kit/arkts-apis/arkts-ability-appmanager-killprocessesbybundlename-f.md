# killProcessesByBundleName

## killProcessesByBundleName

```TypeScript
function killProcessesByBundleName(bundleName: string, clearPageStack: boolean, appIndex?: int): Promise<void>
```

终止指定应用包名的应用进程。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.KILL_APP_PROCESSES or ohos.permission.CLEAN_BACKGROUND_PROCESSES

<!--Device-appManager-function killProcessesByBundleName(bundleName: string, clearPageStack: boolean, appIndex?: int): Promise<void>--><!--Device-appManager-function killProcessesByBundleName(bundleName: string, clearPageStack: boolean, appIndex?: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示需要终止进程的应用包名。 |
| clearPageStack | boolean | 是 | 表示是否清除页面堆栈。true表示清除，false表示不清除。 |
| appIndex | int | 否 | 应用分身Id，默认值为0。取值为0时，表示终止主应用的所有进程。取值大于0时，表示终止指定分身应用的所有进程。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the input parameter is not valid parameter. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let isClearPageStack = false;
let appIndex = 1;

try {
  appManager.killProcessesByBundleName(bundleName, isClearPageStack, appIndex).then((data) => {
    console.info('killProcessesByBundleName success.');
  }).catch((error: Error) => {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error(`killProcessesByBundleName fail, code: ${code}, msg:${message}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

