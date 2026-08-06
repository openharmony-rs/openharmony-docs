# resetDefaultApplicationSync（系统接口）

## resetDefaultApplicationSync

```TypeScript
function resetDefaultApplicationSync(type: string, userId?: int): void
```

以同步方法根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型重置默认应用。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.SET_DEFAULT_APPLICATION

<!--Device-defaultAppManager-function resetDefaultApplicationSync(type: string, userId?: int): void--><!--Device-defaultAppManager-function resetDefaultApplicationSync(type: string, userId?: int): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要重置的应用类型，取[ApplicationType]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的值，或者符合媒体类型格式的文件类型，或者[UniformDataType]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_类型。 |
| userId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 否 | 表示用户ID，可以通过[getOsAccountLocalId接口]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_获取。默认值：调用方所在用户。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700025](../errorcode-bundle.md#17700025-输入的type无效) | The specified type is invalid. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
import { uniformTypeDescriptor } from '@kit.ArkData';

let userId = 100;
try {
  defaultAppManager.resetDefaultApplicationSync(defaultAppManager.ApplicationType.BROWSER, userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

try {
  defaultAppManager.resetDefaultApplicationSync("image/png", userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};

try {
  defaultAppManager.resetDefaultApplicationSync(uniformTypeDescriptor.UniformDataType.AVI, userId);
  console.info('Operation successful.');
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};
```

