# LazyColumnLayoutAttribute

定义懒列布局属性。

**继承/实现关系：** LazyColumnLayoutAttribute extends CommonMethod

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface LazyColumnLayoutAttribute--><!--Device-unnamed-export declare interface LazyColumnLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## alignItems

```TypeScript
alignItems(value: HorizontalAlign | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-LazyColumnLayoutAttribute-alignItems(value: HorizontalAlign | undefined): this--><!--Device-LazyColumnLayoutAttribute-alignItems(value: HorizontalAlign | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [HorizontalAlign](arkts-na-enums-horizontalalign-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<LazyColumnLayoutAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-LazyColumnLayoutAttribute-attributeModifier(modifier: AttributeModifier<LazyColumnLayoutAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-LazyColumnLayoutAttribute-attributeModifier(modifier: AttributeModifier<LazyColumnLayoutAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](arkts-na-common-attributemodifier-i.md)&lt;[LazyColumnLayoutAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md)&gt; \| [AttributeModifier](arkts-na-common-attributemodifier-i.md)&lt;[CommonMethod](arkts-na-common-commonmethod-i.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-LazyColumnLayoutAttribute-footer(builder: CustomBuilder | undefined): this--><!--Device-LazyColumnLayoutAttribute-footer(builder: CustomBuilder | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## header

```TypeScript
header(builder: CustomBuilder | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-LazyColumnLayoutAttribute-header(builder: CustomBuilder | undefined): this--><!--Device-LazyColumnLayoutAttribute-header(builder: CustomBuilder | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-LazyColumnLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): this--><!--Device-LazyColumnLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnVisibleIndexesChangeCallback](arkts-na-onvisibleindexeschangecallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setLazyColumnLayoutOptions

```TypeScript
setLazyColumnLayoutOptions(): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-LazyColumnLayoutAttribute-setLazyColumnLayoutOptions(): this--><!--Device-LazyColumnLayoutAttribute-setLazyColumnLayoutOptions(): this-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## space

```TypeScript
space(space: LengthMetrics | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-LazyColumnLayoutAttribute-space(space: LengthMetrics | undefined): this--><!--Device-LazyColumnLayoutAttribute-space(space: LengthMetrics | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| space | [LengthMetrics](../../apis-arkui/arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-LazyColumnLayoutAttribute-sticky(sticky: StickyStyle | undefined): this--><!--Device-LazyColumnLayoutAttribute-sticky(sticky: StickyStyle | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sticky | [StickyStyle](arkts-na-list-stickystyle-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

设置属性修饰符。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyColumnLayoutAttribute-default--><!--Device-LazyColumnLayoutAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

