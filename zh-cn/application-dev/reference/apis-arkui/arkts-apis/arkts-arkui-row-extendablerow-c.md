# ExtendableRow

Defines the Extendable Row.

**继承/实现关系：** ExtendableRow implements RowAttribute

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare abstract class ExtendableRow--><!--Device-unnamed-export declare abstract class ExtendableRow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
@ComponentBuilder
    static $_instantiate<T extends ExtendableRow>(
        factory: ConstructorT<T>,
        options?: RowOptions | RowOptionsV2,
        content_?: CustomBuilder
    ): T
```

Constructor of Extendable Row.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableRow-@ComponentBuilder    static $_instantiate<T extends ExtendableRow>(        factory: ConstructorT<T>,        options?: RowOptions | RowOptionsV2,        content_?: CustomBuilder    ): T--><!--Device-ExtendableRow-@ComponentBuilder    static $_instantiate<T extends ExtendableRow>(        factory: ConstructorT<T>,        options?: RowOptions | RowOptionsV2,        content_?: CustomBuilder    ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | [ConstructorT](../../apis-na/arkts-apis/arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| options | [RowOptions](arkts-arkui-row-rowoptions-i.md) \| [RowOptionsV2](arkts-arkui-row-rowoptionsv2-i.md) | 否 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
@Builder
    static _instantiateImpl<T extends ExtendableRow>(
        styles: CustomBuilderT<T>,
        factory: ConstructorT<T>,
        content_?: CustomBuilder
    ): void
```

Entry of Extendable Row.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableRow-@Builder    static _instantiateImpl<T extends ExtendableRow>(        styles: CustomBuilderT<T>,        factory: ConstructorT<T>,        content_?: CustomBuilder    ): void--><!--Device-ExtendableRow-@Builder    static _instantiateImpl<T extends ExtendableRow>(        styles: CustomBuilderT<T>,        factory: ConstructorT<T>,        content_?: CustomBuilder    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | CustomBuilderT&lt;T&gt; | 是 |  |
| factory | [ConstructorT](../../apis-na/arkts-apis/arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| content_ | CustomBuilder | 否 |  |

## setRowOptions

```TypeScript
public setRowOptions(options?: RowOptions | RowOptionsV2): this
```

Set the Row Options.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableRow-public setRowOptions(options?: RowOptions | RowOptionsV2): this--><!--Device-ExtendableRow-public setRowOptions(options?: RowOptions | RowOptionsV2): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RowOptions](arkts-arkui-row-rowoptions-i.md) \| [RowOptionsV2](arkts-arkui-row-rowoptionsv2-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

