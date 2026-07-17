# RepeatAttribute

除支持[拖拽排序](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)属性外，还支持以下属性。

**继承/实现关系：** RepeatAttribute extends [DynamicNode<RepeatAttribute<T>>](DynamicNode<RepeatAttribute<T>>)

**起始版本：** 12

<!--Device-unnamed-declare class RepeatAttribute<T> extends DynamicNode<RepeatAttribute<T>>--><!--Device-unnamed-declare class RepeatAttribute<T> extends DynamicNode<RepeatAttribute<T>>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## each

```TypeScript
each(itemGenerator: (repeatItem: RepeatItem<T>) => void): RepeatAttribute<T>
```

组件生成函数。当所有[`.template()`](../../../../reference/apis-arkui/arkui-ts/ts-rendering-control-repeat.md#template)的type和[`.templateId()`](../../../../reference/apis-arkui/arkui-ts/ts-rendering-control-repeat.md#templateid)返回值不匹配（即当前item不适用任何template定义的样式）时，将使用`.each()`处理数据项。

> **说明**  
>  
> - `each`属性必须有，否则运行时会报错。  
>  
> - `itemGenerator`的参数为`RepeatItem`，该参数将`item`和`index`结合到了一起，请勿将`RepeatItem`参数拆开使用。  
>  
> - 该接口不支持在[attributeModifier](../arkts-components/arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-RepeatAttribute-each(itemGenerator: (repeatItem: RepeatItem<T>) => void): RepeatAttribute<T>--><!--Device-RepeatAttribute-each(itemGenerator: (repeatItem: RepeatItem<T>) => void): RepeatAttribute<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemGenerator | (repeatItem: RepeatItem<T>) => void | 是 | 组件生成函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RepeatAttribute](arkts-arkui-repeat-repeatattribute-c.md)<T> | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

## key

```TypeScript
key(keyGenerator: (item: T, index: number) => string): RepeatAttribute<T>
```

键值生成函数。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](../arkts-components/arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-RepeatAttribute-key(keyGenerator: (item: T, index: number) => string): RepeatAttribute<T>--><!--Device-RepeatAttribute-key(keyGenerator: (item: T, index: number) => string): RepeatAttribute<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyGenerator | (item: T, index: number) => string | 是 | 键值生成函数。<br/>item：`arr`数组中的数据项，可选。<br/>index：`arr`数组中的数据项索引，可选。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RepeatAttribute](arkts-arkui-repeat-repeatattribute-c.md)<T> | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@form@atomicservice |

## template

```TypeScript
template(type: string, itemBuilder: RepeatItemBuilder<T>, templateOptions?: TemplateOptions): RepeatAttribute<T>
```

由template type渲染对应的template子组件。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](../arkts-components/arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RepeatAttribute-template(type: string, itemBuilder: RepeatItemBuilder<T>, templateOptions?: TemplateOptions): RepeatAttribute<T>--><!--Device-RepeatAttribute-template(type: string, itemBuilder: RepeatItemBuilder<T>, templateOptions?: TemplateOptions): RepeatAttribute<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 当前模板类型。 |
| itemBuilder | [RepeatItemBuilder](arkts-arkui-repeatitembuilder-t.md)<T> | 是 | 组件生成函数。 |
| templateOptions | [TemplateOptions](arkts-arkui-repeat-templateoptions-i.md) | 否 | 当前模板配置项。<br/>默认值为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RepeatAttribute](arkts-arkui-repeat-repeatattribute-c.md)<T> | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## templateId

```TypeScript
templateId(typedFunc: TemplateTypedFunc<T>): RepeatAttribute<T>
```

为当前数据项分配template type。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](../arkts-components/arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RepeatAttribute-templateId(typedFunc: TemplateTypedFunc<T>): RepeatAttribute<T>--><!--Device-RepeatAttribute-templateId(typedFunc: TemplateTypedFunc<T>): RepeatAttribute<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedFunc | [TemplateTypedFunc](arkts-arkui-templatetypedfunc-t.md)<T> | 是 | 生成当前数据项对应的template type。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RepeatAttribute](arkts-arkui-repeat-repeatattribute-c.md)<T> | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## virtualScroll

```TypeScript
virtualScroll(virtualScrollOptions?: VirtualScrollOptions): RepeatAttribute<T>
```

`Repeat`开启虚拟滚动。

> **说明：**  
>  
> 该接口不支持在[attributeModifier](../arkts-components/arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RepeatAttribute-virtualScroll(virtualScrollOptions?: VirtualScrollOptions): RepeatAttribute<T>--><!--Device-RepeatAttribute-virtualScroll(virtualScrollOptions?: VirtualScrollOptions): RepeatAttribute<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| virtualScrollOptions | [VirtualScrollOptions](arkts-arkui-repeat-virtualscrolloptions-i.md) | 否 | 虚拟滚动配置项。<br/>默认值为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RepeatAttribute](arkts-arkui-repeat-repeatattribute-c.md)<T> | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

