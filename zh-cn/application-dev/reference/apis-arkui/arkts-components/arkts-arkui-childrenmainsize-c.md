# ChildrenMainSize

维护List组件或ListItemGroup组件的子组件在主轴方向的大小信息，仅支持一对一绑定到List组件或ListItemGroup组件。 > **说明：** > > - 提供的主轴方向大小信息必须与子组件实际在主轴方向的大小一致，子组件在主轴方向大小变化或者增删子组件时都必须通过ChildrenMainSize对象方法通知List组件或ListItemGroup组件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare class ChildrenMainSize--><!--Device-unnamed-declare class ChildrenMainSize-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(childDefaultSize: number)
```

ChildrenMainSize有参构造函数。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChildrenMainSize-constructor(childDefaultSize: number)--><!--Device-ChildrenMainSize-constructor(childDefaultSize: number)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| childDefaultSize | number | 是 | 子组件在主轴方向的默认大小。&lt;br/&gt;单位：vp&lt;br/&gt;**说明：** &lt;br/&gt;必须是有限的非负数值，否则抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## splice

```TypeScript
splice(start: number, deleteCount?: number, childrenSize?: Array<number>): void
```

批量增删改子组件在主轴方向的大小信息。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChildrenMainSize-splice(start: number, deleteCount?: number, childrenSize?: Array<number>): void--><!--Device-ChildrenMainSize-splice(start: number, deleteCount?: number, childrenSize?: Array<number>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 从0开始计算的索引值，表示要开始修改子组件在主轴方向大小信息的位置。&lt;br/&gt;**说明：** &lt;br/&gt;1. 必须是有限的非负数值，否则抛出异常。&lt;br/&gt;2. 非整数会被截断为 整数。&lt;br/&gt;3. 超过最大索引值不生效。&lt;br/&gt;取值范围：[0, +∞) |
| deleteCount | number | 否 | 从start开始删除的大小信息的数量。&lt;br/&gt;**说明：** &lt;br/&gt;1. 必须是有限的非负数值，否则处理为0。&lt;br/&gt;2. 非整数会被截断为整数。&lt;br /&gt;3. start + deleteCount - 1可以超过最大索引值，会删除索引值start开始之后的所有子组件的大小信息。&lt;br/&gt;默认值为+∞。 &lt;br/&gt;取值范围：[0, +∞) |
| childrenSize | Array&lt;number&gt; | 否 | 要在start位置插入的所有子组件的主轴方向的大小。&lt;br/&gt;Array中各个数值单位：vp &lt;br/&gt;**说明：** &lt;br/&gt;1.数组中数值如 果是有限的非负值，则认为是指定的大小，后续不随默认大小的变化而变化。&lt;br/&gt;2. 数组中数值如果不是有限的非负值，会被处理成默认大小，后续会随默认大小的变化而变化。&lt;br/&gt;默认值为空数组。 &lt;br/&gt;取值范围： [0, +∞) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

## update

```TypeScript
update(index: number, childSize: number): void
```

修改指定索引值对应的子组件的主轴方向的大小信息。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ChildrenMainSize-update(index: number, childSize: number): void--><!--Device-ChildrenMainSize-update(index: number, childSize: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 从0开始计算的索引值，表示要开始修改子组件在主轴方向大小信息的位置。&lt;br/&gt;**说明：** &lt;br/&gt;1. 必须是有限的非负数值，否则抛出异常。&lt;br/&gt;2. 非整数会被截断为 整数。&lt;br/&gt;3. 超过最大索引值不生效。 &lt;br/&gt;取值范围：[0, +∞) |
| childSize | number | 是 | 要更新成的大小。&lt;br/&gt;单位：vp &lt;br/&gt;**说明：** &lt;br/&gt;1.数值如果是有限的非负值，则认为是指定的大小，后续不随默认大小的变化而变化。&lt;br/&gt;2. 数 值如果不是有限的非负值，会被处理成默认大小，后续会随默认大小的变化而变化。 &lt;br/&gt;取值范围：[0, +∞) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Mandatory parameters are left unspecified. &lt;br&gt; 2. Incorrect parameters types. &lt;br&gt; 3. Parameter verification failed. |

