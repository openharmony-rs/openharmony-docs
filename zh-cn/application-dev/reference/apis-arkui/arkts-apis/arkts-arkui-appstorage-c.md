# AppStorage

AppStorage是与应用进程绑定的全局UI状态存储中心，由UI框架在应用启动时创建，将UI状态数据存储于运行内存，实现应用级全局状态共享。具体UI使用说明，详见 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 > **说明：** > > 从API version 12开始，AppStorage支持\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_、 > \_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_，支持null、undefined以及 > \_\_\_MD\_LINK\_DESC\_USD\_4\_\_\_。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-unnamed-declare class AppStorage--><!--Device-unnamed-declare class AppStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Clear

```TypeScript
static Clear(): boolean
```

删除\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中所有属性。前提是AppStorage已经没有任何订阅者。如果有订阅者，Clear将不会生效并返回 false。如果没有订阅者且删除成功则返回true。 订阅者的含义参考[delete]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 10

**替代接口：** [AppStorage#clear](arkts-arkui-appstorage-c.md#clear)

<!--Device-AppStorage-static Clear(): boolean--><!--Device-AppStorage-static Clear(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中的属性已经没有订阅者则删除成功，返回true。否则返回false。 |

## Delete

```TypeScript
static Delete(propName: string): boolean
```

在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中删除propName对应的属性。 仅当AppStorage中该属性没有任何订阅者时可删除成功并返回true；如果有订阅者，则返回false。 属性的订阅者为[Link]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_、[Prop]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_等接口返回的实例，以及 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_和 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_装饰的变量。如果\@StorageLink('propName')、\@ StorageProp('propName')装饰的变量或SubscribedAbstractProperty实例依旧对propName有同步关系，则该属性不能从AppStorage中删除。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [AppStorage#delete](arkts-arkui-appstorage-c.md#delete)

<!--Device-AppStorage-static Delete(propName: string): boolean--><!--Device-AppStorage-static Delete(propName: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中有对应的属性，且该属性已经没有订阅者，则删除成功，返回true。如果属性不存在，或者该属性还存在订阅者，则返回false。 |

## Get

```TypeScript
static Get<T>(propName: string): T | undefined
```

获取propName在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中对应的属性值。如果不存在则返回undefined。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [AppStorage#get](arkts-arkui-appstorage-c.md#get)

<!--Device-AppStorage-static Get<T>(propName: string): T | undefined--><!--Device-AppStorage-static Get<T>(propName: string): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | AppStorage中propName对应的属性值，如果不存在则返回undefined。 |

## Has

```TypeScript
static Has(propName: string): boolean
```

判断propName对应的属性是否在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中存在。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [AppStorage#has](arkts-arkui-appstorage-c.md#has)

<!--Device-AppStorage-static Has(propName: string): boolean--><!--Device-AppStorage-static Has(propName: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果propName对应的属性在AppStorage中存在，则返回true。不存在则返回false。 |

## IsMutable

```TypeScript
static IsMutable(propName: string): boolean
```

返回\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中propName对应的属性是否是可变的。 > **说明：** > > 从API version 7开始支持，从API version 10开始废弃，暂无替代接口。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

<!--Device-AppStorage-static IsMutable(propName: string): boolean--><!--Device-AppStorage-static IsMutable(propName: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回AppStorage中propName对应的属性是否是可变的。当前该返回值恒为true。 |

## Keys

```TypeScript
static Keys(): IterableIterator<string>
```

返回\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中所有的属性名。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [AppStorage#keys](arkts-arkui-appstorage-c.md#keys)

<!--Device-AppStorage-static Keys(): IterableIterator<string>--><!--Device-AppStorage-static Keys(): IterableIterator<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;string&gt; | AppStorage中所有的属性名。 |

## Link

```TypeScript
static Link(propName: string): any
```

与\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中对应的propName建立双向数据绑定。如果给定的propName在AppStorage中存在，返回 与AppStorage中propName对应属性的双向绑定数据。 双向绑定数据的修改会同步回AppStorage中，AppStorage会将变化同步到所有绑定该propName的数据和自定义组件中。 如果AppStorage中不存在propName，则返回undefined。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [AppStorage#link](arkts-arkui-appstorage-c.md#link)

<!--Device-AppStorage-static Link(propName: string): any--><!--Device-AppStorage-static Link(propName: string): any-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| any | 返回双向绑定的数据，如果AppStorage中不存在对应的propName，则返回undefined。 |

## Prop

```TypeScript
static Prop(propName: string): any
```

与\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中对应的propName建立单向数据绑定。如果给定的propName在AppStorage中存在，则返 回与AppStorage中propName对应属性的单向绑定数据。如果AppStorage中不存在propName，则返回undefined。单向绑定数据的修改不会同步回AppStorage中。 > **说明：** > > Prop仅支持S类型（number、boolean、string）。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [AppStorage#prop](arkts-arkui-appstorage-c.md#prop)

<!--Device-AppStorage-static Prop(propName: string): any--><!--Device-AppStorage-static Prop(propName: string): any-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| any | 返回单向绑定的数据，如果AppStorage中不存在对应的propName，则返回undefined。 |

## Set

```TypeScript
static Set<T>(propName: string, newValue: T): boolean
```

在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中设置propName对应属性的值。如果newValue与propName对应属性的值相同，则不做赋值 操作，状态变量不会通知UI刷新propName对应属性的值。与[SetOrCreate]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_不同，Set仅在propName已存在时生效，propName不存在时返回 false。从API version 12开始，newValue可以为null或undefined。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [AppStorage#set](arkts-arkui-appstorage-c.md#set)

<!--Device-AppStorage-static Set<T>(propName: string, newValue: T): boolean--><!--Device-AppStorage-static Set<T>(propName: string, newValue: T): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| newValue | T | 是 | propName对应属性的新值，从API version 12开始可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中不存在propName对应的属性，返回false。设置成功则返回true。 |

## SetAndLink

```TypeScript
static SetAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

与[Link]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口类似，如果给定的propName在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中存 在，则返回该propName对应的属性的双向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，并返回其双向绑定数据。defaultValue必须为T类型，且不能为 null或undefined。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [AppStorage#setAndLink](arkts-arkui-appstorage-c.md#setandlink)

<!--Device-AppStorage-static SetAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static SetAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值，defaultValue不能为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | SubscribedAbstractProperty\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的实例，为AppStorage中propName对应属性的双向绑定的数据。 |

## SetAndProp

```TypeScript
static SetAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>
```

与[Prop]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口类似，如果给定的propName在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中存 在，则返回该propName对应的属性的单向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，返回其单向绑定数据。defaultValue必须为S类型，且不能为 null或undefined。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [AppStorage#setAndProp](arkts-arkui-appstorage-c.md#setandprop)

<!--Device-AppStorage-static SetAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>--><!--Device-AppStorage-static SetAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | S | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值，defaultValue不能为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;S&gt; | SubscribedAbstractProperty\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的实例，为AppStorage中propName对应属性的单向绑定的数据。 |

## SetOrCreate

```TypeScript
static SetOrCreate<T>(propName: string, newValue: T): void
```

如果propName已经在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中存在，并且newValue和propName对应属性的值不同，则设置 propName对应属性的值为newValue，否则状态变量不会通知UI刷新propName对应属性的值。如果不存在，则创建propName属性，值为newValue。从API version 12开始，newValue可以为 null或undefined。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [AppStorage#setOrCreate](arkts-arkui-appstorage-c.md#setorcreate)

<!--Device-AppStorage-static SetOrCreate<T>(propName: string, newValue: T): void--><!--Device-AppStorage-static SetOrCreate<T>(propName: string, newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| newValue | T | 是 | propName对应属性的新值，从API version 12开始可以为null或undefined。 |

## Size

```TypeScript
static Size(): number
```

返回\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中的属性数量。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 10

**替代接口：** [AppStorage#size](arkts-arkui-appstorage-c.md#size)

<!--Device-AppStorage-static Size(): number--><!--Device-AppStorage-static Size(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | AppStorage中属性的数量。 |

## clear

```TypeScript
static clear(): boolean
```

删除\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中所有属性。仅当AppStorage没有任何订阅者时可删除成功并返回true；如果有订阅者， clear不会生效并返回false。 订阅者的含义参考[delete]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static clear(): boolean--><!--Device-AppStorage-static clear(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中的属性已经没有订阅者则删除成功，返回true；如果当前仍有订阅者，返回false。 |

## delete

```TypeScript
static delete(propName: string): boolean
```

在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中删除propName对应的属性。 仅当AppStorage中该属性没有任何订阅者时可删除成功并返回true；如果有订阅者，则返回false。 属性的订阅者为： 1. \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、\_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_装饰的变量。 2. 通过[link]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_、[prop]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_、[setAndLink]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_、[setAndProp]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_接口返回的[SubscribedAbstractProperty]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_的实例。 如需删除这些订阅者，可通过以下方式： 1. 删除\@StorageLink、\@StorageProp所在的自定义组件。删除自定义组件请参考\_\_\_MD\_LINK\_DESC\_USD\_3\_\_\_。 2. 对link、prop、setAndLink、setAndProp接口返回的SubscribedAbstractProperty的实例调用[aboutToBeDeleted]\_\_\_JSDOC\_LINK\_DESC\_USD\_9\_\_\_接口。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static delete(propName: string): boolean--><!--Device-AppStorage-static delete(propName: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中有对应的属性，且该属性已经没有订阅者，则删除成功，返回true。如果属性不存在，或者该属性还存在订阅者，则返回false。 |

## get

```TypeScript
static get<T>(propName: string): T | undefined
```

获取propName在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中对应的属性值。如果不存在则返回undefined。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static get<T>(propName: string): T | undefined--><!--Device-AppStorage-static get<T>(propName: string): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | AppStorage中propName对应的属性值，如果不存在则返回undefined。 |

## has

```TypeScript
static has(propName: string): boolean
```

判断propName对应的属性是否在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中存在。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static has(propName: string): boolean--><!--Device-AppStorage-static has(propName: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果propName对应的属性在AppStorage中存在，则返回true。不存在则返回false。 |

## keys

```TypeScript
static keys(): IterableIterator<string>
```

返回\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中所有的属性名。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static keys(): IterableIterator<string>--><!--Device-AppStorage-static keys(): IterableIterator<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;string&gt; | AppStorage中所有的属性名。 |

## link

```TypeScript
static link<T>(propName: string): SubscribedAbstractProperty<T>
```

与\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中对应的propName建立双向数据绑定。如果给定的propName在AppStorage中存在，返回 AppStorage中propName对应属性的双向绑定数据。与[prop]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的单向数据绑定不同，link的修改会同步回AppStorage，AppStorage会将变化同步到所有绑定该 propName的数据和自定义组件中。 如果AppStorage中不存在propName，则返回undefined。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static link<T>(propName: string): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static link<T>(propName: string): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 返回双向绑定的数据，如果AppStorage中不存在对应的propName，则返回undefined。 |

## prop

```TypeScript
static prop<T>(propName: string): SubscribedAbstractProperty<T>
```

与\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中对应的propName建立单向数据绑定。如果给定的propName在AppStorage中存在，则返 回与AppStorage中propName对应属性的单向绑定数据。如果AppStorage中不存在propName，则返回undefined。单向绑定数据的修改不会同步回AppStorage中。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static prop<T>(propName: string): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static prop<T>(propName: string): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 返回单向绑定的数据，如果AppStorage中不存在对应的propName，则返回undefined。 |

## ref

```TypeScript
static ref<T>(propName: string): AbstractProperty<T> | undefined
```

如果给定的propName在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中存在，则返回AppStorage中propName对应属性的引用。否则，返 回undefined。 与[link]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的功能基本一致，区别在于不需要手动释放返回的[AbstractProperty&lt;T&gt;]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_类型的变量。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static ref<T>(propName: string): AbstractProperty<T> | undefined--><!--Device-AppStorage-static ref<T>(propName: string): AbstractProperty<T> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 返回AppStorage中propName对应属性的引用，如果AppStorage中不存在对应的propName，则返回undefined。 |

## set

```TypeScript
static set<T>(propName: string, newValue: T): boolean
```

在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中设置propName对应属性的值。如果newValue与propName对应属性的值相同，则不做赋值 操作，状态变量不会通知UI刷新propName对应属性的值。与[setOrCreate]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_不同，set仅在propName已存在时生效，propName不存在时返回 false。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static set<T>(propName: string, newValue: T): boolean--><!--Device-AppStorage-static set<T>(propName: string, newValue: T): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| newValue | T | 是 | propName对应属性的新值，从API version 12开始可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中不存在propName对应的属性，或设值失败，则返回false。设置成功则返回true。 |

## setAndLink

```TypeScript
static setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

与[link]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口类似，如果给定的propName在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中存 在，则返回该propName对应的属性的双向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，返回其双向绑定数据。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值。从API version 12开始，defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | SubscribedAbstractProperty\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的实例，为AppStorage中propName对应属性的双向绑定的数据。 |

## setAndProp

```TypeScript
static setAndProp<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

与[prop]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口类似，如果给定的propName在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中存 在，则返回该propName对应的属性的单向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，返回其单向绑定数据。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static setAndProp<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static setAndProp<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值。从API version 12开始，defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | SubscribedAbstractProperty\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的实例，为AppStorage中propName对应属性的单向绑定的数据。 |

## setAndRef

```TypeScript
static setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>
```

与[ref]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口类似，如果给定的propName在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中存在，则 返回AppStorage中propName对应属性的引用。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，并返回其引用。 与[setAndLink]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_的功能基本一致，区别在于不需要手动释放返回的[AbstractProperty&lt;T&gt;]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_ 类型的变量。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>--><!--Device-AppStorage-static setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值，defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | AbstractProperty\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_的实例，为AppStorage中propName对应属性的引用。 |

## setOrCreate

```TypeScript
static setOrCreate<T>(propName: string, newValue: T): void
```

如果propName已经在\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中存在，并且newValue和propName对应属性的值不同，则设置 propName对应属性的值为newValue，否则状态变量不会通知UI刷新propName对应属性的值。 如果propName不存在，则创建propName属性，值为newValue。setOrCreate仅可创建单个AppStorage的键值对，如需创建多个AppStorage键值对，可多次调用此方法。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static setOrCreate<T>(propName: string, newValue: T): void--><!--Device-AppStorage-static setOrCreate<T>(propName: string, newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| newValue | T | 是 | propName对应属性的新值，从API version 12开始可以为null或undefined。 |

## size

```TypeScript
static size(): number
```

返回\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中的属性数量。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static size(): number--><!--Device-AppStorage-static size(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | AppStorage中属性的数量。 |

## staticClear

```TypeScript
static staticClear(): boolean
```

删除\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中所有属性。仅当AppStorage没有任何订阅者时可删除成功并返回true；如果有订阅者， staticClear不会生效并返回false。订阅者的含义参考[delete]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [AppStorage.Clear](arkts-arkui-appstorage-c.md#clear)

<!--Device-AppStorage-static staticClear(): boolean--><!--Device-AppStorage-static staticClear(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 删除AppStorage中所有的属性。仅当没有任何订阅者时删除成功，返回true；如果仍有订阅者，返回false。 |

