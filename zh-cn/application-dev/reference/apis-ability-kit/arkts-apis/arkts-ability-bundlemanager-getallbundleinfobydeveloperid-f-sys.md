# getAllBundleInfoByDeveloperId（系统接口）

## getAllBundleInfoByDeveloperId

```TypeScript
function getAllBundleInfoByDeveloperId(developerId: string): Array<BundleInfo>
```

���ݸ�����developerId��ȡ��ǰ�û��µİ���Ϣ�б���

**起始版本：** 12

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| developerId | string | 是 | ��ʾӦ�õĿ�����ID�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;BundleInfo&gt; | ͬ������Array�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter developerId is empty. |
| [17700059](../../errorcode-universal.md#17700059-The) | The specified developerId is invalid. |

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

