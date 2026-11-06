# Repeat
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @maorh-->
<!--Designer: @keerecles-->
<!--Tester: @khq-->
<!--Adviser: @zhang_yixin13-->

Repeat基于数组类型数据来进行循环渲染，一般与滚动容器组件配合使用。

本文档仅为API参数说明。组件描述和使用说明见[Repeat开发者指南](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)。

> **说明：**
>
> - 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。

## 接口

### Repeat

Repeat\<T\>(arr: Array\<T\>)

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型       | 必填 | 说明      |
| ------ | ---------- | -------- | -------- |
| arr    | Array\<T\> | 是 | 数据源，为`Array<T>`类型的数组，由开发者决定数据类型。 |

**示例：**
```ts
// arr是Array<string>类型的数组，以arr为数据源创建Repeat组件
Repeat<string>(this.arr)
```

### Repeat<sup>18+</sup>

Repeat\<T\>(arr: RepeatArray\<T\>, options?: RepeatOptions)

> **说明：**
>
> 从API version 18开始，Repeat数据源支持RepeatArray类型。
>
> 从API版本26.1.0开始，Repeat支持传入[RepeatOptions](#repeatoptions)，用于绑定控制器[RepeatController](#repeatcontroller)，以及设置动效过程中的子组件复用策略[allowReuseInAnimation](#repeatoptions)。

**卡片能力：** 从API version 18开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型       | 必填 | 说明      |
| ------ | ---------- | -------- | -------- |
| arr    | [RepeatArray\<T\>](#repeatarrayt18) | 是 | 数据源，为`RepeatArray<T>`类型的数组，由开发者决定数据类型。 |
| options    | [RepeatOptions](#repeatoptions) | 否 | 创建Repeat组件时的配置项，用于绑定控制器、设置动效过程中的子组件复用策略。不传入时使用默认配置（不绑定控制器）。<br>**起始版本：** 26.1.0<br>**模型约束：** 此接口仅可在Stage模型下使用。<br>**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。 |

## 属性

除支持[拖拽排序](./ts-universal-attributes-drag-sorting.md)属性外，还支持以下属性。

### each

each(itemGenerator: (repeatItem: RepeatItem\<T\>) => void)

组件生成函数。当所有[`.template()`](#template)的type和[`.templateId()`](#templateid)返回值不匹配（即当前item不适用任何template定义的样式）时，将使用`.each()`处理数据项。当`.each()`的组件生成函数也为空时，将不渲染子组件。

> **说明：**
>
> - `each`属性必须有，否则运行时会报错。
> - `itemGenerator`的参数为`RepeatItem`，该参数将`item`和`index`结合到了一起，请勿将`RepeatItem`参数拆开使用。
>
> - 该接口不支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明 |
| ------ | ---------- | -------- | -------- |
| itemGenerator  | (repeatItem: [RepeatItem\<T\>](#repeatitemt)) => void | 是 | 组件生成函数。repeatItem：将item（arr数组中的数据项）和index（数据项索引）组合到一起的状态变量。 |

**示例：**
```ts
// arr是Array<string>类型的数组，为每个数据创建一个Text组件
Repeat<string>(this.arr)
  .each((repeatItem: RepeatItem<string>) => { Text(repeatItem.item) })
```

### key

key(keyGenerator: (item: T, index: number) => string)

键值生成函数。键值用于标识每个数据项，Repeat通过对比新旧键值来判断数据项的变化（新增、删除、修改），从而决定组件的复用与更新，实现高效渲染。

> **说明：**
>
> 该接口不支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明  |
| ------ | ---------- | -------- | -------- |
| keyGenerator  | (item: T, index: number) => string | 是 | 键值生成函数。<br>item：`arr`数组中的数据项，可选。缺省时默认忽略该参数，请勿在闭包函数的实现中使用该参数，否则会编译报错。<br>index：`arr`数组中的数据项索引，可选。缺省时默认忽略该参数，请勿在闭包函数的实现中使用该参数，否则会编译报错。 |

**示例：**
```ts
// arr是Array<string>类型的数组，为每个数据创建一个Text组件
// 并将字符串的值作为其键值
Repeat<string>(this.arr)
  .each((repeatItem: RepeatItem<string>) => { Text(repeatItem.item) })
  .key((obj: string) => obj)
```

### virtualScroll

virtualScroll(virtualScrollOptions?: VirtualScrollOptions)

`Repeat`开启虚拟滚动。适用于数据项数量超出屏幕可见区域的长列表场景。开启后，Repeat仅加载可见区域及预加载区域内的子组件，而非加载全部数据项，从而提升大数据量场景下的滚动性能。

> **说明：**
>
> 该接口不支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明  |
| ------ | ---------- | -------- | -------- |
| virtualScrollOptions  | [VirtualScrollOptions](#virtualscrolloptions)  | 否 | 虚拟滚动配置项。当需要自定义虚拟滚动配置（如设置期望加载的数据项总数、复用功能、内存优化策略等）时传入此参数；不传入时默认值为undefined，Repeat将使用默认配置（totalCount取数据源长度、reusable默认为true等）。 |

**示例：**
```ts
// arr是Array<string>类型的数组，为每个数据创建一个Text组件
// 在List容器组件中使用Repeat，并打开virtualScroll
List() {
  Repeat<string>(this.arr)
    .each((repeatItem: RepeatItem<string>) => { ListItem() { Text(repeatItem.item) }})
    .virtualScroll()
}
```

### template

template(type: string, itemBuilder: RepeatItemBuilder\<T\>, templateOptions?: TemplateOptions)

由template type渲染对应的template子组件，适用于列表中存在多种类型数据项、需要按类型展示不同样式布局的场景。

当所有`.template()`的type和`.templateId()`返回值不匹配（即当前item不适用任何template定义的样式）时，将使用[`.each()`](#each)的组件生成函数处理数据项。当`.each()`的组件生成函数也为空时，将不渲染子组件。

> **说明：**
>
> 该接口不支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明  |
| ------ | ---------- | -------- | -------- |
| type | string | 是 | 当前模板类型标识，需与templateId()的返回值相匹配，用于确定数据项使用哪个模板进行渲染。 |
| itemBuilder  | [RepeatItemBuilder](#repeatitembuildert)\<T\> | 是 | 组件生成函数，用于渲染当前template对应的子组件。repeatItem为携带item（数据项）与index（索引）的组合状态变量，请勿将`RepeatItem`参数拆开使用。 |
| templateOptions | [TemplateOptions](#templateoptions对象说明) | 否 | 当前模板配置项。当需要自定义模板配置（如设置模板缓存池中可缓存子组件节点的最大数量cachedCount等）时传入此参数；不传入时默认值为undefined，Repeat将使用默认模板配置。 |

**示例：**
```ts
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

### templateId

templateId(typedFunc: TemplateTypedFunc\<T\>)

为当前数据项分配template type，适用于列表中存在多种类型数据项、需要为不同类型数据项指定不同渲染模板的场景。需要与[`.template()`](#template)配合使用，templateId()的返回值应与template()中定义的type相匹配。当返回值不匹配任何template()定义的type时，该数据项将由[`.each()`](#each)的组件生成函数处理；若.each()也为空，则不渲染子组件。

> **说明：**
>
> 该接口不支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明  |
| ------ | ---------- | -------- | -------- |
| typedFunc | [TemplateTypedFunc](#templatetypedfunct)\<T\> | 是 | 生成当前数据项对应的template type。 |

**示例：**
```ts
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

## RepeatArray\<T\><sup>18+</sup>

type RepeatArray\<T\> = Array\<T\> \| ReadonlyArray\<T\> \| Readonly\<Array\<T\>\>

Repeat数据源参数联合类型。

**卡片能力：** 从API version 18开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

|  类型       | 说明      |
| -------- | -------- |
| Array\<T\> | 常规数组类型。 |
| ReadonlyArray\<T\> | 只读数组类型，不允许数组对象变更。 |
| Readonly\<Array\<T\>> | 只读数组类型，不允许数组对象变更。 |

## RepeatOptions

创建Repeat组件时的配置项。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| --- | --- | --- | --- | --- |
| controller | [RepeatController](#repeatcontroller) | 否 | 是 | 绑定到Repeat组件上的控制器。绑定后，需要清理缓存时可调用[clearCache](#clearcache)清理Repeat组件懒加载模式下缓存池中的组件。该控制器仅在创建Repeat时绑定，不支持动态修改。<br>默认值：undefined，即不绑定控制器。 |
| allowReuseInAnimation | boolean | 否 | 是 | Repeat在[animateTo](../arkts-apis-uicontext-uicontext.md#animateto)动效过程中更新时，是否允许复用子组件。仅在Repeat的父容器组件为[List](./ts-container-list.md)、[Grid](./ts-container-grid.md)、[WaterFlow](./ts-container-waterflow.md)时生效。<br>Repeat与动效一起使用时，Repeat的复用能力会与动效产生冲突，导致动效异常。在涉及动效的场景下，需将该参数设置为false，Repeat在动效过程中更新时将不复用子组件，从而支持动效。<br>true：动效过程中复用能力仍保持开启。<br>false：动效过程中复用能力关闭。<br>默认值：Repeat的父容器组件为List时为false；父容器组件为Grid或WaterFlow时为true。 |

## RepeatController

Repeat组件的控制器。通过[RepeatOptions](#repeatoptions)中的controller字段将控制器绑定到Repeat组件上，需要清理缓存时调用[clearCache](#clearcache)清理Repeat组件懒加载模式下缓存池中的组件。

> **说明：**
>
> 1. controller仅在Repeat创建时绑定，不支持动态修改。
> 2. 一个控制器只能控制一个Repeat组件。若将控制器绑定到另一个Repeat，则之前的绑定自动失效，控制器仅控制最后绑定的组件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor()

RepeatController的构造函数。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### clearCache

clearCache(): void

清理该控制器绑定的Repeat组件懒加载模式下缓存池中的组件。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RepeatItem\<T\>

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型   | 只读 | 可选 | 说明                                         |
| ------ | ------ | ---- | ---- | -------------------------------------------- |
| item   | T      | 否 | 否  | arr中每一个数据项。T为开发者传入的数据类型。 |
| index  | number | 否 | 否  | 当前数据项对应的索引。                       |

## VirtualScrollOptions

配置懒加载模式下期望加载的数据项总数、复用能力、数据精准懒加载能力。从API版本26.0.0开始，支持配置内存优化策略。

### 属性

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 类型   | 只读 | 可选 | 说明                                                         |
| ---------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| totalCount | number | 否 | 是  | 期望加载的数据项总数，可以不等于数据源长度（实际传入Repeat的数组的长度）。<br>取值范围：自然数。<br>totalCount与onTotalCount()最多设置一个；如果均未设置，则采用默认值：数据源长度；如果同时设置，则忽略totalCount。<br>totalCount缺省或超出取值范围时，totalCount取值为数据源长度，列表正常滚动。<br>totalCount = 0时，不加载数据。<br>0 < totalCount <= 数据源长度时，界面中只渲染区间[0, totalCount - 1]范围内的数据。<br>totalCount > 数据源长度时，Repeat将渲染区间[0, totalCount - 1]范围内的数据，容器组件滚动条样式根据totalCount值变化。在容器组件滚动过程中，应用需要保证在列表即将滑动到数据源末尾时请求后续数据。开发者需要对数据请求的错误场景（如网络延迟）进行保护操作，直到数据源全部加载完成，否则列表滑动过程中会出现滚动效果异常。建议配合使用[onLazyLoading](#onlazyloading19)实现数据懒加载。<br>除totalCount属性外，开发者也可以通过[onTotalCount](#ontotalcount19)方法设置自定义方法，计算期望加载的数据项总数。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| reusable<sup>18+</sup> | boolean | 否 | 是  | 是否开启复用功能。当Repeat的子组件为[@ReusableV2](../../../ui/state-management/arkts-new-reusableV2.md)装饰的自定义组件时，Repeat自身的复用能力优先于@ReusableV2的复用能力，若开发者希望使用@ReusableV2的复用能力，建议关闭Repeat自身的复用能力。<br>true：开启复用。<br>false：关闭复用。<br>默认值：true<br>**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。 |
| memoryOptimizationStrategy | [RepeatMemOptStrategy](#repeatmemoptstrategy) | 否 | 是 | Repeat的内存优化策略。该参数在创建Repeat时设定，不支持动态修改。<br>默认值：[DEFAULT](#repeatmemoptstrategy)<br>**起始版本：** 26.0.0<br>**模型约束：** 此接口仅可在Stage模型下使用。<br>**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。|

**示例：**

```ts
// arr是Array<string>类型的数组，在List容器组件中使用Repeat，并打开virtualScroll
// 将加载的数据项总数设为数据源的长度，并开启复用功能
List() {
  Repeat<string>(this.arr)
    .each((repeatItem: RepeatItem<string>) => { ListItem() { Text(repeatItem.item) }})
    .virtualScroll({ totalCount: this.arr.length, reusable: true })
}
```

### onTotalCount<sup>19+</sup>

onTotalCount?(): number

可选方法，计算期望加载的数据项总数。需要开发者给定计算方法，其返回值可以不等于数据源长度（实际传入Repeat的数组的长度）。

[totalCount](#属性-1)和onTotalCount()的返回值都表示期望加载的数据项总数。开发者可直接设置totalCount属性，给出期望加载的数据项总数，也可以通过onTotalCount()设定自定义方法，计算期望加载的数据项总数。totalCount与onTotalCount()最多设置一个。如果均未设置，则采用默认值：数据源长度；如果同时设置，则忽略totalCount。

onTotalCount()不同返回值的数据加载处理规则与totalCount一致，具体如下：

- onTotalCount()返回值 = 0时，不加载数据。
- 0 < onTotalCount()返回值 <= 数据源长度时，只加载区间[0, onTotalCount()返回值 - 1]索引范围内的数据。
- onTotalCount()返回值 > 数据源长度时，代表Repeat期望加载区间[0, onTotalCount()返回值 - 1]索引范围内的数据，容器组件滚动条样式根据onTotalCount()返回值变化。在容器组件滚动过程中，应用需要保证在列表即将滑动到数据源末尾时请求后续数据。开发者需要对数据请求的错误场景（如网络延迟）进行保护操作，直到数据源全部加载完成，否则列表滑动过程中会出现滚动效果异常。建议配合使用[onLazyLoading](#onlazyloading19)实现数据懒加载。
- onTotalCount()返回值是非自然数时，由数据源长度取代其返回值。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|    类型   | 说明 |
| ------ | ---------- |
|  number |  期望加载的数据项总数。<br>取值范围：自然数。 |

### onLazyLoading<sup>19+</sup>

onLazyLoading?(index: number): void

可选方法，懒加载指定索引的数据。需要开发者给定数据加载方法。

onLazyLoading方法需在懒加载场景下使用。开发者可设置自定义方法，用于向指定的数据源index中写入数据。以下为onLazyLoading的处理规则：

- Repeat读取数据源中index对应的数据之前，会先检查index处是否存在数据。
- 如果不存在数据，但开发者提供了onLazyLoading方法，Repeat将调用此方法。
- 在onLazyLoading方法中，开发者需要向Repeat指定的index中写入数据，方式如下：`arr[index] = ...`，其中`arr`表示传入Repeat的数组。不允许使用除`[]`以外的数组操作，且不允许写入指定index以外的元素，否则系统将抛出异常。
- onLazyLoading方法执行完成后，若指定index中仍无数据，将导致当前index和后续索引对应的组件无法加载。
- 精准懒加载能力为可选配置项。当onLazyLoading缺省，并且totalCount或onTotalCount的返回值大于数据源长度时，Repeat不会渲染列表滚动到数据源末尾时缺失的后续数据。
- onLazyLoading方法中应避免阻塞式耗时操作（如同步网络请求、复杂计算）。若数据加载耗时可能影响滚动流畅度，建议先在onLazyLoading方法中为此数据创建占位符，再创建异步任务加载数据。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明 |
| ------ | ---------- | -------- | -------- |
| index  | number | 是 | 需要加载的数据项对应的索引。<br>取值范围：自然数。 |

**示例：**

```ts
// 假设数据项总数为100，首屏渲染需3项数据
// 初始数组提供前3项数据（arr = ['No.0', 'No.1', 'No.2']），并开启数据懒加载功能
List() {
  Repeat<string>(this.arr)
    .each((repeatItem: RepeatItem<string>) => { ListItem() { Text(repeatItem.item) }})
    .virtualScroll({ 
      onTotalCount: () => { return 100; },
      onLazyLoading: (index: number) => { this.arr[index] = `No.${index}`; }
    })
}
```

## RepeatItemBuilder\<T\>

type RepeatItemBuilder\<T\> = (repeatItem: RepeatItem\<T\>) => void

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型          | 必填      | 说明                                    |
| ---------- | ------------- | --------------------------------------- | --------------------------------------- |
| repeatItem | [RepeatItem](#repeatitemt)\<T\> | 否 | 将item和index组合到一起的状态变量。<br>缺省时默认忽略该参数，请勿在闭包函数的实现中使用该参数，否则会编译报错。 |

## TemplateOptions对象说明

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称      | 类型   | 只读 | 可选 | 说明                                                         |
| ----------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| cachedCount | number | 否 | 是  | 当前template的缓存池中可缓存子组件节点的最大数量。取值范围是[0, +∞)，默认值为容器组件显示区域节点与预加载区域节点的个数之和。当容器组件显示区域节点与预加载节点的个数之和增多时（滑动过程中，只有部分高度的子组件在显示区域），cachedCount也会对应增长。需要注意cachedCount数量不会减少。传入负数等超出取值范围的值时，使用默认值处理。|

当cachedCount值被设置为当前template在容器组件显示区域的最大节点数量时，Repeat会做到最大程度的复用。当容器组件显示区域内没有当前template的节点时，缓存池不会释放，同时应用内存增大。开发者需要根据应用对内存占用和组件复用效率的需求自行调整，推荐cachedCount值设置为容器组件显示区域内节点个数。需要注意，不建议设置cachedCount小于2，这会导致在快速滑动场景下频繁创建新的节点，从而造成性能劣化。

> **说明：**
> 
> 滚动容器组件属性`.cachedCount()`和Repeat组件属性`.template()`的参数`cachedCount`都是为了平衡性能和内存，但是含义是不同的。
> - 滚动容器组件`.cachedCount()`：是指在容器组件显示区域外预加载区域的大小，该区域内子组件节点位于组件树上。滚动容器组件会额外渲染这些预加载区域的节点，从而提高列表滑动性能。
> - `.template()`中的`cachedCount`：指Repeat每个template的缓存池大小，当渲染新的子组件时，Repeat先判断对应template缓存池中是否有可用节点，有则复用，没有则创建新节点。

**示例：**
```ts
// arr是Array<string>类型的数组，在List容器组件中使用Repeat，并打开virtualScroll
// 创建模板temp，该模板为数据创建Text组件，所有数据项都使用temp模板
// 将temp模板的最大缓存节点数量设为2
List() {
  Repeat<string>(this.arr)
    .each((repeatItem: RepeatItem<string>) => {})
    .virtualScroll()
    .template('temp', (repeatItem: RepeatItem<string>) => { ListItem() { Text(repeatItem.item) }}, { cachedCount: 2 })
    .templateId((item: string, index: number) => { return 'temp' })
}
```

## TemplateTypedFunc\<T\>

type TemplateTypedFunc\<T\> = (item: T, index: number) => string

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                         |
| ------ | ------ | ---- | -------------------------------------------- |
| item   | T      | 否   | arr中每一个数据项。T为开发者传入的数据类型。<br>缺省时默认忽略该参数，请勿在闭包函数的实现中使用该参数，否则会编译报错。 |
| index  | number | 否   | 当前数据项对应的索引。<br>缺省时默认忽略该参数，请勿在闭包函数的实现中使用该参数，否则会编译报错。|

**返回值：**

| 类型   | 说明                                         |
| ------ | -------------------------------------------- |
| string      | 当前数据项生成的template type。|

## RepeatMemOptStrategy

Repeat内存优化策略枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |
| --- | --- | --- |
| DEFAULT | 0 | 无内存优化策略。 |
| ENABLE_AUTO_CACHE_OPTIMIZATION | 1 << 0 | 自动内存优化策略，当需要降低Repeat子节点的内存占用时，建议使用此策略以降低内存使用量。<br>当应用退后台时、Repeat所在组件不可见时（[visibility](./ts-universal-attributes-visibility.md#visibility)属性设置为[Visible](./ts-appendix-enums.md#visibility)以外的值，或组件面积为0，不考虑遮挡）、整机低内存时（[MemoryLevel](../../apis-ability-kit/js-apis-app-ability-abilityConstant.md#memorylevel)达到MEMORY_LEVEL_LOW或MEMORY_LEVEL_CRITICAL），释放[缓存池](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md#节点更新复用能力说明)内的所有节点。<br>当应用恢复前台时、Repeat所在组件恢复显示时，恢复缓存池内的节点。<br>在释放和恢复节点时，会触发[自定义组件生命周期](../../../ui/state-management/arkts-page-custom-components-lifecycle.md)。 |

## 示例

### 示例1（使用自动内存优化策略）

以下示例中，通过[VirtualScrollOptions](#virtualscrolloptions)的memoryOptimizationStrategy属性使用了自动内存优化策略。点击Scroll按钮，使列表跳转，旧节点进入缓存池。应用退后台时，清理缓存。应用恢复前台时，恢复缓存。

从API版本26.0.0开始，VirtualScrollOptions新增memoryOptimizationStrategy属性。

```ts
@ComponentV2
struct ChildComponent {
  aboutToAppear() {
    console.info('ChildComponent aboutToAppear');
  }
  aboutToDisappear() {
    console.info('ChildComponent aboutToDisappear');
  }
  build() {
    Text('ChildComponent')
  }
}

@Entry
@ComponentV2
struct MemoryOptimizeDemo {
  @Local data: Array<number> = [];
  private scroller: Scroller = new Scroller();
  aboutToAppear() {
    for (let i = 0; i < 100; i++) {
      this.data.push(i);
    }
  }
  build() {
    Column() {
      Button('Scroll').onClick(() => { // 点击按钮触发列表跳转，旧组件进入缓存池
        this.scroller.scrollToIndex(30);
      })
      List({ scroller: this.scroller }) {
        Repeat<number>(this.data)
          .each((repeatItem: RepeatItem<number>) => {
            ListItem() {
              ChildComponent()
            }
          })
          .virtualScroll({ memoryOptimizationStrategy: RepeatMemOptStrategy.ENABLE_AUTO_CACHE_OPTIMIZATION }) // 使用自动内存优化策略
      }
      .cachedCount(5)
    }
  }
}
```

### 示例2（主动清理缓存池）

以下示例中，通过[RepeatOptions](#repeatoptions)的controller属性绑定了[RepeatController](#repeatcontroller)。点击Scroll按钮，使列表跳转，旧组件进入缓存池。然后点击Clear按钮，主动清理Repeat缓存池中的组件。

从API版本26.1.0开始，Repeat接口新增options参数。

```ts
@ComponentV2
struct ChildComponent {
  aboutToAppear() {
    console.info('ChildComponent aboutToAppear');
  }
  aboutToDisappear() {
    console.info('ChildComponent aboutToDisappear');
  }
  build() {
    Text('ChildComponent')
  }
}

@Entry
@ComponentV2
struct ClearCacheDemo {
  @Local data: Array<number> = [];
  // 创建RepeatController对象
  private controller: RepeatController = new RepeatController();
  private scroller: Scroller = new Scroller();

  aboutToAppear(): void {
    for (let i = 0; i < 100; i++) {
      this.data.push(i);
    }
  }

  build() {
    Column() {
      List({ scroller: this.scroller }) {
        // 通过RepeatOptions的controller字段绑定控制器
        Repeat<number>(this.data, { controller: this.controller })
          .each((repeatItem: RepeatItem<number>) => {
            ListItem() {
              ChildComponent()
            }
          })
          .virtualScroll()
      }
      .cachedCount(5)
      .height('80%')

      Button('Scroll')
        .onClick(() => {
          // 点击按钮触发列表跳转，旧组件进入缓存池
          this.scroller.scrollToIndex(30);
        })

      Button('Clear')
        .onClick(() => {
          // 主动清理Repeat缓存池中的组件
          this.controller.clearCache();
        })
    }
  }
}
```

### 示例3（使用动效能力）

以下示例中，通过[RepeatOptions](#repeatoptions)的allowReuseInAnimation属性适配了动效能力。

从API版本26.1.0开始，Repeat接口新增options参数。

```ts
@Entry
@ComponentV2
struct RepeatAnimationDemo {
  @Local dataArray: string[] = [];
  private count: number = 0;

  aboutToAppear(): void {
    for (let i = 0; i < 20; i++) {
      this.dataArray.push(`Item ${i}`);
    }
  }

  build() {
    Column({ space: 5 }) {
      Row({ space: 5 }) {
        Button('Update Repeat in Animation')
          .onClick(() => { // 在动效过程中插入子组件
            this.getUIContext()?.animateTo({ duration: 1000 }, () => {
              this.dataArray.splice(0, 0, `New item ${this.count++}`)
            })
          })
      }
      Row({ space: 5 }) {
        Grid() {
          Repeat(this.dataArray, { allowReuseInAnimation: false }) // Repeat在动效过程中不复用子组件，从而适配动效
            .each((repeatItem) => {
              GridItem() {
                Text(repeatItem.item)
              }
              .width(150)
              .height(50)
              .border({ width: 1 })
              .transition(TransitionEffect.translate({ x: 300 })) // 设置子组件插入时的过渡效果
            })
            .key((item: string, index: number) => item)
            .virtualScroll()
        }
        .columnsTemplate('1fr')
        .columnsGap(5)
        .rowsGap(5)
        .width('80%')
      }
    }
    .width('100%')
  }
}
```

运行效果：

![Repeat-animate-grid](figures/repeat-animate-grid.gif)