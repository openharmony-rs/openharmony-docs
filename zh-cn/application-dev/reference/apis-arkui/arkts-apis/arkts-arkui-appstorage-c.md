# AppStorage

AppStorage具体UI使用说明，详见[AppStorage(应用全局的UI状态存储)](../../../ui/state-management/arkts-appstorage.md)

**起始版本：** 7

<!--Device-unnamed-declare class AppStorage--><!--Device-unnamed-declare class AppStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Clear

```TypeScript
static Clear(): boolean
```

删除[AppStorage](../../../ui/state-management/arkts-appstorage.md)中所有属性。删除所有属性的前提是，AppStorage已经没有任何订阅者。如果有订阅者，Clear将不会生效并返回false。如果没有订阅者且删除成功则返回true。

订阅者的含义参考[delete](arkts-arkui-appstorage-c.md#delete)。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [clear](arkts-arkui-appstorage-c.md#clear)

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

在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中删除propName对应的属性。

在AppStorage中删除该属性的前提是必须保证该属性没有订阅者。如果有订阅者，则返回false。如果没有订阅者则删除成功并返回true。

属性的订阅者为[Link](arkts-arkui-appstorage-c.md#link)、[Prop](arkts-arkui-appstorage-c.md#prop)等接口绑定的propName，以及[@StorageLink('propName')](../../../ui/state-management/arkts-appstorage.md#storagelink)和[@StorageProp('propName')](../../../ui/state-management/arkts-appstorage.md#storageprop)。如果自定义组件中使用@StorageLink('propName')和@StorageProp('propName')或者SubscribedAbstractProperty实例依旧对propName有同步关系，则该属性不能从AppStorage中删除。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [delete](arkts-arkui-appstorage-c.md#delete)

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

获取propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的属性值。如果不存在则返回undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [get](arkts-arkui-appstorage-c.md#get)

<!--Device-AppStorage-static Get<T>(propName: string): T | undefined--><!--Device-AppStorage-static Get<T>(propName: string): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Value of the property corresponding to **propName** in AppStorage, or **undefined** if it does not exist. |

## Has

```TypeScript
static Has(propName: string): boolean
```

判断propName对应的属性是否在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [has](arkts-arkui-appstorage-c.md#has)

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

返回[AppStorage](../../../ui/state-management/arkts-appstorage.md)中propName对应的属性是否是可变的。

**起始版本：** 7

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

返回[AppStorage](../../../ui/state-management/arkts-appstorage.md)中所有的属性名。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [keys](arkts-arkui-appstorage-c.md#keys)

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

与[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的propName建立双向数据绑定。如果给定的propName在AppStorage中存在，返回与AppStorage中propName对应属性的双向绑定数据。

双向绑定数据的修改会同步回AppStorage中，AppStorage会将变化同步到所有绑定该propName的数据和自定义组件中。

如果AppStorage中不存在propName，则返回undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [link](arkts-arkui-appstorage-c.md#link)

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

与[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的propName建立单向属性绑定。如果给定的propName在AppStorage中存在，则返回与AppStorage中propName对应属性的单向绑定数据。如果AppStorage中不存在propName，则返回undefined。单向绑定数据的修改不会被同步回AppStorage中。
> **说明：**
> Prop仅支持简单类型。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [prop](arkts-arkui-appstorage-c.md#prop)

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

在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中设置propName对应属性的值，如果newValue的值和propName对应属性的值相同，即不需要做赋值操作，状态变量不会通知UI刷新propName对应属性的值，从API version 12开始，newValue可以为null或undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [set](arkts-arkui-appstorage-c.md#set)

<!--Device-AppStorage-static Set<T>(propName: string, newValue: T): boolean--><!--Device-AppStorage-static Set<T>(propName: string, newValue: T): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| newValue | T | 是 | 属性值，从API version 12开始可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中不存在propName对应的属性，返回false。设置成功则返回true。 |

## SetAndLink

```TypeScript
static SetAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

与[Link](arkts-arkui-appstorage-c.md#link)接口类似，如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，则返回该propName对应的属性的双向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，并返回其双向绑定数据。defaultValue必须为T类型，且不能为null或undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [setAndLink](arkts-arkui-appstorage-c.md#setandlink)

<!--Device-AppStorage-static SetAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static SetAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在AppStorage中不存在，使用defaultValue在AppStorage中初始化propName对应属性的值，defaultValue不能为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | SubscribedAbstractProperty <T>的实例，和AppStorage中propName对应属性的双向绑定的数据。 |

## SetAndProp

```TypeScript
static SetAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>
```

与[Prop](arkts-arkui-appstorage-c.md#prop)接口类似。如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，则返回该propName对应的属性的单向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，返回其单向绑定数据。defaultValue必须为S类型，且不能为null或undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [setAndProp](arkts-arkui-appstorage-c.md#setandprop)

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
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;S&gt; | SubscribedAbstractProperty <S>的实例。 |

## SetOrCreate

```TypeScript
static SetOrCreate<T>(propName: string, newValue: T): void
```

如果propName已经在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，则设置propName对应的属性值为newValue。如果不存在，则创建propName属性，值为newValue。

newValue不能为null或undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [setOrCreate](arkts-arkui-appstorage-c.md#setorcreate)

<!--Device-AppStorage-static SetOrCreate<T>(propName: string, newValue: T): void--><!--Device-AppStorage-static SetOrCreate<T>(propName: string, newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| newValue | T | 是 | 属性值，不能为null或undefined。 |

## Size

```TypeScript
static Size(): number
```

返回[AppStorage](../../../ui/state-management/arkts-appstorage.md)中的属性数量。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [size](arkts-arkui-appstorage-c.md#size)

<!--Device-AppStorage-static Size(): number--><!--Device-AppStorage-static Size(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回AppStorage中属性的数量。 |

## clear

```TypeScript
static clear(): boolean
```

删除[AppStorage](../../../ui/state-management/arkts-appstorage.md)中所有属性。删除所有属性的前提是，AppStorage已经没有任何订阅者。如果有订阅者，clear将不会生效并返回false。如果没有订阅者，则删除成功，并返回true。

订阅者的含义参考[delete](arkts-arkui-appstorage-c.md#delete)。

**起始版本：** 10

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

在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中删除propName对应的属性。

在AppStorage中删除该属性的前提是必须保证该属性没有订阅者。如果有订阅者，则返回false。如果没有订阅者，则删除成功并返回true。

属性的订阅者为：

1. [@StorageLink](../../../ui/state-management/arkts-appstorage.md#storagelink)、[@StorageProp](../../../ui/state-management/arkts-appstorage.md#storageprop)装饰的变量。

2. 通过[link](arkts-arkui-appstorage-c.md#link)、[prop](arkts-arkui-appstorage-c.md#prop)、[setAndLink](arkts-arkui-appstorage-c.md#setandlink)、[setAndProp](arkts-arkui-appstorage-c.md#setandprop)接口返回的[SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c-sys.md)的实例。

如果想要删除这些订阅者，可以通过以下方式：

1. 删除@StorageLink、@StorageProp所在的自定义组件。删除自定义组件请参考[自定义组件的删除](../../../ui/state-management/arkts-page-custom-components-lifecycle.md#自定义组件的删除)。

2. 对link、prop、setAndLink、setAndProp接口返回的SubscribedAbstractProperty的实例调用[aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#abouttobedeleted)接口。

**起始版本：** 10

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

获取propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的属性值。如果不存在则返回undefined。

**起始版本：** 10

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
| T | Value of the property corresponding to **propName** in AppStorage, or **undefined** if it does not exist. |

## has

```TypeScript
static has(propName: string): boolean
```

判断propName对应的属性是否在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在。

**起始版本：** 10

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

返回[AppStorage](../../../ui/state-management/arkts-appstorage.md)中所有的属性名。

**起始版本：** 10

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

与[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的propName建立双向数据绑定。如果给定的propName在AppStorage中存在，返回AppStorage中propName对应属性的双向绑定数据。

双向绑定数据的修改会同步回AppStorage中，AppStorage会将变化同步到所有绑定该propName的数据和自定义组件中。

如果AppStorage中不存在propName，则返回undefined。

**起始版本：** 10

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
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | 返回双向绑定的数据，如果AppStorage中不存在对应的propName，则返回undefined。 |

## prop

```TypeScript
static prop<T>(propName: string): SubscribedAbstractProperty<T>
```

与[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的propName建立单向属性绑定。如果给定的propName在AppStorage中存在，则返回与AppStorage中propName对应属性的单向绑定数据。如果AppStorage中不存在propName，则返回undefined。单向绑定数据的修改不会被同步回AppStorage中。

**起始版本：** 10

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
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | 返回单向绑定的数据，如果AppStorage中不存在对应的propName，则返回undefined。 |

## ref

```TypeScript
static ref<T>(propName: string): AbstractProperty<T> | undefined
```

如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，则返回AppStorage中propName对应属性的引用。否则，返回undefined。

与[link](arkts-arkui-appstorage-c.md#link)的功能基本一致，但不需要手动释放返回的[AbstractProperty<T>](arkts-arkui-abstractproperty-i.md)类型的变量。

**起始版本：** 12

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
| [AbstractProperty](arkts-arkui-abstractproperty-i.md)&lt;T&gt; | A reference to the property in AppStorage, or **undefined** if the property does not exist. |

## set

```TypeScript
static set<T>(propName: string, newValue: T): boolean
```

在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中设置propName对应属性的值。如果newValue的值和propName对应属性的值相同，即不需要做赋值操作，状态变量不会通知UI刷新propName对应属性的值。
> **说明：**
> 从API version 12开始，AppStorage支持[Map](../../../ui/state-management/arkts-appstorage.md#装饰map类型变量)、  
> [Set](../../../ui/state-management/arkts-appstorage.md#装饰set类型变量)、  
> [Date类型](../../../ui/state-management/arkts-appstorage.md#装饰date类型变量)，支持null、undefined以及  
> [联合类型](../../../ui/state-management/arkts-appstorage.md#appstorage支持联合类型)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static set<T>(propName: string, newValue: T): boolean--><!--Device-AppStorage-static set<T>(propName: string, newValue: T): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| newValue | T | 是 | 属性值，从API version 12开始可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中不存在propName对应的属性，或设值失败，则返回false。设置成功则返回true。 |

## setAndLink

```TypeScript
static setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

与[link](arkts-arkui-appstorage-c.md#link)接口类似，如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，则返回该propName对应的属性的双向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，返回其双向绑定数据。
> **说明：**
> 从API version 12开始，AppStorage支持[Map](../../../ui/state-management/arkts-appstorage.md#装饰map类型变量)、  
> [Set](../../../ui/state-management/arkts-appstorage.md#装饰set类型变量)、  
> [Date类型](../../../ui/state-management/arkts-appstorage.md#装饰date类型变量)，支持null、undefined以及  
> [联合类型](../../../ui/state-management/arkts-appstorage.md#appstorage支持联合类型)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值，从API version 12开始，defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | SubscribedAbstractProperty <T>的实例，为AppStorage中propName对应属性的双向绑定的数据。 |

## setAndProp

```TypeScript
static setAndProp<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

与[prop](arkts-arkui-appstorage-c.md#prop)接口类似。如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，则返回该propName对应的属性的单向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，返回其单向绑定数据。
> **说明：**
> 从API version 12开始，AppStorage支持[Map](../../../ui/state-management/arkts-appstorage.md#装饰map类型变量)、  
> [Set](../../../ui/state-management/arkts-appstorage.md#装饰set类型变量)、  
> [Date类型](../../../ui/state-management/arkts-appstorage.md#装饰date类型变量)，支持null、undefined以及  
> [联合类型](../../../ui/state-management/arkts-appstorage.md#appstorage支持联合类型)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static setAndProp<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static setAndProp<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值，从API version 12开始，defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | SubscribedAbstractProperty <T>的实例。 |

## setAndRef

```TypeScript
static setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>
```

与[ref](arkts-arkui-appstorage-c.md#ref)接口类似，如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，则返回AppStorage中propName对应属性的引用。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，并返回其引用。

与[setAndLink](arkts-arkui-appstorage-c.md#setandlink)的功能基本一致，但不需要手动释放返回的[AbstractProperty<T>](arkts-arkui-abstractproperty-i.md)类型的变量。
> **说明：**
> 从API version 12开始，AppStorage支持[Map](../../../ui/state-management/arkts-appstorage.md#装饰map类型变量)、  
> [Set](../../../ui/state-management/arkts-appstorage.md#装饰set类型变量)、  
> [Date类型](../../../ui/state-management/arkts-appstorage.md#装饰date类型变量)，支持null、undefined以及  
> [联合类型](../../../ui/state-management/arkts-appstorage.md#appstorage支持联合类型)。

**起始版本：** 12

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
| [AbstractProperty](arkts-arkui-abstractproperty-i.md)&lt;T&gt; | AbstractProperty <T>的实例，为AppStorage中propName对应属性的引用。 |

## setOrCreate

```TypeScript
static setOrCreate<T>(propName: string, newValue: T): void
```

如果propName已经在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，并且newValue和propName对应属性的值不同，则设置propName对应属性的值为newValue，否则状态变量不会通知UI刷新propName对应属性的值。

如果propName不存在，则创建propName属性，值为newValue。setOrCreate只可以创建单个AppStorage的键值对，如果想创建多个AppStorage键值对，可以多次调用此方法。
> **说明：**
> 从API version 12开始，AppStorage支持[Map](../../../ui/state-management/arkts-appstorage.md#装饰map类型变量)、  
> [Set](../../../ui/state-management/arkts-appstorage.md#装饰set类型变量)、  
> [Date类型](../../../ui/state-management/arkts-appstorage.md#装饰date类型变量)，支持null、undefined以及  
> [联合类型](../../../ui/state-management/arkts-appstorage.md#appstorage支持联合类型)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static setOrCreate<T>(propName: string, newValue: T): void--><!--Device-AppStorage-static setOrCreate<T>(propName: string, newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| newValue | T | 是 | 属性值，从API version 12开始可以为null或undefined。 |

## size

```TypeScript
static size(): number
```

返回[AppStorage](../../../ui/state-management/arkts-appstorage.md)中的属性数量。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppStorage-static size(): number--><!--Device-AppStorage-static size(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回AppStorage中属性的数量。 |

## staticClear

```TypeScript
static staticClear(): boolean
```

删除所有的属性。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [Clear](arkts-arkui-appstorage-c.md#clear)

<!--Device-AppStorage-static staticClear(): boolean--><!--Device-AppStorage-static staticClear(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 删除所有的属性。如果删除成功，返回true；如果当前有状态变量依旧引用此属性，返回false。 |

