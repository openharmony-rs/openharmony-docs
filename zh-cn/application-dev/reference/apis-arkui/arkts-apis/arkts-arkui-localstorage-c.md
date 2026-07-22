# LocalStorage

LocalStorage具体UI使用说明，详见[LocalStorage(页面级UI状态存储)](../../../ui/state-management/arkts-localstorage.md)

**起始版本：** 9

<!--Device-unnamed-declare class LocalStorage--><!--Device-unnamed-declare class LocalStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## GetShared

```TypeScript
static GetShared(): LocalStorage
```

获取当前stage共享的[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [getShared](arkts-arkui-localstorage-c.md#getshared)

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-static GetShared(): LocalStorage--><!--Device-LocalStorage-static GetShared(): LocalStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocalStorage](arkts-arkui-localstorage-c.md) | 返回LocalStorage实例。 |

## clear

```TypeScript
clear(): boolean
```

删除[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中所有的属性。删除所有属性的前提是已经没有任何订阅者。如果有订阅者，clear不会生效并返回false。如果没有订阅者则删除成功并返回true。

订阅者的含义参考[delete](arkts-arkui-localstorage-c.md#delete)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-clear(): boolean--><!--Device-LocalStorage-clear(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果LocalStorage中的属性已经没有任何订阅者，则删除成功，并返回true。否则返回false。 |

## constructor

```TypeScript
constructor(initializingProperties?: Object)
```

创建一个新的[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例。使用Object.keys(initializingProperties)返回的属性和其数值，初始化LocalStorage实例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-constructor(initializingProperties?: Object)--><!--Device-LocalStorage-constructor(initializingProperties?: Object)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| initializingProperties | Object | 否 | 用initializingProperties包含的属性和数值初始化LocalStorage。initializingProperties不能为undefined。默认值为空对象，即初始化时不在LocalStorage中新增属性。 |

## delete

```TypeScript
delete(propName: string): boolean
```

在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中删除propName对应的属性。在LocalStorage中删除属性的前提是该属性已经没有订阅者，如果有订阅者，则返回false。如果没有订阅者则删除成功并返回true。

属性的订阅者为：

1. [@LocalStorageLink](../../../ui/state-management/arkts-localstorage.md#localstoragelink)、[@LocalStorageProp](../../../ui/state-management/arkts-localstorage.md#localstorageprop)装饰的变量。

2. 通过[link](arkts-arkui-localstorage-c.md#link)、[prop](arkts-arkui-localstorage-c.md#prop)、[setAndLink](arkts-arkui-localstorage-c.md#setandlink)、[setAndProp](arkts-arkui-localstorage-c.md#setandprop)接口返回的[SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c-sys.md)的实例。

如果想要删除这些订阅者，可以通过以下方式：

1. 删除@LocalStorageLink、@LocalStorageProp所在的自定义组件。删除自定义组件请参考[自定义组件的删除](../../../ui/state-management/arkts-page-custom-components-lifecycle.md#自定义组件的删除)。

2. 对link、prop、setAndLink、setAndProp接口返回的SubscribedAbstractProperty的实例调用[aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#abouttobedeleted)接口。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-delete(propName: string): boolean--><!--Device-LocalStorage-delete(propName: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果LocalStorage中有对应的属性，且该属性已经没有订阅者，则删除成功，返回true。如果属性不存在，或者该属性还存在订阅者，则返回false。 |

## get

```TypeScript
get<T>(propName: string): T | undefined
```

获取propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中对应的属性值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-get<T>(propName: string): T | undefined--><!--Device-LocalStorage-get<T>(propName: string): T | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | Value of the property corresponding to **propName** in LocalStorage, or **undefined** if it does not exist. |

## getShared

```TypeScript
static getShared(): LocalStorage
```

获取当前stage共享的[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例。
> **说明：**
> 从API version 12开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getSharedLocalStorage](getSharedLocalStorage)  
> 来明确UI的执行上下文。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** getSharedLocalStorage

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-static getShared(): LocalStorage--><!--Device-LocalStorage-static getShared(): LocalStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocalStorage](arkts-arkui-localstorage-c.md) | 返回LocalStorage实例。 |

## has

```TypeScript
has(propName: string): boolean
```

判断propName对应的属性是否在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-has(propName: string): boolean--><!--Device-LocalStorage-has(propName: string): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果propName对应的属性在LocalStorage中存在，则返回true。不存在则返回false。 |

## keys

```TypeScript
keys(): IterableIterator<string>
```

返回[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中所有的属性名。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-keys(): IterableIterator<string>--><!--Device-LocalStorage-keys(): IterableIterator<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;string&gt; | LocalStorage中所有的属性名。 |

## link

```TypeScript
link<T>(propName: string): SubscribedAbstractProperty<T>
```

如果给定的propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例中存在，则返回与LocalStorage中propName对应属性的双向绑定数据。

双向绑定数据的修改会被同步回LocalStorage中，LocalStorage会将变化同步到所有绑定该propName的数据和Component中。

如果LocalStorage中不存在propName，则返回undefined。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-link<T>(propName: string): SubscribedAbstractProperty<T>--><!--Device-LocalStorage-link<T>(propName: string): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | SubscribedAbstractProperty <T>的实例，与LocalStorage中propName对应属性的双向绑定的数据，如果LocalStorage中不存在对应的propName，则返回undefined。 |

## prop

```TypeScript
prop<S>(propName: string): SubscribedAbstractProperty<S>
```

如果给定的propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在，则返回与LocalStorage中propName对应属性的单向绑定数据。如果LocalStorage中不存在propName，则返回undefined。单向绑定数据的修改不会被同步回LocalStorage中。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-prop<S>(propName: string): SubscribedAbstractProperty<S>--><!--Device-LocalStorage-prop<S>(propName: string): SubscribedAbstractProperty<S>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;S&gt; | SubscribedAbstractProperty <S>的实例，和LocalStorage中propName对应属性的单向绑定的数据。如果LocalStorage中不存在对应的propName，则返回undefined。 |

## ref

```TypeScript
public ref<T>(propName: string): AbstractProperty<T> | undefined
```

如果给定的propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在，则返回LocalStorage中propName对应属性的引用。否则，返回undefined。

与[link](arkts-arkui-localstorage-c.md#link)的功能基本一致，但不需要手动释放返回的[AbstractProperty<T>](arkts-arkui-abstractproperty-i.md)类型的变量。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LocalStorage-public ref<T>(propName: string): AbstractProperty<T> | undefined--><!--Device-LocalStorage-public ref<T>(propName: string): AbstractProperty<T> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbstractProperty](arkts-arkui-abstractproperty-i.md)&lt;T&gt; | A reference to the property in LocalStorage, or **undefined** if the property does not exist. |

## set

```TypeScript
set<T>(propName: string, newValue: T): boolean
```

在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中设置propName对应属性的值。如果newValue的值和propName对应属性的值相同，即不需要做赋值操作，状态变量不会通知UI刷新propName对应属性的值。
> **说明：**
> 从API version 12开始，LocalStorage支持[Map](../../../ui/state-management/arkts-localstorage.md#装饰map类型变量)、  
> [Set](../../../ui/state-management/arkts-localstorage.md#装饰set类型变量)、  
> [Date类型](../../../ui/state-management/arkts-localstorage.md#装饰date类型变量)，支持null、undefined以及  
> [联合类型](../../../ui/state-management/arkts-localstorage.md#localstorage支持联合类型)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-set<T>(propName: string, newValue: T): boolean--><!--Device-LocalStorage-set<T>(propName: string, newValue: T): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |
| newValue | T | 是 | 属性值，从API version 12开始可以为undefined或者null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果LocalStorage中不存在propName对应的属性，返回false。设置成功返回true。 |

## setAndLink

```TypeScript
setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

与[link](arkts-arkui-localstorage-c.md#link)接口类似，如果给定的propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在，则返回该propName对应的属性的双向绑定数据。如果不存在，则使用defaultValue在LocalStorage中创建和初始化propName对应的属性，返回其双向绑定数据。
> **说明：**
> 从API version 12开始，LocalStorage支持[Map](../../../ui/state-management/arkts-localstorage.md#装饰map类型变量)、  
> [Set](../../../ui/state-management/arkts-localstorage.md#装饰set类型变量)、  
> [Date类型](../../../ui/state-management/arkts-localstorage.md#装饰date类型变量)，支持null、undefined以及  
> [联合类型](../../../ui/state-management/arkts-localstorage.md#localstorage支持联合类型)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-LocalStorage-setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在LocalStorage中不存在时，使用defaultValue在LocalStorage中初始化propName对应属性的值，从API version12开始defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | SubscribedAbstractProperty <T>的实例，与LocalStorage中propName对应属性的双向绑定的数据。 |

## setAndProp

```TypeScript
setAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>
```

与[prop](arkts-arkui-localstorage-c.md#prop)接口类似。如果propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在，则返回该propName对应的属性的单向绑定数据。如果不存在，则使用defaultValue在LocalStorage中创建和初始化propName对应的属性，返回其单向绑定数据。
> **说明：**
> 从API version 12开始，LocalStorage支持[Map](../../../ui/state-management/arkts-localstorage.md#装饰map类型变量)、  
> [Set](../../../ui/state-management/arkts-localstorage.md#装饰set类型变量)、  
> [Date类型](../../../ui/state-management/arkts-localstorage.md#装饰date类型变量)，支持null、undefined以及  
> [联合类型](../../../ui/state-management/arkts-localstorage.md#localstorage支持联合类型)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-setAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>--><!--Device-LocalStorage-setAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |
| defaultValue | S | 是 | 当propName在LocalStorage中不存在，使用defaultValue在LocalStorage中初始化propName对应属性的值，从API version 12开始defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;S&gt; | SubscribedAbstractProperty <S>的实例，和LocalStorage中propName对应属性的单向绑定的数据。 |

## setAndRef

```TypeScript
public setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>
```

与[ref](arkts-arkui-appstorage-c.md#ref)接口类似，如果给定的propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在，则返回LocalStorage中propName对应属性的引用。如果不存在，则使用defaultValue在LocalStorage中创建和初始化propName对应的属性，并返回其引用。

与[setAndLink](arkts-arkui-localstorage-c.md#setandlink)的功能基本一致，但不需要手动释放返回的[AbstractProperty<T>](arkts-arkui-abstractproperty-i.md)类型的变量。
> **说明：**
> 从API version 12开始，LocalStorage支持[Map](../../../ui/state-management/arkts-localstorage.md#装饰map类型变量)、  
> [Set](../../../ui/state-management/arkts-localstorage.md#装饰set类型变量)、  
> [Date类型](../../../ui/state-management/arkts-localstorage.md#装饰date类型变量)，支持null、undefined以及  
> [联合类型](../../../ui/state-management/arkts-localstorage.md#localstorage支持联合类型)。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LocalStorage-public setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>--><!--Device-LocalStorage-public setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在LocalStorage中不存在时，使用defaultValue在LocalStorage中初始化propName对应属性的值，defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbstractProperty](arkts-arkui-abstractproperty-i.md)&lt;T&gt; | AbstractProperty <T>的实例，为LocalStorage中propName对应属性的引用。 |

## setOrCreate

```TypeScript
setOrCreate<T>(propName: string, newValue: T): boolean
```

如果propName已经在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在，并且newValue和propName对应属性的值不同，则设置propName对应属性的值为newValue，否则状态变量不会通知UI刷新propName对应属性的值。

如果propName不存在，则创建propName属性，值为newValue。setOrCreate只可以创建单个LocalStorage的键值对，如果想创建多个LocalStorage键值对，可以多次调用此方法。
> **说明：**
> 从API version 12开始，LocalStorage支持[Map](../../../ui/state-management/arkts-localstorage.md#装饰map类型变量)、  
> [Set](../../../ui/state-management/arkts-localstorage.md#装饰set类型变量)、  
> [Date类型](../../../ui/state-management/arkts-localstorage.md#装饰date类型变量)，支持null、undefined以及  
> [联合类型](../../../ui/state-management/arkts-localstorage.md#localstorage支持联合类型)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-setOrCreate<T>(propName: string, newValue: T): boolean--><!--Device-LocalStorage-setOrCreate<T>(propName: string, newValue: T): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |
| newValue | T | 是 | 属性值，从API version 12开始可以为undefined或者null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果LocalStorage中存在propName，则更新其值为newValue，返回true。<br/>如果LocalStorage中不存在propName，则创建propName，并初始化其值为newValue，返回true。 |

## size

```TypeScript
size(): number
```

返回[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中的属性数量。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-size(): number--><!--Device-LocalStorage-size(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | LocalStorage中属性的数量。 |

