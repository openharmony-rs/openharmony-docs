# getProfileByExtensionAbilitySync

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getProfileByExtensionAbilitySync

```TypeScript
function getProfileByExtensionAbilitySync(moduleName: string, extensionAbilityName: string, metadataName?: string): Array<string>
```

以同步方法根据给定的moduleName、extensionAbilityName和metadataName（module.json5中[metadata标签](../../../../quick-start/module-configuration-file.md#metadata标签)下的name）获取自身相应配置文件的json格式字符串，返回对象为string数组。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-bundleManager-function getProfileByExtensionAbilitySync(moduleName: string, extensionAbilityName: string, metadataName?: string): Array<string>--><!--Device-bundleManager-function getProfileByExtensionAbilitySync(moduleName: string, extensionAbilityName: string, metadataName?: string): Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 表示Module名称。 |
| extensionAbilityName | string | 是 | 表示ExtensionAbility组件的名称。 |
| metadataName | string | 否 | 表示ExtensionAbility组件的元信息名称，即module.json5配置文件中[extensionAbilities标签](../../../../quick-start/module-configuration-file.md#extensionabilities标签)下的metadata标签的name，默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 返回Array&lt;string&gt;对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified moduleName is not existed. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified extensionAbilityName not existed. |
| [17700024](../errorcode-bundle.md#17700024-没有相应的配置文件) | Failed to get the profile because there is no profile in the HAP. |

**示例：**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName = 'entry';
let extensionAbilityName = 'com.example.myapplication.extension';
let metadataName = 'ability_metadata';

try {
  let data = bundleManager.getProfileByExtensionAbilitySync(moduleName, extensionAbilityName);
  hilog.info(0x0000, 'testTag', 'getProfileByExtensionAbilitySync successfully. Data: %{public}s',
    JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbilitySync failed. Cause: %{public}s', message);
}

try {
  let data = bundleManager.getProfileByExtensionAbilitySync(moduleName, extensionAbilityName, metadataName);
  hilog.info(0x0000, 'testTag', 'getProfileByExtensionAbilitySync successfully. Data: %{public}s',
    JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbilitySync failed. Cause: %{public}s', message);
}

```

