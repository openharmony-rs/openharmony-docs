# setApplicationEnabledSync（系统接口）

## setApplicationEnabledSync

```TypeScript
function setApplicationEnabledSync(bundleName: string, isEnabled: boolean): void
```

��ͬ����������ָ��Ӧ�õĽ��û�ʹ��״̬��

**起始版本：** 10

**需要权限：** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָ��Ӧ�õ�bundleName�� |
| isEnabled | boolean | 是 | ֵΪtrue��ʾʹ�ܣ�ֵΪfalse��ʾ���á� |

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

let bundleName = "com.ohos.myapplication";

try {
  bundleManager.setApplicationEnabledSync(bundleName, false);
  hilog.info(0x0000, 'testTag', 'setApplicationEnabledSync successfully.');
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setApplicationEnabledSync failed: %{public}s', message);
}

```


## setApplicationEnabledSync

```TypeScript
function setApplicationEnabledSync(bundleName: string, appIndex: number, isEnabled: boolean, killProcess: boolean): void
```

����Ӧ�ó��������û��ǽ��ã��������ڽ���ʱ�Ƿ�ɱ�����̡�

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ�ð��� |
| appIndex | number | 是 | Ӧ�õķ�������<br/><br/>ȡֵ��ΧΪȫ�������� |
| isEnabled | boolean | 是 | true��ʾ����Ӧ�ó���false��ʾ����Ӧ�ó��� |
| killProcess | boolean | 是 | true��ʾӦ�ý����ڽ���ʱɱ��Ӧ�ó�����̣���ֵΪfalse��ʾ����ʱ����ɱ��Ӧ�ó������ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. Non-system APP calling system API. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle is not found. |
| [17700061](../../errorcode-universal.md#17700061-The) | The specified app index is invalid. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 需要替换为要设置的应用Bundle名称、应用索引、是否启用应用和禁用应用时是否退出应用进程
let bundleName: string = 'com.example.myapplication';
let appIndex: number = 0;
let isEnabled: boolean = true;
let killProcess: boolean = false;

try {
  bundleManager.setApplicationEnabledSync(bundleName, appIndex, isEnabled, killProcess);
  hilog.info(0x0000, 'testTag', 'setApplicationEnabledSync successfully');
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setApplicationEnabledSync failed: %{public}s', message);
}

```

