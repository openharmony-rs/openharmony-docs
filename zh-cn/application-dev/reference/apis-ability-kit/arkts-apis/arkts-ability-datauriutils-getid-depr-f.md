# getId

## 导入模块

```TypeScript
```

## getId

```TypeScript
function getId(uri: string): number
```

获取指定uri路径末尾的ID。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getId](arkts-ability-datauriutils-getid-f.md)

<!--Device-dataUriUtils-function getId(uri: string): number--><!--Device-dataUriUtils-function getId(uri: string): number-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示uri对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回uri路径末尾的ID。 |

**示例**

```TypeScript
import dataUriUtils from '@ohos.ability.dataUriUtils';

let id = dataUriUtils.getId('com.example.dataUriUtils/1221');
```

