# getAdditionalInfo（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

<a id="getadditionalinfo"></a>
## getAdditionalInfo

```TypeScript
function getAdditionalInfo(bundleName: string): string
```

以同步接口查询指定bundleName的额外信息。该返回值是在调用install接口时传入的[InstallParam](arkts-ability-installer-installparam-i-sys.md)中的additionalInfo字段。

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getAdditionalInfo(bundleName: string): string--><!--Device-bundleManager-function getAdditionalInfo(bundleName: string): string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 指定的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回指定bundleName的额外信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter bundleName is empty. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundleName is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";

try {
  let info = bundleManager.getAdditionalInfo(bundleName);
  hilog.info(0x0000, 'testTag', 'getAdditionalInfo successfully, additionInfo:%{public}s', info);
} catch (error) {
  let message = (error as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAdditionalInfo failed. Cause: %{public}s', message);
}

```

