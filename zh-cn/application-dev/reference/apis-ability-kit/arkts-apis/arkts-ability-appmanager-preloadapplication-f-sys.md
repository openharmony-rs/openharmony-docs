# preloadApplication（系统接口）

## preloadApplication

```TypeScript
function preloadApplication(bundleName: string, userId: number, mode: PreloadMode, appIndex?: number): Promise<void>
```

预加载应用进程。接口返回成功并不代表预加载成功，具体结果以目标应用进程是否创建成功为准。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.PRELOAD_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 预加载的应用包名。 |
| userId | number | 是 | 预加载的用户Id。 |
| mode | PreloadMode | 是 | 预加载模式。 |
| appIndex | number | 否 | 预加载应用分身的appIndex。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |
| [16300005](../../errorcode-universal.md#16300005-The) | The target bundle does not exist. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let bundleName = "ohos.samples.etsclock";
  let userId = 100;
  let mode = appManager.PreloadMode.PRESS_DOWN;
  let appIndex = 0;
  appManager.preloadApplication(bundleName, userId, mode, appIndex)
    .then(() => {
      hilog.info(0x0000, 'testTag', `preloadApplication success`);
    })
    .catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `preloadApplication error, code: ${err.code}, msg:${err.message}`);
    })
} catch (err) {
  hilog.error(0x0000, 'testTag', `preloadApplication error, code: ${(err as BusinessError).code}, msg:${(err as BusinessError).message}`);
}

```

