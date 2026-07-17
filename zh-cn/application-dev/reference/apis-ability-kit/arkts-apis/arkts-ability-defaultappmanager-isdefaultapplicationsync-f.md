# isDefaultApplicationSync

## 导入模块

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## isDefaultApplicationSync

```TypeScript
function isDefaultApplicationSync(type: string): boolean
```

以同步方法根据系统已定义的应用类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-data-uniformtypedescriptor.md)类型判断当前应用是否是该类型的默认应用，使用boolean形式返回结果。

**起始版本：** 10

<!--Device-defaultAppManager-function isDefaultApplicationSync(type: string): boolean--><!--Device-defaultAppManager-function isDefaultApplicationSync(type: string): boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 要查询的应用类型，取[ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md)或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-data-uniformtypedescriptor.md)类型中的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前应用是否是默认应用，true表示是默认应用，false表示不是默认应用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';

try {
  let data = defaultAppManager.isDefaultApplicationSync(defaultAppManager.ApplicationType.BROWSER)
  console.info('Operation successful. IsDefaultApplicationSync ? ' + JSON.stringify(data));
} catch (error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
}

```

