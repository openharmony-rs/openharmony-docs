# getDeveloperIds（系统接口）

## getDeveloperIds

```TypeScript
function getDeveloperIds(appDistributionType?: number): Array<string>
```

���ݸ�����Ӧ��[appDistributionType](arkts-ability-bundlemanager-appdistributiontype-e-sys.md#AppDistributionType)��ȡ��ǰ�û��µ����п�����ID�б���

**起始版本：** 12

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appDistributionType | number | 否 | ��ʾӦ�õķַ����ͣ����ò���ȱʡʱ���᷵������Ӧ�õĿ�����ID�б��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | ͬ������Array�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appDistributionType = bundleManager.AppDistributionType.ENTERPRISE;

try {
  let data = bundleManager.getDeveloperIds(appDistributionType);
  hilog.info(0x0000, 'testTag', 'getDeveloperIds successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getDeveloperIds failed: %{public}s', message);
}

```

