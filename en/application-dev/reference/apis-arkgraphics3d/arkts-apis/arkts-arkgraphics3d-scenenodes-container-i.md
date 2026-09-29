# Container

```TypeScript
export interface Container<T>
```

Container for defining scene nodes. It provides a way to group scene nodes into a hierarchy.

@interface Container

**Since:** 12

<!--Device-unnamed-export interface Container<T>--><!--Device-unnamed-export interface Container<T>-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## append

```TypeScript
append(item: T): void
```

Appends a node to the container.

**Since:** 12

<!--Device-Container-append(item: T): void--><!--Device-Container-append(item: T): void-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| item | T | Yes | Object of the T type. |

## clear

```TypeScript
clear(): void
```

Clears all nodes in the container.

**Since:** 12

<!--Device-Container-clear(): void--><!--Device-Container-clear(): void-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## count

```TypeScript
count(): number
```

Obtains the number of nodes in the container.

**Since:** 12

<!--Device-Container-count(): int--><!--Device-Container-count(): int-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of nodes in the container. The value is a non-negative integer. |

## get

```TypeScript
get(index: number): T | null
```

Obtains a node of a given index. If no node is obtained, null is returned.

**Since:** 12

<!--Device-Container-get(index: int): T | null--><!--Device-Container-get(index: int): T | null-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the node. The value is an integer greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| T &#124; null | Object obtained. If no object is obtained, null is returned. |

## insertAfter

```TypeScript
insertAfter(item: T, sibling: T | null): void
```

Inserts the object after the sibling node.

**Since:** 12

<!--Device-Container-insertAfter(item: T, sibling: T | null): void--><!--Device-Container-insertAfter(item: T, sibling: T | null): void-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| item | T | Yes | Node to be inserted. |
| sibling | T &#124; null | Yes | Sibling node. |

## remove

```TypeScript
remove(item: T): void
```

Removes a node.

**Since:** 12

<!--Device-Container-remove(item: T): void--><!--Device-Container-remove(item: T): void-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| item | T | Yes | Node to remove. |
