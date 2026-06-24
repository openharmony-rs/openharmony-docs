# getSpecifiedDistributionType（系统接口）

## getSpecifiedDistributionType

```TypeScript
function getSpecifiedDistributionType(bundleName: string): string
```

��ͬ���ķ�����ѯָ��bundleName��[HarmonyAppProvision�����ļ�˵��](../../../../security/app-provision-structure.md)���÷���ֵ���ڵ���install�ӿ�ʱ��
���[InstallParam](arkts-ability-installer-installparam-i-sys.md#InstallParam)�е�specifiedDistributionType�ֶΡ�

��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָ����bundleName�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | ����ָ��bundleName��[HarmonyAppProvision�����ļ�˵��](../../../../security/app-provision-structure.md)�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";

try {
  let type = bundleManager.getSpecifiedDistributionType(bundleName);
  hilog.info(0x0000, 'testTag', 'getSpecifiedDistributionType successfully, type:%{public}s', type);
} catch (error) {
  let message = (error as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSpecifiedDistributionType failed. Cause: %{public}s', message);
}

```

