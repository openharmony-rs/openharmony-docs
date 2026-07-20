# Container

定义场景对象容器.

**起始版本：** 12

<!--Device-unnamed-export interface Container<T>--><!--Device-unnamed-export interface Container<T>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

<a id="append"></a>
## append

```TypeScript
append(item: T): void
```

将项目追加到容器.

**起始版本：** 12

<!--Device-Container-append(item: T): void--><!--Device-Container-append(item: T): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | T | 是 | 要追加到容器末尾的项目 |

<a id="clear"></a>
## clear

```TypeScript
clear(): void
```

清空所有子节点.

**起始版本：** 12

<!--Device-Container-clear(): void--><!--Device-Container-clear(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

<a id="count"></a>
## count

```TypeScript
count(): number
```

返回容器中的项目数量.

**起始版本：** 12

<!--Device-Container-count(): int--><!--Device-Container-count(): int-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 容器的数量 |

<a id="get"></a>
## get

```TypeScript
get(index: number): T | null
```

从容器的子节点列表中返回给定索引的子节点.

**起始版本：** 12

<!--Device-Container-get(index: int): T | null--><!--Device-Container-get(index: int): T | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 要返回的子节点的索引 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回由索引指定的项目 |

<a id="insertafter"></a>
## insertAfter

```TypeScript
insertAfter(item: T, sibling: T | null): void
```

插入项目.

**起始版本：** 12

<!--Device-Container-insertAfter(item: T, sibling: T | null): void--><!--Device-Container-insertAfter(item: T, sibling: T | null): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | T | 是 | 要插入到容器的项目 |
| sibling | T \| null | 是 | 在此项目后插入，如果sibling为null则插入到头部 |

<a id="remove"></a>
## remove

```TypeScript
remove(item: T): void
```

从容器的子节点中移除项目.

**起始版本：** 12

<!--Device-Container-remove(item: T): void--><!--Device-Container-remove(item: T): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | T | 是 | 要移除的项目 |

