# cleanBundleCacheFiles（系统接口）

## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string, callback: AsyncCallback<void>): void
```

���ݸ�����bundleName����BundleCache��ʹ��callback�첽�ص���

���÷�����������������ʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.REMOVE_CACHE_FILES

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾҪ�����仺�����ݵ�Ӧ�ó����bundleName�� |
| callback | AsyncCallback&lt;void&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)��������Ӧ�û���Ŀ¼���ݳɹ���errΪ<br/>undefined������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700030](../../errorcode-universal.md#17700030-The) | The specified bundle does not support clearing of cache files. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";

try {
  bundleManager.cleanBundleCacheFiles(bundleName, err => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'cleanBundleCacheFiles successfully.');
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', message);
}

```


## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string): Promise<void>
```

���ݸ�����bundleName����BundleCache��ʹ��Promise�첽�ص���

���÷�����������������ʱ����ҪȨ�ޡ�

**起始版本：** 9

**需要权限：** ohos.permission.REMOVE_CACHE_FILES

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾҪ�����仺�����ݵ�Ӧ�ó����bundleName�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700030](../../errorcode-universal.md#17700030-The) | The specified bundle does not support clearing of cache files. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";

try {
  bundleManager.cleanBundleCacheFiles(bundleName).then(() => {
    hilog.info(0x0000, 'testTag', 'cleanBundleCacheFiles successfully.');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', message);
}

```


## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string, appIndex: number): Promise<void>
```

���ݸ�����bundleName��appIndex����BundleCache��ʹ��Promise�첽�ص���

���÷�����������������ʱ����ҪȨ�ޡ�

**起始版本：** 15

**需要权限：** ohos.permission.REMOVE_CACHE_FILES

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ʾҪ�����仺�����ݵ�Ӧ�ó����bundleName�� |
| appIndex | number | 是 | ��ʾҪ�����仺�����ݵ�Ӧ�ó���ķ���Ӧ��������<br/>appIndexΪ0ʱ����ʾ������Ӧ�û������ݡ�appIndex����0ʱ����ʾ����ָ������Ӧ�û������ݡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700030](../../errorcode-universal.md#17700030-The) | The specified bundle does not support clearing of cache files. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex not in valid range. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";
let appIndex = 1;

try {
  bundleManager.cleanBundleCacheFiles(bundleName, appIndex).then(() => {
    hilog.info(0x0000, 'testTag', 'cleanBundleCacheFiles successfully.');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'cleanBundleCacheFiles failed: %{public}s', message);
}

```

