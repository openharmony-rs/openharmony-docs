# getBundleInfoForSelf

## getBundleInfoForSelf

```TypeScript
function getBundleInfoForSelf(bundleFlags: number): Promise<BundleInfo>
```

���ݸ�����bundleFlags��ȡ��ǰӦ�õ�BundleInfo��ʹ��Promise�첽�ص���

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | ָ�����ص�BundleInfo����������Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleInfo&gt; | Promise���󣬷��ص�ǰӦ�õ�BundleInfo�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |

**示例：**

```TypeScript
// 获取bundleInfo，包含带有metadataArray信息的appInfo信息
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleFlags =
  bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION | bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_METADATA;

try {
  bundleManager.getBundleInfoForSelf(bundleFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getBundleInfoForSelf successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getBundleInfoForSelf failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleInfoForSelf failed: %{public}s', message);
}

```


## getBundleInfoForSelf

```TypeScript
function getBundleInfoForSelf(bundleFlags: number, callback: AsyncCallback<BundleInfo>): void
```

���ݸ�����bundleFlags��ȡ��ǰӦ�õ�BundleInfo��ʹ��callback�첽�ص���

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | ָ�����ص�BundleInfo����������Ϣ�� |
| callback | AsyncCallback&lt;BundleInfo&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪ<br/>undefined��dataΪ��ȡ���ĵ�ǰӦ�õ�BundleInfo������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |

**示例：**

```TypeScript
// 获取bundleInfo，包含permissions信息的abilitiesInfo信息
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleFlags =
  bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_HAP_MODULE | bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_ABILITY |
  bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION;

try {
  bundleManager.getBundleInfoForSelf(bundleFlags, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getBundleInfoForSelf failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getBundleInfoForSelf successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getBundleInfoForSelf failed: %{public}s', message);
}

```

