# switchUninstallState（系统接口）

## switchUninstallState

```TypeScript
function switchUninstallState(bundleName: string, state: boolean): void
```

�л�ָ��Ӧ�õĿ�ж��״̬���˽ӿ���EDMӦ�����عܿػ��Ʋ�����Ӱ�졣

**起始版本：** 12

**需要权限：** ohos.permission.CHANGE_BUNDLE_UNINSTALL_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾָ��Ӧ�õ�bundleName�� |
| state | boolean | 是 | ��ʾӦ�õĿ�ж��״̬��ֵΪtrue��ʾӦ�ÿ��Ա�ж�أ�ֵΪfalse��ʾӦ�ò����Ա�ж�ء� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700060](../../errorcode-universal.md#17700060-The) | The specified application cannot be uninstalled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  bundleManager.switchUninstallState('com.example.myapplication', false);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'switchUninstallState failed: %{public}s', message);
}

```

