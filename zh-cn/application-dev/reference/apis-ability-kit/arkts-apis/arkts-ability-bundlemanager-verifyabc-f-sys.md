# verifyAbc（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## verifyAbc

```TypeScript
function verifyAbc(abcPaths: Array<string>, deleteOriginalFiles: boolean, callback: AsyncCallback<void>): void
```

根据给定的abcPaths和deleteOriginalFiles校验.abc文件。使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.RUN_DYN_CODE

<!--Device-bundleManager-function verifyAbc(abcPaths: Array<string>, deleteOriginalFiles: boolean, callback: AsyncCallback<void>): void--><!--Device-bundleManager-function verifyAbc(abcPaths: Array<string>, deleteOriginalFiles: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abcPaths | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | .abc文件路径。 |
| deleteOriginalFiles | boolean | 是 | 是否删除.abc文件，true删除，false不删除。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)，当获取成功时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700201](../errorcode-bundle.md#17700201-abc文件校验失败) | Failed to verify the abc file. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let abcPaths: Array<string> = ['/data/storage/el2/base/a.abc'];

try {
  bundleManager.verifyAbc(abcPaths, true, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'verifyAbc failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'verifyAbc successfully');
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'verifyAbc failed: %{public}s', message);
}

```


## verifyAbc

```TypeScript
function verifyAbc(abcPaths: Array<string>, deleteOriginalFiles: boolean): Promise<void>
```

根据给定的abcPaths和deleteOriginalFiles校验.abc文件。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.RUN_DYN_CODE

<!--Device-bundleManager-function verifyAbc(abcPaths: Array<string>, deleteOriginalFiles: boolean): Promise<void>--><!--Device-bundleManager-function verifyAbc(abcPaths: Array<string>, deleteOriginalFiles: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abcPaths | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | .abc文件路径。 |
| deleteOriginalFiles | boolean | 是 | 是否删除.abc文件，true删除，false不删除。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700201](../errorcode-bundle.md#17700201-abc文件校验失败) | Failed to verify the abc file. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let abcPaths: Array<string> = ['/data/storage/el2/base/a.abc'];

try {
  bundleManager.verifyAbc(abcPaths, true).then((data) => {
    hilog.info(0x0000, 'testTag', 'verifyAbc successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'verifyAbc failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'verifyAbc failed. Cause: %{public}s', message);
}

```

