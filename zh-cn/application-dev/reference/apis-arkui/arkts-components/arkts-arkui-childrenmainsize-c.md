# ChildrenMainSize

Indicates children main size.

**起始版本：** 12

<!--Device-unnamed-declare class ChildrenMainSize--><!--Device-unnamed-declare class ChildrenMainSize-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor(childDefaultSize: number)
```

Creates an instance of ChildrenMainSize.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChildrenMainSize-constructor(childDefaultSize: number)--><!--Device-ChildrenMainSize-constructor(childDefaultSize: number)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| childDefaultSize | number | 是 | default main size, in vp. If the main axis is vertical, it indicates height.If the main axis is horizontal, it indicates width. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

<a id="splice"></a>
## splice

```TypeScript
splice(start: number, deleteCount?: number, childrenSize?: Array<number>): void
```

Changes children main size by removing or replacing existing elements and/or adding new elements in place.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChildrenMainSize-splice(start: number, deleteCount?: number, childrenSize?: Array<number>): void--><!--Device-ChildrenMainSize-splice(start: number, deleteCount?: number, childrenSize?: Array<number>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | Zero-based index at which to start changing the children main size. |
| deleteCount | number | 否 | Indicating the number of children main size to remove from start. |
| childrenSize | Array&lt;number&gt; | 否 | Add the new children main size, beginning from start. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

<a id="update"></a>
## update

```TypeScript
update(index: number, childSize: number): void
```

Updates main size for specified child.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChildrenMainSize-update(index: number, childSize: number): void--><!--Device-ChildrenMainSize-update(index: number, childSize: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | index of child to be updated. |
| childSize | number | 是 | new section options. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |

## childDefaultSize

```TypeScript
get childDefaultSize(): number
```

Get default size

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChildrenMainSize-get childDefaultSize(): number--><!--Device-ChildrenMainSize-get childDefaultSize(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

