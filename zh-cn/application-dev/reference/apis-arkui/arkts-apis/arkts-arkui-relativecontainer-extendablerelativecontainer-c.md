# ExtendableRelativeContainer

Defines the Extendable RelativeContainer.

**继承/实现关系：** ExtendableRelativeContainer implements RelativeContainerAttribute

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare abstract class ExtendableRelativeContainer--><!--Device-unnamed-export declare abstract class ExtendableRelativeContainer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
@ComponentBuilder
    static $_instantiate<T extends ExtendableRelativeContainer>(
        factory: ConstructorT<T>,
        content_?: CustomBuilder
    ): T
```

Constructor of Extendable RelativeContainer.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableRelativeContainer-@ComponentBuilder    static $_instantiate<T extends ExtendableRelativeContainer>(        factory: ConstructorT<T>,        content_?: CustomBuilder    ): T--><!--Device-ExtendableRelativeContainer-@ComponentBuilder    static $_instantiate<T extends ExtendableRelativeContainer>(        factory: ConstructorT<T>,        content_?: CustomBuilder    ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | [ConstructorT](../../apis-na/arkts-apis/arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
@Builder
    static _instantiateImpl<T extends ExtendableRelativeContainer>(
        styles: CustomBuilderT<T>,
        factory: ConstructorT<T>,
        content_?: CustomBuilder
    ): void
```

Entry of Extendable RelativeContainer.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableRelativeContainer-@Builder    static _instantiateImpl<T extends ExtendableRelativeContainer>(        styles: CustomBuilderT<T>,        factory: ConstructorT<T>,        content_?: CustomBuilder    ): void--><!--Device-ExtendableRelativeContainer-@Builder    static _instantiateImpl<T extends ExtendableRelativeContainer>(        styles: CustomBuilderT<T>,        factory: ConstructorT<T>,        content_?: CustomBuilder    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | CustomBuilderT&lt;T&gt; | 是 |  |
| factory | [ConstructorT](../../apis-na/arkts-apis/arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| content_ | CustomBuilder | 否 |  |

## setRelativeContainerOptions

```TypeScript
public setRelativeContainerOptions(): this
```

Set the RelativeContainer Options.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableRelativeContainer-public setRelativeContainerOptions(): this--><!--Device-ExtendableRelativeContainer-public setRelativeContainerOptions(): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

