# getProfileByAbility

## getProfileByAbility

```TypeScript
function getProfileByAbility(moduleName: string, abilityName: string, metadataName: string, callback: AsyncCallback<Array<string>>): void
```

���ݸ�����moduleName��abilityName��metadataName��module.json5��
[abilities��ǩ](../../../../quick-start/module-configuration-file.md#abilities��ǩ)�µ�metadata��ǩ��name����ȡ������Ӧ�����ļ���json��ʽ�ַ���
��ʹ��callback�첽�ص���

> ˵����
> > ��������ļ���Ϣ��������Դ���ø�ʽ���򷵻�ֵ��������Դ���ø�ʽ������ $string:res_id���������߿���ͨ��[��Դ����](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md#resourceManager)����
> �ؽӿڣ�����ȡ���õ���Դ��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | ��ʾModule���ơ� |
| abilityName | string | 是 | ��ʾUIAbility��������ơ� |
| metadataName | string | 是 | ��ʾUIAbility�����<br/>[Ԫ��Ϣ����](../../../../quick-start/module-configuration-file.md#metadata��ǩ)����module.json5�����ļ���<br/>[abilities��ǩ](../../../../quick-start/module-configuration-file.md#abilities��ǩ)�µ�metadata��ǩ��name�� |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | 是 | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪ<br/>undefined��dataΪ��ȡ����Array������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not existed. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified abilityName is not existed. |
| [17700024](../../errorcode-universal.md#17700024-Failed) | Failed to get the profile because there is no profile in the HAP. |
| [17700029](../../errorcode-universal.md#17700029-The) | The specified ability is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName = 'entry';
let abilityName = 'EntryAbility';
let metadataName = 'ability_metadata';

try {
  bundleManager.getProfileByAbility(moduleName, abilityName, metadataName, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getProfileByAbility failed. Cause: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getProfileByAbility successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByAbility failed. Cause: %{public}s', message);
}

```


## getProfileByAbility

```TypeScript
function getProfileByAbility(moduleName: string, abilityName: string, metadataName?: string): Promise<Array<string>>
```

���ݸ�����moduleName��abilityName��metadataName��module.json5��
[abilities��ǩ](../../../../quick-start/module-configuration-file.md#abilities��ǩ)�µ�metadata��ǩ��name����ȡ������Ӧ�����ļ���json��ʽ�ַ���
��ʹ��Promise�첽�ص���

> ˵����
> > ��������ļ���Ϣ��������Դ���ø�ʽ���򷵻�ֵ��������Դ���ø�ʽ������ $string:res_id���������߿���ͨ��[��Դ����](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md#resourceManager)����
> �ؽӿڣ�����ȡ���õ���Դ��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | ��ʾModule���ơ� |
| abilityName | string | 是 | ��ʾUIAbility��������ơ� |
| metadataName | string | 否 | ��ʾUIAbility�����Ԫ��Ϣ���ƣ���module.json5�����ļ���<br/>[abilities��ǩ](../../../../quick-start/module-configuration-file.md#abilities��ǩ)�µ�metadata��ǩ��name��Ĭ��ֵΪ�ա� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise���󣬷���Array�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not existed. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified abilityName is not existed. |
| [17700024](../../errorcode-universal.md#17700024-Failed) | Failed to get the profile because there is no profile in the HAP. |
| [17700029](../../errorcode-universal.md#17700029-The) | The specified ability is disabled. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName = 'entry';
let abilityName = 'EntryAbility';

try {
  // 通过模块名称和ability名称获取相应配置文件的json格式字符串信息
  bundleManager.getProfileByAbility(moduleName, abilityName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getProfileByAbility successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getProfileByAbility failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByAbility failed. Cause: %{public}s', message);
}

```

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName = 'entry';
let abilityName = 'EntryAbility';
let metadataName = 'ability_metadata';

try {
  // 通过模块名称，ability名称和UIAbility组件的元信息名称获取自身相应配置文件的json格式字符串信息
  bundleManager.getProfileByAbility(moduleName, abilityName, metadataName).then((data) => {
    hilog.info(0x0000, 'testTag', 'getProfileByAbility successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getProfileByAbility failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByAbility failed. Cause: %{public}s', message);
}

```

