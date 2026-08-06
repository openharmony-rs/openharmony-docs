# PromptOptionsV2

Configuration parameter of ExceptionPromptV2. Use @ObservedV2 and @Trace to support deep observation and dynamic refresh of properties.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class PromptOptionsV2--><!--Device-unnamed-export declare class PromptOptionsV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config?: PromptOptionsV2Config)
```

Constructor of PromptOptionsV2.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-constructor(config?: PromptOptionsV2Config)--><!--Device-PromptOptionsV2-constructor(config?: PromptOptionsV2Config)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Configuration information of ExceptionPromptV2 |

## actionText

```TypeScript
public actionText?: ResourceStr
```

Text of the icon on the right of the ExceptionPromptV2. If this parameter is not set or is set to undefined, the text is not displayed.

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-public actionText?: ResourceStr--><!--Device-PromptOptionsV2-public actionText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
public icon?: ResourceStr
```

Icon style of the ExceptionPromptV2. If this parameter is not set or is set to undefined, the icon is not displayed.

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-public icon?: ResourceStr--><!--Device-PromptOptionsV2-public icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isShown

```TypeScript
public isShown?: boolean
```

Whether the ExceptionPromptV2 is displayed. true: The exception prompt is displayed. false: The exception prompt is hidden. Default value: false.

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-public isShown?: boolean--><!--Device-PromptOptionsV2-public isShown?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marginTop

```TypeScript
public marginTop: Dimension
```

Top margin of the ExceptionPromptV2. Distance from the top to the content area of ExceptionPromptV2.

**类型：** Dimension

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-public marginTop: Dimension--><!--Device-PromptOptionsV2-public marginTop: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marginType

```TypeScript
public marginType: MarginTypeV2
```

Margin Type of ExceptionPromptV2. Margin from the content area to the edge of the container.

**类型：** MarginTypeV2

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-public marginType: MarginTypeV2--><!--Device-PromptOptionsV2-public marginType: MarginTypeV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
public symbolStyle?: SymbolGlyphModifier
```

Symbol icon style of the ExceptionPromptV2, which has higher priority than icon. If this parameter is not set or is set to undefined, the symbol icon is not displayed.

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-public symbolStyle?: SymbolGlyphModifier--><!--Device-PromptOptionsV2-public symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tip

```TypeScript
public tip?: ResourceStr
```

Text content of the ExceptionPromptV2. By default, the following text resources are provided: 1. ohos\_network\_not\_connected: displayed when no Internet connection. 2. ohos\_network\_connected\_unstable: displayed when the Internet connection is unstable. 3. ohos\_unstable\_connect\_server: displayed when the server fails to be connected. 4. ohos\_custom\_network\_tips\_left: displayed when an Internet connection is available but the location fails to be obtained. If this parameter is not set or is set to undefined, the text content is not displayed.

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PromptOptionsV2-public tip?: ResourceStr--><!--Device-PromptOptionsV2-public tip?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

