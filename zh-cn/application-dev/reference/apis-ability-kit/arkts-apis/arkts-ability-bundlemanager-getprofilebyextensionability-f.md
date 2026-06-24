# getProfileByExtensionAbility

## getProfileByExtensionAbility

```TypeScript
function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName: string, callback: AsyncCallback<Array<string>>): void
```

���ݸ�����moduleName��extensionAbilityName��metadataName��module.json5��
[metadata��ǩ](../../../../quick-start/module-configuration-file.md#metadata��ǩ)�µ�name����ȡ������Ӧ�����ļ���json��ʽ�ַ�����ʹ��callback�첽
�ص���

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | ��ʾModule���ơ� |
| extensionAbilityName | string | 是 | ��ʾExtensionAbility��������ơ� |
| metadataName | string | 是 | ��ʾExtensionAbility�����Ԫ��Ϣ���ƣ���module.json5�����ļ���<br/>[extensionAbilities��ǩ](../../../../quick-start/module-configuration-file.md#extensionabilities��ǩ)�µ�metadata��ǩ��<br/>name�� |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪ<br/>undefined��dataΪ��ȡ����Array������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not existed. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified extensionAbilityName not existed. |
| [17700024](../../errorcode-universal.md#17700024-Failed) | Failed to get the profile because there is no profile in the HAP. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName = 'entry';
let extensionAbilityName = 'com.example.myapplication.extension';
let metadataName = 'ability_metadata';

try {
  bundleManager.getProfileByExtensionAbility(moduleName, extensionAbilityName, metadataName, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getProfileByExtensionAbility successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed: %{public}s', message);
}

```


## getProfileByExtensionAbility

```TypeScript
function getProfileByExtensionAbility(moduleName: string, extensionAbilityName: string, metadataName?: string): Promise<Array<string>>
```

���ݸ�����moduleName��extensionAbilityName��metadataName��module.json5��
[metadata��ǩ](../../../../quick-start/module-configuration-file.md#metadata��ǩ)�µ�name����ȡ������Ӧ�����ļ���json��ʽ�ַ�����ʹ��Promise�첽��
����

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | ��ʾModule���ơ� |
| extensionAbilityName | string | 是 | ��ʾExtensionAbility��������ơ� |
| metadataName | string | 否 | ��ʾExtensionAbility�����Ԫ��Ϣ���ƣ���module.json5�����ļ���<br/>[extensionAbilities��ǩ](../../../../quick-start/module-configuration-file.md#extensionabilities��ǩ)�µ�metadata��ǩ��<br/>name��Ĭ��ֵΪ�ա� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise���󣬷���Array���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not existed. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified extensionAbilityName not existed. |
| [17700024](../../errorcode-universal.md#17700024-Failed) | Failed to get the profile because there is no profile in the HAP. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName = 'entry';
let extensionAbilityName = 'com.example.myapplication.extension';
let metadataName = 'ability_metadata';

try {
  bundleManager.getProfileByExtensionAbility(moduleName, extensionAbilityName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getProfileByExtensionAbility successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed. Cause: %{public}s', message);
}

try {
  bundleManager.getProfileByExtensionAbility(moduleName, extensionAbilityName, metadataName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getProfileByExtensionAbility successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbility failed. Cause: %{public}s', message);
}

```

