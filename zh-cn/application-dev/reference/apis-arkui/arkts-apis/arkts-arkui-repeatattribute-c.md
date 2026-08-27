# RepeatAttribute

除支持拖拽排序属性外，还支持以下属性。

**继承/实现关系：** RepeatAttribute extends DynamicNode<RepeatAttribute<T>>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## each

```TypeScript
each(itemGenerator: (repeatItem: RepeatItem<T>) => void): RepeatAttribute<T>
```

组件生成函数。当所有[`.template()`](#template)的type和[`.templateId()`](#templateid)返 回值不匹配（即当前item不适用任何template定义的样式）时，将使用`.each()`处理数据项。当`.each()`的组件生成函数也为空时，将不渲染子组件。

> **说明：**
> 
> - `each`属性必须有，否则运行时会报错。
> 
> - `itemGenerator`的参数为`RepeatItem`，该参数将`item`和`index`结合到了一起，请勿将`RepeatItem`参数拆开使用。
> 
> - 该接口不支持在attributeModifier中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemGenerator | (repeatItem: RepeatItem & lt;T & gt;) = & gt; void | 是 | 组件生成函数。repeatItem：将item（arr数组中的数据项）和index（数据项索引）组合到一起的状态变量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RepeatAttribute](arkts-arkui-repeatattribute-c.md)&lt;T&gt; |  |

**示例**

```TypeScript
// arr是Array<string>类型的数组，为每个数据创建一个Text组件
Repeat<string>(this.arr)
  .each((repeatItem: RepeatItem<string>) => { Text(repeatItem.item) })
```

## key

```TypeScript
key(keyGenerator: (item: T, index: number) => string): RepeatAttribute<T>
```

键值生成函数。键值用于标识每个数据项，Repeat通过对比新旧键值来判断数据项的变化（新增、删除、修改），从而决定组件的复用与更新，实现高效渲染。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyGenerator | (item: T, index: number) = & gt; string | 是 | 键值生成函数。 item：`arr`数组中的数据项，可选。缺省时默认忽略该参数，请勿在闭包函数的实现中使用该参数，否则会编译报错。 index：`arr`数组中的数据项索引，可选。缺省时默认忽略该参数，请勿在闭包函数的实现中使用该参数，否则会编译报错。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RepeatAttribute](arkts-arkui-repeatattribute-c.md)&lt;T&gt; |  |

**示例**

```TypeScript
// arr是Array<string>类型的数组，为每个数据创建一个Text组件
// 并将字符串的值作为其键值
Repeat<string>(this.arr)
  .each((repeatItem: RepeatItem<string>) => { Text(repeatItem.item) })
  .key((obj: string) => obj)
```

## template

```TypeScript
template(type: string, itemBuilder: RepeatItemBuilder<T>, templateOptions?: TemplateOptions): RepeatAttribute<T>
```

由template type渲染对应的template子组件，适用于列表中存在多种类型数据项、需要按类型展示不同样式布局的场景。当所有`.template()`的type和`.templateId()`返回值不匹配（即当前item不适用任何template定义的样式）时，将使用[`.each()`](#each)的 组件生成函数处理数据项。当`.each()`的组件生成函数也为空时，将不渲染子组件。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | string | 是 | 当前模板类型标识，需与templateId()的返回值相匹配，用于确定数据项使用哪个模板进行渲染。 |
| itemBuilder | [RepeatItemBuilder](arkts-arkui-repeatitembuilder-t.md)&lt;T&gt; | 是 | 组件生成函数，用于渲染当前template对应的子组件。repeatItem为携带item（数据项）与index（索引）的组合状态变量，请 勿将`RepeatItem`参数拆开使用。 |
| templateOptions | [TemplateOptions](arkts-arkui-templateoptions-i.md) | 否 | 当前模板配置项。当需要自定义模板配置（如设置模板缓存池中可缓存子组件节点的最大数量cachedCount等）时传入此参数；不传入时默认值为 undefined，Repeat将使用默认模板配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RepeatAttribute](arkts-arkui-repeatattribute-c.md)&lt;T&gt; |  |

**示例**

```TypeScript
// arr是Array<string>类型的数组
// 在List容器组件中使用Repeat，并打开virtualScroll
// 创建模板temp，该模板为数据创建Text组件
// 所有数据项都使用temp模板
List() {
  Repeat<string>(this.arr)
    .each((repeatItem: RepeatItem<string>) => {})
    .virtualScroll()
    .template('temp', (repeatItem: RepeatItem<string>) => { ListItem() { Text(repeatItem.item) }})
    .templateId((item: string, index: number) => { return 'temp' })
}
```

## templateId

```TypeScript
templateId(typedFunc: TemplateTypedFunc<T>): RepeatAttribute<T>
```

为当前数据项分配template type，适用于列表中存在多种类型数据项、需要为不同类型数据项指定不同渲染模板的场景。需要与[`.template()`](#template)配合使用， templateId()的返回值应与template()中定义的type相匹配。当返回值不匹配任何template()定义的type时，该数据项将由[`.each()`](#each)的组 件生成函数处理；若.each()也为空，则不渲染子组件。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| typedFunc | [TemplateTypedFunc](arkts-arkui-templatetypedfunc-t.md)&lt;T&gt; | 是 | 生成当前数据项对应的template type。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RepeatAttribute](arkts-arkui-repeatattribute-c.md)&lt;T&gt; |  |

**示例**

```TypeScript
// arr是Array<string>类型的数组
// 在List容器组件中使用Repeat，并打开virtualScroll
// 创建模板temp，该模板为数据创建Text组件
// 所有数据项都使用temp模板
List() {
  Repeat<string>(this.arr)
    .each((repeatItem: RepeatItem<string>) => {})
    .virtualScroll()
    .template('temp', (repeatItem: RepeatItem<string>) => { ListItem() { Text(repeatItem.item) }})
    .templateId((item: string, index: number) => { return 'temp' })
}
```

## virtualScroll

```TypeScript
virtualScroll(virtualScrollOptions?: VirtualScrollOptions): RepeatAttribute<T>
```

`Repeat`开启虚拟滚动。适用于数据项数量超出屏幕可见区域的长列表场景。开启后，Repeat仅加载可见区域及预加载区域内的子组件，而非加载全部数据项，从而提升大数据量场景下的滚动性能。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| virtualScrollOptions | [VirtualScrollOptions](arkts-arkui-virtualscrolloptions-i.md) | 否 | 虚拟滚动配置项。当需要自定义虚拟滚动配置（如设置期望加载的数据项总数、复用功能、内存优化策略等）时传入此参数；不传入时默 认值为undefined，Repeat将使用默认配置（totalCount取数据源长度、reusable默认为true等）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RepeatAttribute](arkts-arkui-repeatattribute-c.md)&lt;T&gt; |  |

**示例**

```TypeScript
// arr是Array<string>类型的数组，为每个数据创建一个Text组件
// 在List容器组件中使用Repeat，并打开virtualScroll
List() {
  Repeat<string>(this.arr)
    .each((repeatItem: RepeatItem<string>) => { ListItem() { Text(repeatItem.item) }})
    .virtualScroll()
}
```
