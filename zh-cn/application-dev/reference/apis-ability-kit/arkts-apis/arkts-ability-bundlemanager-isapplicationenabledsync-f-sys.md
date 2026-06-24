# isApplicationEnabledSync（系统接口）

## isApplicationEnabledSync

```TypeScript
function isApplicationEnabledSync(bundleName: string): boolean
```

��ͬ��������ȡָ��Ӧ�õĽ��û�ʹ��״̬��

**起始版本：** 10

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾӦ�ó����bundleName�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ����true��ʾ��ǰӦ��Ϊʹ��״̬������false��ʾ��ǰӦ��Ϊ����״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';

try {
  let data = bundleManager.isApplicationEnabledSync(bundleName);
  hilog.info(0x0000, 'testTag', 'isApplicationEnabledSync successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'isApplicationEnabledSync failed: %{public}s', message);
}

```

