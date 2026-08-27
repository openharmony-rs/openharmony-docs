# AppStorage

AppStorage是与应用进程绑定的全局UI状态存储中心，由UI框架在应用启动时创建，将UI状态数据存储于运行内存，实现应用级全局状态共享。具体UI使用说明，详见 [AppStorage：应用全局的UI状态存储](../../../ui/state-management/arkts-appstorage.md)。

> **说明：**
> 
> 从API version 12开始，AppStorage支持[Map](../../../ui/state-management/arkts-appstorage.md#装饰map类型变量)、
> [Set](../../../ui/state-management/arkts-appstorage.md#装饰set类型变量)、
> [Date类型](../../../ui/state-management/arkts-appstorage.md#装饰date类型变量)，支持null、undefined以及
> [联合类型](../../../ui/state-management/arkts-appstorage.md#appstorage支持联合类型)。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## Clear

```TypeScript
static Clear(): boolean
```

删除[AppStorage](../../../ui/state-management/arkts-appstorage.md)中所有属性。前提是AppStorage已经没有任何订阅者。如果有订阅者，Clear将不会生效并返回 false。如果没有订阅者且删除成功则返回true。订阅者的含义参考[delete](#delete)。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [clear](#clear)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中的属性已经没有订阅者则删除成功，返回true。否则返回false。 |

**示例**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let res: boolean = AppStorage.Clear(); // true，已经没有订阅者
```

## clear

```TypeScript
static clear(): boolean
```

删除[AppStorage](../../../ui/state-management/arkts-appstorage.md)中所有属性。仅当AppStorage没有任何订阅者时可删除成功并返回true；如果有订阅者， clear不会生效并返回false。订阅者的含义参考[delete](#delete)。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中的属性已经没有订阅者则删除成功，返回true；如果当前仍有订阅者，返回false。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let res: boolean = AppStorage.clear(); // true，已经没有订阅者
```

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let res: boolean = storage.clear(); // true，已经没有订阅者
```

## Delete

```TypeScript
static Delete(propName: string): boolean
```

在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中删除propName对应的属性。仅当AppStorage中该属性没有任何订阅者时可删除成功并返回true；如果有订阅者，则返回false。属性的订阅者为[Link](#link)、[Prop](#prop)等接口返回的实例，以及 [@StorageLink](../../../ui/state-management/arkts-appstorage.md#storagelink)和 [@StorageProp](../../../ui/state-management/arkts-appstorage.md#storageprop)装饰的变量。如果\@StorageLink('propName')、\@ StorageProp('propName')装饰的变量或SubscribedAbstractProperty实例依旧对propName有同步关系，则该属性不能从AppStorage中删除。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [delete](#delete)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中有对应的属性，且该属性已经没有订阅者，则删除成功，返回true。如果属性不存在，或者该属性还存在订阅者，则返回false。 |

**示例**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
AppStorage.Link('PropA');
let res: boolean = AppStorage.Delete('PropA'); // false，PropA 还存在订阅者

AppStorage.SetOrCreate('PropB', 48);
let res1: boolean = AppStorage.Delete('PropB'); // true，PropB 已从AppStorage成功删除
```

## delete

```TypeScript
static delete(propName: string): boolean
```

在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中删除propName对应的属性。仅当AppStorage中该属性没有任何订阅者时可删除成功并返回true；如果有订阅者，则返回false。属性的订阅者为：
1. [@StorageLink](../../../ui/state-management/arkts-appstorage.md#storagelink)、[@StorageProp](../../../ui/state-management/arkts-appstorage.md#storageprop)装饰的变量。
2. 通过[link](#link)、[prop](#prop)、[setAndLink](#setandlink)、[setAndProp](#setandprop)接口返回的[SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)的实例。
如需删除这些订阅者，可通过以下方式：
1. 删除\@StorageLink、\@StorageProp所在的自定义组件。删除自定义组件请参考[自定义组件的删除](../../../ui/state-management/arkts-page-custom-components-lifecycle.md#自定义组件的删除)。
2. 对link、prop、setAndLink、setAndProp接口返回的SubscribedAbstractProperty的实例调用[aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#abouttobedeleted)接口。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果AppStorage中有对应的属性，且该属性已经没有订阅者，则删除成功，返回true。如果属性不存在，或者该属性还存在订阅者，则返回false。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
AppStorage.link<number>('PropA');
let res: boolean = AppStorage.delete('PropA'); // false，PropA 还存在订阅者

AppStorage.setOrCreate('PropB', 48);
let res1: boolean = AppStorage.delete('PropB'); // true，PropB 已从AppStorage成功删除
```

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
storage.link<number>('PropA');
let res: boolean = storage.delete('PropA'); // false，PropA 还存在订阅者
let res1: boolean = storage.delete('PropB'); // false，PropB 不存在于storage中
storage.setOrCreate('PropB', 48);
let res2: boolean = storage.delete('PropB'); // true，PropB 已从storage成功删除
```

## Get

```TypeScript
static Get<T>(propName: string): T | undefined
```

获取propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的属性值。如果不存在则返回undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [get](#get)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T \| undefined | AppStorage中propName对应的属性值，如果不存在则返回undefined。 |

**示例**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let value: number = AppStorage.Get('PropA') as number; // 47
```

## get

```TypeScript
static get<T>(propName: string): T | undefined
```

获取propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的属性值。如果不存在则返回undefined。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T \| undefined | AppStorage中propName对应的属性值，如果不存在则返回undefined。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let value: number = AppStorage.get('PropA') as number; // 47
```

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let value: number = storage.get('PropA') as number; // 47
```

## Has

```TypeScript
static Has(propName: string): boolean
```

判断propName对应的属性是否在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [has](#has)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果propName对应的属性在AppStorage中存在，则返回true。不存在则返回false。 |

**示例**

```TypeScript
AppStorage.Has('simpleProp');
```

## has

```TypeScript
static has(propName: string): boolean
```

判断propName对应的属性是否在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果propName对应的属性在AppStorage中存在，则返回true。不存在则返回false。 |

**示例**

```TypeScript
AppStorage.has('simpleProp');
```

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
storage.has('PropA'); // true
```

## IsMutable

```TypeScript
static IsMutable(propName: string): boolean
```

返回[AppStorage](../../../ui/state-management/arkts-appstorage.md)中propName对应的属性是否是可变的。

> **说明：**
> 
> 从API version 7开始支持，从API version 10开始废弃，暂无替代接口。

**起始版本：** 7

**废弃版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回AppStorage中propName对应的属性是否是可变的。当前该返回值恒为true。 |

**示例**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let res: boolean = AppStorage.IsMutable('PropA');
```

## Keys

```TypeScript
static Keys(): IterableIterator<string>
```

返回[AppStorage](../../../ui/state-management/arkts-appstorage.md)中所有的属性名。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [keys](#keys)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator & lt;string & gt; | AppStorage中所有的属性名。 |

**示例**

```TypeScript
AppStorage.SetOrCreate('PropB', 48);
let keys: IterableIterator<string> = AppStorage.Keys();
```

## keys

```TypeScript
static keys(): IterableIterator<string>
```

返回[AppStorage](../../../ui/state-management/arkts-appstorage.md)中所有的属性名。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator & lt;string & gt; | AppStorage中所有的属性名。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropB', 48);
let keys: IterableIterator<string> = AppStorage.keys();
```

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let keys: IterableIterator<string> = storage.keys();
```

## Link

```TypeScript
static Link(propName: string): any
```

与[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的propName建立双向数据绑定。如果给定的propName在AppStorage中存在，返回 与AppStorage中propName对应属性的双向绑定数据。双向绑定数据的修改会同步回AppStorage中，AppStorage会将变化同步到所有绑定该propName的数据和自定义组件中。如果AppStorage中不存在propName，则返回undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [link](#link)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| any | 返回双向绑定的数据，如果AppStorage中不存在对应的propName，则返回undefined。 |

**示例**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let linkToPropA1: SubscribedAbstractProperty<number> = AppStorage.Link('PropA');
let linkToPropA2: SubscribedAbstractProperty<number> = AppStorage.Link('PropA'); // linkToPropA2.get() == 47
linkToPropA1.set(48); // 双向同步：linkToPropA1.get() == linkToPropA2.get() == 48
```

## link

```TypeScript
static link<T>(propName: string): SubscribedAbstractProperty<T>
```

与[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的propName建立双向数据绑定。如果给定的propName在AppStorage中存在，返回 AppStorage中propName对应属性的双向绑定数据。与[prop](#prop)的单向数据绑定不同，link的修改会同步回AppStorage，AppStorage会将变化同步到所有绑定该 propName的数据和自定义组件中。如果AppStorage中不存在propName，则返回undefined。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | 返回双向绑定的数据，如果AppStorage中不存在对应的propName，则返回undefined。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let linkToPropA1: SubscribedAbstractProperty<number> = AppStorage.link('PropA');
let linkToPropA2: SubscribedAbstractProperty<number> = AppStorage.link('PropA'); // linkToPropA2.get() == 47
linkToPropA1.set(48); // 双向同步：linkToPropA1.get() == linkToPropA2.get() == 48
```

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let linkToPropA1: SubscribedAbstractProperty<number> = storage.link('PropA');
let linkToPropA2: SubscribedAbstractProperty<number> = storage.link('PropA'); // linkToPropA2.get() == 47
linkToPropA1.set(48); // 双向同步：linkToPropA1.get() == linkToPropA2.get() == 48
```

## Prop

```TypeScript
static Prop(propName: string): any
```

与[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的propName建立单向数据绑定。如果给定的propName在AppStorage中存在，则返 回与AppStorage中propName对应属性的单向绑定数据。如果AppStorage中不存在propName，则返回undefined。单向绑定数据的修改不会同步回AppStorage中。

> **说明：**
> 
> Prop仅支持S类型（number、boolean、string）。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [prop](#prop)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| any | 返回单向绑定的数据，如果AppStorage中不存在对应的propName，则返回undefined。 |

**示例**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let prop1: SubscribedAbstractProperty<number> = AppStorage.Prop('PropA');
let prop2: SubscribedAbstractProperty<number> = AppStorage.Prop('PropA');
prop1.set(1); // 单向同步：prop1.get()的值为1，prop2.get()的值为47
```

## prop

```TypeScript
static prop<T>(propName: string): SubscribedAbstractProperty<T>
```

与[AppStorage](../../../ui/state-management/arkts-appstorage.md)中对应的propName建立单向数据绑定。如果给定的propName在AppStorage中存在，则返 回与AppStorage中propName对应属性的单向绑定数据。如果AppStorage中不存在propName，则返回undefined。单向绑定数据的修改不会同步回AppStorage中。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | 返回单向绑定的数据，如果AppStorage中不存在对应的propName，则返回undefined。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let prop1: SubscribedAbstractProperty<number> = AppStorage.prop('PropA');
let prop2: SubscribedAbstractProperty<number> = AppStorage.prop('PropA');
prop1.set(1); // 单向同步：prop1.get()的值为1，prop2.get()的值为47
```

## ref

```TypeScript
static ref<T>(propName: string): AbstractProperty<T> | undefined
```

如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，则返回AppStorage中propName对应属性的引用。否则，返 回undefined。与[link](#link)的功能基本一致，区别在于不需要手动释放返回的[AbstractProperty&lt;T&gt;](arkts-arkui-abstractproperty-i.md)类型的变量。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbstractProperty](arkts-arkui-abstractproperty-i.md)&lt;T&gt; \| undefined | 返回AppStorage中propName对应属性的引用，如果AppStorage中不存在对应的propName，则返回undefined。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let refToPropA1: AbstractProperty<number> | undefined = AppStorage.ref('PropA');
let refToPropA2: AbstractProperty<number> | undefined = AppStorage.ref('PropA'); // refToPropA2.get() == 47
refToPropA1?.set(48); // 同步修改AppStorage：refToPropA1.get() == refToPropA2.get() == 48
```

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let refToPropA1: AbstractProperty<number> | undefined = storage.ref('PropA');
let refToPropA2: AbstractProperty<number> | undefined = storage.ref('PropA'); // refToPropA2.get() == 47
refToPropA1?.set(48); // refToPropA1.get() == refToPropA2.get() == 48
```

## Set

```TypeScript
static Set<T>(propName: string, newValue: T): boolean
```

在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中设置propName对应属性的值。如果newValue与propName对应属性的值相同，则不做赋值 操作，状态变量不会通知UI刷新propName对应属性的值。与[SetOrCreate](#setorcreate)不同，Set仅在propName已存在时生效，propName不存在时返回 false。从API version 12开始，newValue可以为null或undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [set](#set)

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

**示例**

```TypeScript
AppStorage.SetOrCreate('PropA', 48);
let res: boolean = AppStorage.Set('PropA', 47); // true
let res1: boolean = AppStorage.Set('PropB', 47); // false
```

## set

```TypeScript
static set<T>(propName: string, newValue: T): boolean
```

在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中设置propName对应属性的值。如果newValue与propName对应属性的值相同，则不做赋值 操作，状态变量不会通知UI刷新propName对应属性的值。与[setOrCreate](#setorcreate)不同，set仅在propName已存在时生效，propName不存在时返回 false。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

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

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 48);
let res: boolean = AppStorage.set('PropA', 47); // true
let res1: boolean = AppStorage.set('PropB', 47); // false
```

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let res: boolean = storage.set('PropA', 47); // true
let res1: boolean = storage.set('PropB', 47); // false
```

## SetAndLink

```TypeScript
static SetAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

与[Link](#link)接口类似，如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存 在，则返回该propName对应的属性的双向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，并返回其双向绑定数据。defaultValue必须为T类型，且不能为 null或undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [setAndLink](#setandlink)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值，defaultValue不能为 null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md) & lt;T & gt;的实例，为AppStorage中propName对应属性的双向绑定的数据。 |

**示例**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let link1: SubscribedAbstractProperty<number> = AppStorage.SetAndLink('PropB', 49); // 用默认值49创建PropB
let link2: SubscribedAbstractProperty<number> = AppStorage.SetAndLink('PropA', 50); // PropA已存在，值为47
```

## setAndLink

```TypeScript
static setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

与[link](#link)接口类似，如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存 在，则返回该propName对应的属性的双向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，返回其双向绑定数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值。从API version 12开 始，defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md) & lt;T & gt;的实例，为AppStorage中propName对应属性的双向绑定的数据。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let link1: SubscribedAbstractProperty<number> = AppStorage.setAndLink('PropB', 49); // 用默认值49创建PropB
let link2: SubscribedAbstractProperty<number> = AppStorage.setAndLink('PropA', 50); // PropA已存在，值为47
```

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let link1: SubscribedAbstractProperty<number> = storage.setAndLink('PropB', 49); // 用默认值49创建PropB
let link2: SubscribedAbstractProperty<number> = storage.setAndLink('PropA', 50); // PropA已存在，值为47
```

## SetAndProp

```TypeScript
static SetAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>
```

与[Prop](#prop)接口类似，如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存 在，则返回该propName对应的属性的单向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，返回其单向绑定数据。defaultValue必须为S类型，且不能为 null或undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [setAndProp](#setandprop)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | S | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值，defaultValue不能为 null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;S&gt; | [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md) & lt;S & gt;的实例，为AppStorage中propName对应属性的单向绑定的数据。 |

**示例**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let prop: SubscribedAbstractProperty<number> = AppStorage.SetAndProp('PropB', 49); // PropA -> 47, PropB -> 49
```

## setAndProp

```TypeScript
static setAndProp<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

与[prop](#prop)接口类似，如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存 在，则返回该propName对应的属性的单向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，返回其单向绑定数据。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值。从API version 12开 始，defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md) & lt;T & gt;的实例，为AppStorage中propName对应属性的单向绑定的数据。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let prop: SubscribedAbstractProperty<number> = AppStorage.setAndProp('PropB', 49); // PropA -> 47, PropB -> 49
```

## setAndRef

```TypeScript
static setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>
```

与[ref](#ref)接口类似，如果给定的propName在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，则 返回AppStorage中propName对应属性的引用。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，并返回其引用。与[setAndLink](#setandlink)的功能基本一致，区别在于不需要手动释放返回的[AbstractProperty&lt;T&gt;](arkts-arkui-abstractproperty-i.md) 类型的变量。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化propName对应属性的值，defaultValue可以为 null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbstractProperty](arkts-arkui-abstractproperty-i.md)&lt;T&gt; | [AbstractProperty](arkts-arkui-abstractproperty-i.md) & lt;T & gt;的实例，为AppStorage中propName对应属性的引用。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let ref1: AbstractProperty<number> = AppStorage.setAndRef('PropB', 49); // 用默认值49创建PropB
let ref2: AbstractProperty<number> = AppStorage.setAndRef('PropA', 50); // PropA已存在，值为47
```

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let ref1: AbstractProperty<number> = storage.setAndRef('PropB', 49); // 用默认值49创建PropB
let ref2: AbstractProperty<number> = storage.setAndRef('PropA', 50); // PropA已存在，值为47
```

## SetOrCreate

```TypeScript
static SetOrCreate<T>(propName: string, newValue: T): void
```

如果propName已经在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，并且newValue和propName对应属性的值不同，则设置 propName对应属性的值为newValue，否则状态变量不会通知UI刷新propName对应属性的值。如果不存在，则创建propName属性，值为newValue。从API version 12开始，newValue可以为 null或undefined。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [setOrCreate](#setorcreate)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| newValue | T | 是 | propName对应属性的新值，从API version 12开始可以为null或undefined。 |

**示例**

```TypeScript
AppStorage.SetOrCreate('simpleProp', 121);
```

## setOrCreate

```TypeScript
static setOrCreate<T>(propName: string, newValue: T): void
```

如果propName已经在[AppStorage](../../../ui/state-management/arkts-appstorage.md)中存在，并且newValue和propName对应属性的值不同，则设置 propName对应属性的值为newValue，否则状态变量不会通知UI刷新propName对应属性的值。如果propName不存在，则创建propName属性，值为newValue。setOrCreate仅可创建单个AppStorage的键值对，如需创建多个AppStorage键值对，可多次调用此方法。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | AppStorage中的属性名。 |
| newValue | T | 是 | propName对应属性的新值，从API version 12开始可以为null或undefined。 |

**示例**

```TypeScript
AppStorage.setOrCreate('simpleProp', 121);
```

## Size

```TypeScript
static Size(): number
```

返回[AppStorage](../../../ui/state-management/arkts-appstorage.md)中的属性数量。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [size](#size)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | AppStorage中属性的数量。 |

**示例**

```TypeScript
AppStorage.SetOrCreate('PropB', 48);
let res: number = AppStorage.Size(); // 1
```

## size

```TypeScript
static size(): number
```

返回[AppStorage](../../../ui/state-management/arkts-appstorage.md)中的属性数量。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | AppStorage中属性的数量。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropB', 48);
let res: number = AppStorage.size(); // 1
```

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let res: number = storage.size(); // 1
```

## staticClear

```TypeScript
static staticClear(): boolean
```

删除[AppStorage](../../../ui/state-management/arkts-appstorage.md)中所有属性。仅当AppStorage没有任何订阅者时可删除成功并返回true；如果有订阅者， staticClear不会生效并返回false。订阅者的含义参考[delete](#delete)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [Clear](#clear)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 删除AppStorage中所有的属性。仅当没有任何订阅者时删除成功，返回true；如果仍有订阅者，返回false。 |

**示例**

```TypeScript
let clearResult = AppStorage.staticClear();
```
