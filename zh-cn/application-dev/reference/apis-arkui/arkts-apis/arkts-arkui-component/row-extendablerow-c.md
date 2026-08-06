# ExtendableRow

Defines the Extendable Row.

**继承/实现关系：** ExtendableRow implements [RowAttribute](row-rowattribute-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare abstract class ExtendableRow implements RowAttribute--><!--Device-unnamed-export declare abstract class ExtendableRow implements RowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
static $_instantiate<T extends ExtendableRow>(
        factory: ConstructorT<T>,
        options?: RowOptions | RowOptionsV2,
        content_?: CustomBuilder
    ): T
```

Constructor of Extendable Row.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableRow-static $_instantiate<T extends ExtendableRow>(        factory: ConstructorT<T>,        options?: RowOptions | RowOptionsV2,        content_?: CustomBuilder    ): T--><!--Device-ExtendableRow-static $_instantiate<T extends ExtendableRow>(        factory: ConstructorT<T>,        options?: RowOptions | RowOptionsV2,        content_?: CustomBuilder    ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| RowOptionsV2 | 否 |  |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
static _instantiateImpl<T extends ExtendableRow>(
        styles: CustomBuilderT<T>,
        factory: ConstructorT<T>,
        content_?: CustomBuilder
    ): void
```

Entry of Extendable Row.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableRow-static _instantiateImpl<T extends ExtendableRow>(        styles: CustomBuilderT<T>,        factory: ConstructorT<T>,        content_?: CustomBuilder    ): void--><!--Device-ExtendableRow-static _instantiateImpl<T extends ExtendableRow>(        styles: CustomBuilderT<T>,        factory: ConstructorT<T>,        content_?: CustomBuilder    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

## setRowOptions

```TypeScript
public setRowOptions(options?: RowOptions | RowOptionsV2): this
```

Set the Row Options.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableRow-public setRowOptions(options?: RowOptions | RowOptionsV2): this--><!--Device-ExtendableRow-public setRowOptions(options?: RowOptions | RowOptionsV2): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| RowOptionsV2 | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

