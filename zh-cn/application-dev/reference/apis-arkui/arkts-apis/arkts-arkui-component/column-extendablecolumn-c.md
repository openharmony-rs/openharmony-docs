# ExtendableColumn

Defines the Extendable Column.

**继承/实现关系：** ExtendableColumn implements [ColumnAttribute](column-columnattribute-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare abstract class ExtendableColumn implements ColumnAttribute--><!--Device-unnamed-export declare abstract class ExtendableColumn implements ColumnAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
static $_instantiate<T extends ExtendableColumn>(
        factory: ConstructorT<T>, 
        options?: ColumnOptions | ColumnOptionsV2, 
        content_?: CustomBuilder
    ): T
```

Constructor of Extendable Column.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableColumn-static $_instantiate<T extends ExtendableColumn>(        factory: ConstructorT<T>,         options?: ColumnOptions | ColumnOptionsV2,         content_?: CustomBuilder    ): T--><!--Device-ExtendableColumn-static $_instantiate<T extends ExtendableColumn>(        factory: ConstructorT<T>,         options?: ColumnOptions | ColumnOptionsV2,         content_?: CustomBuilder    ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ColumnOptionsV2 | 否 |  |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
static _instantiateImpl<T extends ExtendableColumn>(
        styles: CustomBuilderT<T>, 
        factory: ConstructorT<T>, 
        content_?: CustomBuilder
    ): void
```

Entry of Extendable Column.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableColumn-static _instantiateImpl<T extends ExtendableColumn>(        styles: CustomBuilderT<T>,         factory: ConstructorT<T>,         content_?: CustomBuilder    ): void--><!--Device-ExtendableColumn-static _instantiateImpl<T extends ExtendableColumn>(        styles: CustomBuilderT<T>,         factory: ConstructorT<T>,         content_?: CustomBuilder    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| content\_ | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

## setColumnOptions

```TypeScript
public setColumnOptions(options?: ColumnOptions | ColumnOptionsV2): this
```

Set the Column Options.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableColumn-public setColumnOptions(options?: ColumnOptions | ColumnOptionsV2): this--><!--Device-ExtendableColumn-public setColumnOptions(options?: ColumnOptions | ColumnOptionsV2): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ColumnOptionsV2 | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

