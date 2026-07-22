# getRunningMultiAppInfo（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## getRunningMultiAppInfo

```TypeScript
function getRunningMultiAppInfo(bundleName: string): Promise<RunningMultiAppInfo>
```

根据应用包名获取系统中运行态的应用多开（即在一个设备上运行多个相同的应用）的相关信息。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.GET_RUNNING_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-appManager-function getRunningMultiAppInfo(bundleName: string): Promise<RunningMultiAppInfo>--><!--Device-appManager-function getRunningMultiAppInfo(bundleName: string): Promise<RunningMultiAppInfo>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 查询的应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RunningMultiAppInfo&gt; | Promise对象。返回特定包名的运行态应用多开信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000072](../errorcode-ability.md#16000072-不支持应用多开) | App clone or multi-instance is not supported. |
| [18500001](../errorcode-ability.md#18500001-指定的包名无效) | The bundle does not exist or no patch has been applied. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = "ohos.samples.etsclock";
  appManager.getRunningMultiAppInfo(bundleName).then((info: appManager.RunningMultiAppInfo) => {
      hilog.info(0x0000, 'testTag', `getRunningMultiAppInfo success`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
    })
} catch (err) {
  hilog.error(0x0000, 'testTag', `getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
}

```

