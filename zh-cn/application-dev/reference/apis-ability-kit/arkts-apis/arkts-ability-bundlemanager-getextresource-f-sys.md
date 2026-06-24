# getExtResource（系统接口）

## getExtResource

```TypeScript
function getExtResource(bundleName: string): Promise<Array<string>>
```

���ݸ�����bundleName�����չ��Դ��Ӧ��moduleNames��ʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��չ��Դ��Ӧ�����ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise���󣬷��ؽӿ����н������չ��Դ��Ӧ��moduleNames�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700303](../../errorcode-universal.md#17700303-Failed) | Failed to obtain extended resources. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';

try {
  bundleManager.getExtResource(bundleName).then((modules: Array<string>) => {
    for (let i = 0; i < modules.length; i++) {
      hilog.info(0x0000, 'testTag', 'getExtResource item: %{public}s', modules[i]);
    }
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getExtResource failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getExtResource failed. Cause: %{public}s', message);
}

```

