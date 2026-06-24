# setAbilityFileTypesForSelf（系统接口）

## setAbilityFileTypesForSelf

```TypeScript
function setAbilityFileTypesForSelf(moduleName: string, abilityName: string, fileTypes: Array<string>): void
```

���õ�ǰӦ��֧�ִ򿪵��ļ����͡�

**起始版本：** 22

**需要权限：** ohos.permission.MANAGE_SELF_SKILLS

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| moduleName | string | 是 | ��ʾģ������ơ� |
| abilityName | string | 是 | ��ʾUIAbility��������ơ� |
| fileTypes | Array&lt;string&gt; | 是 | ��ʾ�ļ����͡�fileTypes���鳤�Ȳ��ܳ���1024��ÿ��Ԫ�ز��ܳ���512���ַ���Ԫ��ȡֵΪ<br/>[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)�е�ֵ��Ԫ�ز���Ϊ�ա�ͨ�����<br/>general.object�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [17700002](../../errorcode-universal.md#17700002-The) | The specified moduleName is not found. |
| [17700003](../../errorcode-universal.md#17700003-The) | The specified abilityName is not found. |
| [17700351](../../errorcode-universal.md#17700351-Invalid) | Invalid fileTypes. Possible causes:<br/>1. The array length exceeds 1024;<br/>2. The array contains an empty item;<br/>3. An item exceeds 512 characters;<br/>4. The array contains wildcard or general.object. |

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

