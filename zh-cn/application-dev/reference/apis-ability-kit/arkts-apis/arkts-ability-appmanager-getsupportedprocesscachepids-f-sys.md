# getSupportedProcessCachePids（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## getSupportedProcessCachePids

```TypeScript
function getSupportedProcessCachePids(bundleName : string): Promise<Array<number>>
```

查询当前应用中支持缓存后快速启动的进程PID。使用Promise异步回调。

> **说明：**  
>  
> 本接口仅支持获取调用者所在系统账号下的进程PID。

**起始版本：** 14

**需要权限：** ohos.permission.GET_RUNNING_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-appManager-function getSupportedProcessCachePids(bundleName : string): Promise<Array<int>>--><!--Device-appManager-function getSupportedProcessCachePids(bundleName : string): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要查询的应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<number>> | Promise对象。返回一个数组，包含当前应用中支持缓存后快速启动的所有进程PID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = "ohos.samples.processcache";
  appManager.getSupportedProcessCachePids(bundleName).then((pids: Array<number>) => {
      hilog.info(0x0000, 'testTag', `pids: ${JSON.stringify(pids)}`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `get pids error, code: ${err.code}, msg:${err.message}`);
    })
} catch (err) {
  hilog.error(0x0000, 'testTag', `get pids error, code: ${err.code}, msg:${err.message}`);
}

```

