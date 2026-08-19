# updateId

## 导入模块

```TypeScript
```

## updateId

```TypeScript
function updateId(uri: string, id: number): string
```

更新指定uri中的ID。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [updateId](arkts-ability-datauriutils-updateid-f.md)

<!--Device-dataUriUtils-function updateId(uri: string, id: number): string--><!--Device-dataUriUtils-function updateId(uri: string, id: number): string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示uri对象。 |
| id | number | 是 | 表示要更新的ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回更新ID之后的uri对象。 |

**示例**

```TypeScript
import dataUriUtils from '@ohos.ability.dataUriUtils';

let id = 1122;
let uri = dataUriUtils.updateId(
    'com.example.dataUriUtils/1221',
	id
);
```

