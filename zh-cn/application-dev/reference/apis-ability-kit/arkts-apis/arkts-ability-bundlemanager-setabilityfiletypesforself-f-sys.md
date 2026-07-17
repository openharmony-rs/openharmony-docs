# setAbilityFileTypesForSelf（系统接口）

## 导入模块

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## setAbilityFileTypesForSelf

```TypeScript
function setAbilityFileTypesForSelf(moduleName: string, abilityName: string, fileTypes: Array<string>): void
```

设置当前应用支持打开的文件类型。

**起始版本：** 22

**需要权限：** ohos.permission.MANAGE_SELF_SKILLS

<!--Device-bundleManager-function setAbilityFileTypesForSelf(moduleName: string, abilityName: string, fileTypes: Array<string>): void--><!--Device-bundleManager-function setAbilityFileTypesForSelf(moduleName: string, abilityName: string, fileTypes: Array<string>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | 表示模块的名称。 |
| abilityName | string | 是 | 表示UIAbility组件的名称。 |
| fileTypes | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 是 | 表示文件类型。fileTypes数组长度不能超过1024，每个元素不能超过512个字符，元素取值为[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)中的值，元素不能为空、通配符、general.object。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700002](../errorcode-bundle.md#17700002-指定的modulename不存在) | The specified moduleName is not found. |
| [17700003](../errorcode-bundle.md#17700003-指定的abilityname不存在) | The specified abilityName is not found. |
| [17700351](../errorcode-bundle.md#17700351-无效的文件类型) | Invalid fileTypes. Possible causes:1. The array length exceeds 1024;2. The array contains an empty item;3. An item exceeds 512 characters;4. The array contains wildcard or general.object. |

**示例：**

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

