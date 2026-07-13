# Repeat属性/事件

除支持[拖拽排序](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)属性外，还支持以下属性。

**继承/实现关系：** RepeatAttribute extends [DynamicNode<RepeatAttribute<T>>](DynamicNode<RepeatAttribute<T>>)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## each

```TypeScript
each(itemGenerator: (repeatItem: RepeatItem<T>) => void)
```

组件生成函数。当所有[`.template()`](../../../../reference/apis-arkui/arkui-ts/ts-rendering-control-repeat.md#template)的type和
[`.templateId()`](../../../../reference/apis-arkui/arkui-ts/ts-rendering-control-repeat.md#templateid)返回值不匹配（即当前item不
适用任何template定义的样式）时，将使用`.each()`处理数据项。

> **说明**
>
> - `each`属性必须有，否则运行时会报错。
>
> - `itemGenerator`的参数为`RepeatItem`，该参数将`item`和`index`结合到了一起，请勿将`RepeatItem`参数拆开使用。
>
> - 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemGenerator | (repeatItem: RepeatItem&lt;T&gt;) =&gt; void | 是 | 组件生成函数。 |

## key

```TypeScript
key(keyGenerator: (item: T, index: number) => string)
```

键值生成函数。

> **说明：**
>
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyGenerator | (item: T, index: number) =&gt; string | 是 | 键值生成函数。<br/>item：`arr`数组中的数据项，可选。<br/>index：`arr`数组中的数据项索引，可选。 |

## template

```TypeScript
template(type: string, itemBuilder: RepeatItemBuilder<T>, templateOptions?: TemplateOptions)
```

由template type渲染对应的template子组件。

> **说明：**
>
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 当前模板类型。 |
| itemBuilder | RepeatItemBuilder&lt;T&gt; | 是 | 组件生成函数。 |
| templateOptions | TemplateOptions | 否 | 当前模板配置项。<br/>默认值为undefined。 |

## templateId

```TypeScript
templateId(typedFunc: TemplateTypedFunc<T>)
```

为当前数据项分配template type。

> **说明：**
>
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedFunc | TemplateTypedFunc&lt;T&gt; | 是 | 生成当前数据项对应的template type。 |

## virtualScroll

```TypeScript
virtualScroll(virtualScrollOptions?: VirtualScrollOptions)
```

`Repeat`开启虚拟滚动。

> **说明：**
>
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| virtualScrollOptions | VirtualScrollOptions | 否 | 虚拟滚动配置项。<br/>默认值为undefined。 |

