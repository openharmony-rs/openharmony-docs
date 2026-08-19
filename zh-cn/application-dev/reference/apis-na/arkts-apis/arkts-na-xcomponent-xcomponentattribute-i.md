# XComponentAttribute

定义XComponent属性。

**继承/实现关系：** XComponentAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface XComponentAttribute--><!--Device-unnamed-export declare interface XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<XComponentAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-XComponentAttribute-attributeModifier(modifier: AttributeModifier<XComponentAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-XComponentAttribute-attributeModifier(modifier: AttributeModifier<XComponentAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[XComponentAttribute](arkts-na-xcomponent-xcomponentattribute-i.md)&gt; \| [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-XComponentAttribute-enableAnalyzer(enable: boolean | undefined): this--><!--Device-XComponentAttribute-enableAnalyzer(enable: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableSecure

```TypeScript
enableSecure(isSecure: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-XComponentAttribute-enableSecure(isSecure: boolean | undefined): this--><!--Device-XComponentAttribute-enableSecure(isSecure: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSecure | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableTransparentLayer

```TypeScript
enableTransparentLayer(enabled: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-XComponentAttribute-enableTransparentLayer(enabled: boolean | undefined): this--><!--Device-XComponentAttribute-enableTransparentLayer(enabled: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hdrBrightness

```TypeScript
hdrBrightness(brightness: double | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-XComponentAttribute-hdrBrightness(brightness: double | undefined): this--><!--Device-XComponentAttribute-hdrBrightness(brightness: double | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brightness | double \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## hdrBrightness

```TypeScript
hdrBrightness(brightness: double | undefined, type?: HdrType): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-XComponentAttribute-hdrBrightness(brightness: double | undefined, type?: HdrType): this--><!--Device-XComponentAttribute-hdrBrightness(brightness: double | undefined, type?: HdrType): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brightness | double \| undefined | 是 |  |
| type | [HdrType](arkts-na-xcomponent-hdrtype-e.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onDestroy

```TypeScript
onDestroy(event: VoidCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-XComponentAttribute-onDestroy(event: VoidCallback | undefined): this--><!--Device-XComponentAttribute-onDestroy(event: VoidCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onLoad

```TypeScript
onLoad(callback: VoidCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-XComponentAttribute-onLoad(callback: VoidCallback | undefined): this--><!--Device-XComponentAttribute-onLoad(callback: VoidCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setXComponentOptions

```TypeScript
setXComponentOptions(params: XComponentParameters | XComponentOptions | NativeXComponentParameters): this
```

设置XComponent选项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentAttribute-setXComponentOptions(params: XComponentParameters | XComponentOptions | NativeXComponentParameters): this--><!--Device-XComponentAttribute-setXComponentOptions(params: XComponentParameters | XComponentOptions | NativeXComponentParameters): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [XComponentParameters](arkts-na-xcomponent-xcomponentparameters-i.md) \| [XComponentOptions](arkts-na-xcomponent-xcomponentoptions-i.md) \| [NativeXComponentParameters](arkts-na-xcomponent-nativexcomponentparameters-i.md) | 是 | 用于创建XComponent的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | XComponentAttribute实例 |

## default

```TypeScript
default
```

设置XComponent组件的属性修改器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentAttribute-default--><!--Device-XComponentAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

