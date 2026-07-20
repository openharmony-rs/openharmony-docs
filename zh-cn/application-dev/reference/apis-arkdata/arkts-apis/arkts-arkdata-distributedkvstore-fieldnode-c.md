# FieldNode

表示 Schema 实例的节点，提供定义存储在数据库中的值的方法。

**起始版本：** 9

<!--Device-distributedKVStore-class FieldNode--><!--Device-distributedKVStore-class FieldNode-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

<a id="appendchild"></a>
## appendChild

```TypeScript
appendChild(child: FieldNode): boolean
```

在当前 FieldNode 中添加一个子节点。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FieldNode-appendChild(child: FieldNode): boolean--><!--Device-FieldNode-appendChild(child: FieldNode): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| child | [FieldNode](arkts-arkdata-distributeddata-fieldnode-c.md) | 是 | 要附加的子节点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示子节点成功添加到FieldNode；返回false则表示操作失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript

try {
  let node: distributedKVStore.FieldNode | null = new distributedKVStore.FieldNode('root');
  let child1: distributedKVStore.FieldNode | null = new distributedKVStore.FieldNode('child1');
  let child2: distributedKVStore.FieldNode | null = new distributedKVStore.FieldNode('child2');
  let child3: distributedKVStore.FieldNode | null = new distributedKVStore.FieldNode('child3');
  node.appendChild(child1);
  node.appendChild(child2);
  node.appendChild(child3);
  console.info('appendNode ' + JSON.stringify(node));
  child1 = null;
  child2 = null;
  child3 = null;
  node = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to append child. Code: ${error.code}, message: ${error.message}`);
}

```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(name: string)
```

用于创建带有string字段FieldNode实例的构造函数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FieldNode-constructor(name: string)--><!--Device-FieldNode-constructor(name: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | FieldNode的值，不能为空，长度范围为1-64个字符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Parameter verification failed. |

## default

```TypeScript
default: string
```

表示FieldNode的默认值。default需传入type对应类型可解析的字符串字面量，确保内容类型与type字段类型一致。

**类型：** string

**起始版本：** 9

<!--Device-FieldNode-default: string--><!--Device-FieldNode-default: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## nullable

```TypeScript
set nullable(isnullable: boolean)
```

设置数据库字段是否为空.

**类型：** boolean

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FieldNode-set nullable(isnullable: boolean)--><!--Device-FieldNode-set nullable(isnullable: boolean)-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## type

```TypeScript
set type(type: number)
```

设置节点对应的数据类型。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FieldNode-set type(type: int)--><!--Device-FieldNode-set type(type: int)-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

