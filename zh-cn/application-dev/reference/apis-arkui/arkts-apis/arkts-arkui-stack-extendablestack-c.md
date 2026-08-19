# ExtendableStack

Defines the Extendable Stack.

**继承/实现关系：** ExtendableStack implements StackAttribute

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare abstract class ExtendableStack--><!--Device-unnamed-export declare abstract class ExtendableStack-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
@ComponentBuilder
    static $_instantiate<T extends ExtendableStack>(
        factory: ConstructorT<T>,
        options?: StackOptions,
        content_?: CustomBuilder
    ): T
```

Constructor of Extendable Stack.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableStack-@ComponentBuilder    static $_instantiate<T extends ExtendableStack>(        factory: ConstructorT<T>,        options?: StackOptions,        content_?: CustomBuilder    ): T--><!--Device-ExtendableStack-@ComponentBuilder    static $_instantiate<T extends ExtendableStack>(        factory: ConstructorT<T>,        options?: StackOptions,        content_?: CustomBuilder    ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | [ConstructorT](../../apis-na/arkts-apis/arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| options | [StackOptions](arkts-arkui-stack-stackoptions-i.md) | 否 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
@Builder
    static _instantiateImpl<T extends ExtendableStack>(
        styles: CustomBuilderT<T>,
        factory: ConstructorT<T>,
        content_?: CustomBuilder
    ): void
```

Entry of Extendable Stack.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableStack-@Builder    static _instantiateImpl<T extends ExtendableStack>(        styles: CustomBuilderT<T>,        factory: ConstructorT<T>,        content_?: CustomBuilder    ): void--><!--Device-ExtendableStack-@Builder    static _instantiateImpl<T extends ExtendableStack>(        styles: CustomBuilderT<T>,        factory: ConstructorT<T>,        content_?: CustomBuilder    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | CustomBuilderT&lt;T&gt; | 是 |  |
| factory | [ConstructorT](../../apis-na/arkts-apis/arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| content_ | CustomBuilder | 否 |  |

## setStackOptions

```TypeScript
public setStackOptions(options?: StackOptions): this
```

Set the Stack Options.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableStack-public setStackOptions(options?: StackOptions): this--><!--Device-ExtendableStack-public setStackOptions(options?: StackOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [StackOptions](arkts-arkui-stack-stackoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

