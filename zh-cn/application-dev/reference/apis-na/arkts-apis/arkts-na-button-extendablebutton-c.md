# ExtendableButton

Defines the Extendable Button.

**继承/实现关系：** ExtendableButton implements [ButtonAttribute](arkts-na-button-buttonattribute-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare abstract class ExtendableButton--><!--Device-unnamed-export declare abstract class ExtendableButton-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
@ComponentBuilder
    static $_instantiate<T extends ExtendableButton>(
        factory: ConstructorT<T>, 
        label: ResourceStr, 
        options?: ButtonOptions, 
        content_?: CustomBuilder
    ): T
```

Constructor of Extendable Button.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableButton-@ComponentBuilder    static $_instantiate<T extends ExtendableButton>(        factory: ConstructorT<T>,         label: ResourceStr,         options?: ButtonOptions,         content_?: CustomBuilder    ): T--><!--Device-ExtendableButton-@ComponentBuilder    static $_instantiate<T extends ExtendableButton>(        factory: ConstructorT<T>,         label: ResourceStr,         options?: ButtonOptions,         content_?: CustomBuilder    ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | [ConstructorT](arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| label | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) | 是 |  |
| options | [ButtonOptions](arkts-na-button-buttonoptions-i.md) | 否 | Button Component Options |
| content_ | CustomBuilder | 否 | subcomponent trailing closure |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## $_instantiate

```TypeScript
@ComponentBuilder
    static $_instantiate<T extends ExtendableButton>(
        factory: ConstructorT<T>, 
        options?: ButtonOptions,
        content_?: CustomBuilder
    ): T
```

Constructor of Extendable Button.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableButton-@ComponentBuilder    static $_instantiate<T extends ExtendableButton>(        factory: ConstructorT<T>,         options?: ButtonOptions,        content_?: CustomBuilder    ): T--><!--Device-ExtendableButton-@ComponentBuilder    static $_instantiate<T extends ExtendableButton>(        factory: ConstructorT<T>,         options?: ButtonOptions,        content_?: CustomBuilder    ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | [ConstructorT](arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| options | [ButtonOptions](arkts-na-button-buttonoptions-i.md) | 否 |  |
| content_ | CustomBuilder | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
@Builder
    static _instantiateImpl<T extends ExtendableButton>(
        styles: CustomBuilderT<T>, 
        factory: ConstructorT<T>, 
        content_?: CustomBuilder
    ): void
```

Entry of Extendable Button.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableButton-@Builder    static _instantiateImpl<T extends ExtendableButton>(        styles: CustomBuilderT<T>,         factory: ConstructorT<T>,         content_?: CustomBuilder    ): void--><!--Device-ExtendableButton-@Builder    static _instantiateImpl<T extends ExtendableButton>(        styles: CustomBuilderT<T>,         factory: ConstructorT<T>,         content_?: CustomBuilder    ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | CustomBuilderT&lt;T&gt; | 是 |  |
| factory | [ConstructorT](arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| content_ | CustomBuilder | 否 |  |

## setButtonOptions

```TypeScript
public setButtonOptions(
        label: ResourceStr, 
        options?: ButtonOptions
    ): this
```

Set the Button Options.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableButton-public setButtonOptions(        label: ResourceStr,         options?: ButtonOptions    ): this--><!--Device-ExtendableButton-public setButtonOptions(        label: ResourceStr,         options?: ButtonOptions    ): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| label | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) | 是 |  |
| options | [ButtonOptions](arkts-na-button-buttonoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setButtonOptions

```TypeScript
public setButtonOptions(options?: ButtonOptions): this
```

Set the Button Options.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableButton-public setButtonOptions(options?: ButtonOptions): this--><!--Device-ExtendableButton-public setButtonOptions(options?: ButtonOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ButtonOptions](arkts-na-button-buttonoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

