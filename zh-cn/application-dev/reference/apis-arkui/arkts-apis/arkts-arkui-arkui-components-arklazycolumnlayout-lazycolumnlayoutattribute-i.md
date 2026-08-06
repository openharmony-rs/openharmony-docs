# LazyColumnLayoutAttribute

定义懒列布局属性。

**继承/实现关系：** LazyColumnLayoutAttribute extends [CommonMethod](../../apis-na/arkts-apis/arkts-na-component/common-commonmethod-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface LazyColumnLayoutAttribute extends CommonMethod--><!--Device-unnamed-export declare interface LazyColumnLayoutAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
default alignItems(value: HorizontalAlign | undefined): this
```

设置行内容的水平对齐方式。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyColumnLayoutAttribute-default alignItems(value: HorizontalAlign | undefined): this--><!--Device-LazyColumnLayoutAttribute-default alignItems(value: HorizontalAlign | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 行内容的水平对齐。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：HorizontalAlign.Center。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## attributeModifier

```TypeScript
default attributeModifier(modifier: AttributeModifier<LazyColumnLayoutAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

设置属性修饰符。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyColumnLayoutAttribute-default attributeModifier(modifier: AttributeModifier<LazyColumnLayoutAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-LazyColumnLayoutAttribute-default attributeModifier(modifier: AttributeModifier<LazyColumnLayoutAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| AttributeModifier&lt;CommonMethod&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## footer

```TypeScript
default footer(builder: CustomBuilder | undefined): this
```

设置懒加载列布局的footer。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyColumnLayoutAttribute-default footer(builder: CustomBuilder | undefined): this--><!--Device-LazyColumnLayoutAttribute-default footer(builder: CustomBuilder | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | footer生成器函数\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传递undefined将移除footer。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## header

```TypeScript
default header(builder: CustomBuilder | undefined): this
```

设置懒加载列布局的header。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyColumnLayoutAttribute-default header(builder: CustomBuilder | undefined): this--><!--Device-LazyColumnLayoutAttribute-default header(builder: CustomBuilder | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | header生成器函数\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传递undefined将移除header。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onVisibleIndexesChange

```TypeScript
default onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): this
```

当子组件在可见区域的索引发生变化时触发。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyColumnLayoutAttribute-default onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): this--><!--Device-LazyColumnLayoutAttribute-default onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 回调函数，当可见区域中子组件的索引发生变化时触发.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传递undefined将取消注册回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setLazyColumnLayoutOptions

```TypeScript
default setLazyColumnLayoutOptions(): this
```

设置LazyColumnLayout选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyColumnLayoutAttribute-default setLazyColumnLayoutOptions(): this--><!--Device-LazyColumnLayoutAttribute-default setLazyColumnLayoutOptions(): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## space

```TypeScript
default space(space: LengthMetrics | undefined): this
```

行之间的间距。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyColumnLayoutAttribute-default space(space: LengthMetrics | undefined): this--><!--Device-LazyColumnLayoutAttribute-default space(space: LengthMetrics | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| space | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 行之间的间距。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值为0。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_范围：[0, +∞)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## sticky

```TypeScript
default sticky(sticky: StickyStyle | undefined): this
```

设置header和footer的吸顶吸底样式。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LazyColumnLayoutAttribute-default sticky(sticky: StickyStyle | undefined): this--><!--Device-LazyColumnLayoutAttribute-default sticky(sticky: StickyStyle | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sticky | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | header和footer的吸顶吸底样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

