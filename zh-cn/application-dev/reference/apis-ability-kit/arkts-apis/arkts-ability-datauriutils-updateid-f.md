# updateId

## updateId

```TypeScript
function updateId(uri: string, id: double): string
```

更新指定uri中的ID。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-dataUriUtils-function updateId(uri: string, id: double): string--><!--Device-dataUriUtils-function updateId(uri: string, id: double): string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示uri对象 |
| id | double | 是 | 表示要更新的ID |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回更新ID之后的uri对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

## 示例

```TypeScript
import { dataUriUtils } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let id = 1122;
  let uri = dataUriUtils.updateId(
    'com.example.dataUriUtils/1221',
    id
  );
} catch (err) {
  console.error(`update id err, code: ${(err as BusinessError).code}, msg: ${(err as BusinessError).message}`);
}
```

