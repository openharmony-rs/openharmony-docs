# setAbilityFileTypesForSelf (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## setAbilityFileTypesForSelf

```TypeScript
function setAbilityFileTypesForSelf(moduleName: string, abilityName: string, fileTypes: Array<string>): void
```

Sets the file types that can be opened by the current application.

**Since:** 22

**Required permissions:** ohos.permission.MANAGE_SELF_SKILLS

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name. |
| abilityName | string | Yes | Name of the UIAbility component. |
| fileTypes | Array&lt;string&gt; | Yes | Array of file types. The array must contain no more than 1024 elements, and each element must not exceed 512 characters. Valid values must be from [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md). Empty values, wildcard characters, and **general.object** are not allowed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified moduleName is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified abilityName is not found. |
| [17700351](../errorcode-bundle.md#17700351-invalid-file-type) | Invalid fileTypes. Possible causes: 1. The array length exceeds 1024; 2. The array contains an empty item; 3. An item exceeds 512 characters; 4. The array contains wildcard or general.object. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName: string = "entry";
let abilityName: string = "EntryAbility";
let fileTypes: Array<string> = ["general.png", "general.jpeg"];

try {
  bundleManager.setAbilityFileTypesForSelf(moduleName, abilityName, fileTypes);
  hilog.info(0x0000, 'testTag', 'setAbilityFileTypesForSelf successfully');
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setAbilityFileTypesForSelf failed. Cause: %{public}s', message);
}
```
