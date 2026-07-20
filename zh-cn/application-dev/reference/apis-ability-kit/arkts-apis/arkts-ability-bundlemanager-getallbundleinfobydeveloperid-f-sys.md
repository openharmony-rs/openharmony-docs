# getAllBundleInfoByDeveloperId（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

<a id="getallbundleinfobydeveloperid"></a>
## getAllBundleInfoByDeveloperId

```TypeScript
function getAllBundleInfoByDeveloperId(developerId: string): Array<BundleInfo>
```

根据给定的developerId获取当前用户下的包信息列表。

**起始版本：** 12

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundleManager-function getAllBundleInfoByDeveloperId(developerId: string): Array<BundleInfo>--><!--Device-bundleManager-function getAllBundleInfoByDeveloperId(developerId: string): Array<BundleInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| developerId | string | 是 | 表示应用的开发者ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;BundleInfo&gt; | 同步返回Array<BundleInfo>。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter developerId is empty. |
| [17700059](../errorcode-bundle.md#17700059-指定的开发者id不存在) | The specified developerId is invalid. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let developerId = "123456.789";

try {
  let data = bundleManager.getAllBundleInfoByDeveloperId(developerId);
  hilog.info(0x0000, 'testTag', 'getAllBundleInfoByDeveloperId successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllBundleInfoByDeveloperId failed: %{public}s', message);
}

```

