# deleteId

## 导入模块

```TypeScript
```

## deleteId

```TypeScript
function deleteId(uri: string): string
```

删除指定uri路径末尾的ID。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [deleteId](arkts-ability-datauriutils-deleteid-f.md)

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要从中删除ID的uri对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回删除ID之后的uri对象。 |

**示例**

```TypeScript
import dataUriUtils from '@ohos.ability.dataUriUtils';

let uri = dataUriUtils.deleteId('com.example.dataUriUtils/1221');
```
