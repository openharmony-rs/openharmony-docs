# deleteAbc（系统接口）

## deleteAbc

```TypeScript
function deleteAbc(abcPath: string): Promise<void>
```

���ݸ�����abcPathɾ��.abc�ļ���ʹ��Promise�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.RUN_DYN_CODE

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abcPath | string | 是 | .abc�ļ�·���� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700202](../../errorcode-universal.md#17700202-Failed) | Failed to delete the abc file. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api.&lt;br&gt;**适用版本：** 12+ |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let abcPath: string = '/data/storage/el2/base/a.abc';

try {
  bundleManager.deleteAbc(abcPath).then((data) => {
    hilog.info(0x0000, 'testTag', 'deleteAbc successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'deleteAbc failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'deleteAbc failed. Cause: %{public}s', message);
}

```

