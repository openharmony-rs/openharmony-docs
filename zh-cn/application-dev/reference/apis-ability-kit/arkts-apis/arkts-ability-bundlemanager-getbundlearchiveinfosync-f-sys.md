# getBundleArchiveInfoSync（系统接口）

## getBundleArchiveInfoSync

```TypeScript
function getBundleArchiveInfoSync(hapFilePath: string, bundleFlags: number): BundleInfo
```

��ͬ���������ݸ�����hapFilePath��bundleFlags��ȡBundleInfo����

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePath | string | 是 | ��ʾ�洢HAP��·����·��Ӧ���ǵ�ǰӦ�ó�������Ŀ¼�����·���� |
| bundleFlags | number | 是 | ��ʾ����ָ��Ҫ���ص�BundleInfo�����а�������Ϣ�ı�־�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BundleInfo | ����BundleInfo���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700022](../../errorcode-universal.md#17700022-The) | The hapFilePath is invalid. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let hapFilePath = "/data/xxx/test.hap";
let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_DEFAULT;

try {
  let data = bundleManager.getBundleArchiveInfoSync(hapFilePath, bundleFlags)
  hilog.info(0x0000, 'testTag', 'getBundleArchiveInfoSync successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleArchiveInfoSync failed. Cause: %{public}s', message);
}

```

