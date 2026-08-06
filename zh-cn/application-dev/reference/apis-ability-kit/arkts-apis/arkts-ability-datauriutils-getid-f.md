# getId

## getId

```TypeScript
function getId(uri: string): double
```

获取指定uri路径末尾的ID。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-dataUriUtils-function getId(uri: string): double--><!--Device-dataUriUtils-function getId(uri: string): double-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示uri对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 返回uri路径末尾的ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { dataUriUtils } from '@kit.AbilityKit';

try {
  let id = dataUriUtils.getId('com.example.dataUriUtils/1221');
  console.info(`get id: ${id}`);
} catch (err) {
  console.error(`get id err ,check the uri ${err}`);
}
```

