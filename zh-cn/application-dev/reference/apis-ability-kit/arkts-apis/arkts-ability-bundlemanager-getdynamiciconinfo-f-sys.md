# getDynamicIconInfo（系统接口）

## getDynamicIconInfo

```TypeScript
function getDynamicIconInfo(bundleName: string): Promise<Array<DynamicIconInfo>>
```

����ָ����bundleName��ȡ�����û������з����µĶ�̬ͼ����Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 20

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��̬ͼ���Ӧ�ð����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;DynamicIconInfo&gt;&gt; | Promise���󣬷��ز�ѯ���Ķ�̬ͼ����Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700306](../../errorcode-universal.md#17700306-Failed) | Failed to obtain the dynamic icon. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';

try {
  bundleManager.getDynamicIconInfo(bundleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getDynamicIconInfo successfully %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getDynamicIconInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getDynamicIconInfo failed. Cause: %{public}s', message);
}

```

