# getProfileByAbilitySync

## getProfileByAbilitySync

```TypeScript
function getProfileByAbilitySync(moduleName: string, abilityName: string, metadataName?: string): Array<string>
```

��ͬ���������ݸ�����moduleName��abilityName��metadataName��module.json5��
[metadata��ǩ](../../../../quick-start/module-configuration-file.md#metadata��ǩ)�µ�name����ȡ������Ӧ�����ļ���json��ʽ�ַ��������ض���Ϊstring��
�顣

**起始版本：** 10

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
| Array&lt;string&gt; | ������󣬷���Array�� |

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
  let data = bundleManager.getProfileByAbilitySync(moduleName, abilityName);
  hilog.info(0x0000, 'testTag', 'getProfileByAbilitySync successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByAbilitySync failed. Cause: %{public}s', message);
}

```

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName: string = 'entry';
let abilityName: string = 'EntryAbility';
let metadataName: string = 'ability_metadata';

try {
  // 通过模块名称，ability名称和UIAbility组件的元信息名称获取相应配置文件的json格式字符串信息
  let data = bundleManager.getProfileByAbilitySync(moduleName, abilityName, metadataName);
  hilog.info(0x0000, 'testTag', 'getProfileByAbilitySync successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByAbilitySync failed. Cause: %{public}s', message);
}

```

