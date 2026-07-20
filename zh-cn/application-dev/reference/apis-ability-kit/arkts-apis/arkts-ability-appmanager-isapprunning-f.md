# isAppRunning

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

<a id="isapprunning"></a>
## isAppRunning

```TypeScript
function isAppRunning(bundleName: string, appCloneIndex?: number): Promise<boolean>
```

判断所有用户下指定包名和分身应用索引的应用是否正在运行。使用Promise异步回调。

> **说明：**  
>  
> 如果当前用户未安装该应用，则返回错误码16000073；如果当前用户已安装该应用，则判断所有用户下该指定应用是否正在运行。

**起始版本：** 14

**需要权限：** ohos.permission.GET_RUNNING_INFO

<!--Device-appManager-function isAppRunning(bundleName: string, appCloneIndex?: int): Promise<boolean>--><!--Device-appManager-function isAppRunning(bundleName: string, appCloneIndex?: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 查询的应用包名。 |
| appCloneIndex | number | 否 | 分身应用索引，默认值为0。取值范围：0~1000。取值为0时表示主应用；取值大于0时表示指定分身应用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示至少存在一个用户正在运行指定包名和分身应用索引的应用，返回false表示所有用户下指定包名和分身应用索引的应用都没有运行。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = "ohos.samples.etsclock";
  appManager.isAppRunning(bundleName).then((data: boolean) => {
      hilog.info(0x0000, 'testTag', `data: ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `isAppRunning error, code: ${err.code}, msg:${err.message}`);
    })
} catch (err) {
  hilog.error(0x0000, 'testTag', `isAppRunning error, code: ${err.code}, msg:${err.message}`);
}

```

