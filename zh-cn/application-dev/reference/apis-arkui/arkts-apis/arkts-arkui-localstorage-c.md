# LocalStorage

LocalStorage是页面级的UI状态存储，通过[@Entry](../../../reference/apis-arkui/arkui-ts/ts-universal-entry.md#entry)装饰器接收的参数可以在页面内 共享同一个LocalStorage实例。具体UI使用说明，详见[LocalStorage：页面级UI状态存储](../../../ui/state-management/arkts-localstorage.md)。 > **说明：** > > 从API version 12开始，LocalStorage支持[Map](../../../ui/state-management/arkts-localstorage.md#装饰map类型变量)、 > [Set](../../../ui/state-management/arkts-localstorage.md#装饰set类型变量)、 > [Date类型](../../../ui/state-management/arkts-localstorage.md#装饰date类型变量)，支持null、undefined以及 > [联合类型](../../../ui/state-management/arkts-localstorage.md#localstorage支持联合类型)。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-unnamed-declare class LocalStorage--><!--Device-unnamed-declare class LocalStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## GetShared

```TypeScript
static GetShared(): LocalStorage
```

获取当前Stage共享的[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 10

**替代接口：** getShared

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-static GetShared(): LocalStorage--><!--Device-LocalStorage-static GetShared(): LocalStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocalStorage](arkts-arkui-localstorage-c.md) | 返回当前Stage共享的LocalStorage实例。 |

## 示例

```TypeScript
let storage: LocalStorage = LocalStorage.GetShared();
```

## clear

```TypeScript
clear(): boolean
```

删除[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中所有的属性。仅当LocalStorage中的属性没有任何订阅者时可删除成功并返回true； 如果有订阅者，clear不会生效并返回false。 订阅者的含义参考[delete](#delete)。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-clear(): boolean--><!--Device-LocalStorage-clear(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果LocalStorage中的属性已经没有任何订阅者，则删除成功，并返回true。否则返回false。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let res: boolean = storage.clear(); // true，已经没有订阅者
```

## constructor

```TypeScript
constructor(initializingProperties?: Object)
```

创建一个新的[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例。使用Object.keys(initializingProperties)返回 的属性名及其值，初始化LocalStorage实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-constructor(initializingProperties?: Object)--><!--Device-LocalStorage-constructor(initializingProperties?: Object)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| initializingProperties | Object | 否 | 用于初始化LocalStorage，当需要在创建时预置属性数据时传入此参数。其键作为LocalStorage中的属性名，值为对应属性的初始 值。initializingProperties不能为undefined。不传入时默认值为空对象，LocalStorage中不包含任何预置属性。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
```

## delete

```TypeScript
delete(propName: string): boolean
```

在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中删除propName对应的属性。仅当LocalStorage中该属性没有任何订阅者时可删除成 功并返回true；如果有订阅者，则返回false。 属性的订阅者为： 1. [@LocalStorageLink](../../../ui/state-management/arkts-localstorage.md#localstoragelink)、[@LocalStorageProp](../../../ui/state-management/arkts-localstorage.md#localstorageprop)装饰的变量。 2. 通过[link](#link)、[prop](#prop)、[setAndLink](#setAndLink)、[setAndProp](#setAndProp)接口返回的[SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md#SubscribedAbstractProperty（系统接口）)的实例。 如需删除这些订阅者，可通过以下方式： 1. 删除\@LocalStorageLink、\@LocalStorageProp所在的自定义组件。删除自定义组件请参考[自定义组件的删除](../../../ui/state-management/arkts-page-custom-components-lifecycle.md#自定义组件的删除)。 2. 对link、prop、setAndLink、setAndProp接口返回的SubscribedAbstractProperty的实例调用[aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#aboutToBeDeleted)接口。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

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

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
storage.link<number>('PropA');
let res: boolean = storage.delete('PropA'); // false，PropA 还存在订阅者
let res1: boolean = storage.delete('PropB'); // false，PropB 不存在于storage中
storage.setOrCreate('PropB', 48);
let res2: boolean = storage.delete('PropB'); // true，PropB 已从storage成功删除
```

## get

```TypeScript
get<T>(propName: string): T | undefined
```

获取propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中对应的属性值。如果不存在则返回undefined。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

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
| T | LocalStorage中propName对应的属性值，如果不存在则返回undefined。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let value: number = storage.get('PropA') as number; // 47
```

## getShared

```TypeScript
static getShared(): LocalStorage
```

获取当前Stage共享的[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例。 > **说明：** > > 从API version 12开始，可使用[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md#UIContext)中的 > [getSharedLocalStorage](arkts-arkui-arkui-uicontext-uicontext-c.md#getSharedLocalStorage)明确UI执行上下文中的LocalStorage实例。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 18

**替代接口：** [getSharedLocalStorage](arkts-arkui-arkui-uicontext-uicontext-c.md#getSharedLocalStorage)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-static getShared(): LocalStorage--><!--Device-LocalStorage-static getShared(): LocalStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LocalStorage](arkts-arkui-localstorage-c.md) | 返回当前Stage共享的LocalStorage实例。 |

## has

```TypeScript
has(propName: string): boolean
```

判断propName对应的属性是否在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

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

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
storage.has('PropA'); // true
```

## keys

```TypeScript
keys(): IterableIterator<string>
```

返回[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中所有的属性名。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-keys(): IterableIterator<string>--><!--Device-LocalStorage-keys(): IterableIterator<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;string&gt; | LocalStorage中所有的属性名。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let keys: IterableIterator<string> = storage.keys();
```

## link

```TypeScript
link<T>(propName: string): SubscribedAbstractProperty<T>
```

如果给定的propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)实例中存在，则返回与LocalStorage中propName对应属 性的双向绑定数据。与[prop](#prop)的单向数据绑定不同，link建立双向数据绑定，修改会同步回LocalStorage，LocalStorage会将变化同步到所有绑定该propName 的数据和自定义组件中。 如果LocalStorage中不存在propName，则返回undefined。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

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
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | SubscribedAbstractProperty&lt;T&gt;的实例，与LocalStorage中propName对应属性的双向绑定的数据，如果 LocalStorage中不存在对应的propName，则返回undefined。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let linkToPropA1: SubscribedAbstractProperty<number> = storage.link('PropA');
let linkToPropA2: SubscribedAbstractProperty<number> = storage.link('PropA'); // linkToPropA2.get() == 47
linkToPropA1.set(48); // 双向同步：linkToPropA1.get() == linkToPropA2.get() == 48
```

## prop

```TypeScript
prop<S>(propName: string): SubscribedAbstractProperty<S>
```

如果给定的propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在，则返回与LocalStorage中propName对应属性的 单向绑定数据。如果LocalStorage中不存在propName，则返回undefined。单向绑定数据的修改不会同步回LocalStorage中。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

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
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;S&gt; | SubscribedAbstractProperty&lt;S&gt;的实例，为LocalStorage中propName对应属性的单向绑定的数据。如果 LocalStorage中不存在对应的propName，则返回undefined。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let prop1: SubscribedAbstractProperty<number> = storage.prop('PropA');
let prop2: SubscribedAbstractProperty<number> = storage.prop('PropA');
prop1.set(1); // 单向同步：prop1.get()的值为1，prop2.get()的值为47
```

## ref

```TypeScript
public ref<T>(propName: string): AbstractProperty<T> | undefined
```

如果给定的propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在，则返回LocalStorage中propName对应属性的引 用。否则，返回undefined。 与[link](#link)的功能基本一致，区别在于不需要手动释放返回的[AbstractProperty&lt;T&gt;](arkts-arkui-abstractproperty-i.md#AbstractProperty)类型的变量。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

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
| [AbstractProperty](arkts-arkui-abstractproperty-i.md)&lt;T&gt; | 返回LocalStorage中propName对应属性的引用，如果LocalStorage中不存在对应的propName，则返回 undefined。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let refToPropA1: AbstractProperty<number> | undefined = storage.ref('PropA');
let refToPropA2: AbstractProperty<number> | undefined = storage.ref('PropA'); // refToPropA2.get() == 47
refToPropA1?.set(48); // refToPropA1.get() == refToPropA2.get() == 48
```

## set

```TypeScript
set<T>(propName: string, newValue: T): boolean
```

在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中设置propName对应属性的值。如果newValue与propName对应属性的值相同，则 不做赋值操作，状态变量不会通知UI刷新propName对应属性的值。与[setOrCreate](#setOrCreate)不同，set仅在propName已存在时生效，propName不存在时 返回false。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-set<T>(propName: string, newValue: T): boolean--><!--Device-LocalStorage-set<T>(propName: string, newValue: T): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |
| newValue | T | 是 | propName对应属性的新值，从API version 12开始可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果LocalStorage中不存在propName对应的属性，返回false。设置成功返回true。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let res: boolean = storage.set('PropA', 47); // true
let res1: boolean = storage.set('PropB', 47); // false
```

## setAndLink

```TypeScript
setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

与[link](#link)接口类似，如果给定的propName在 [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在，则返回该propName对应的属性的双向绑定数据。如果不存在，则使用 defaultValue在LocalStorage中创建和初始化propName对应的属性，返回其双向绑定数据。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-LocalStorage-setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在LocalStorage中不存在时，使用defaultValue在LocalStorage中初始化propName对应属性的值。从API version 12开始，defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | SubscribedAbstractProperty&lt;T&gt;的实例，与LocalStorage中propName对应属性的双向绑定的数据。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let link1: SubscribedAbstractProperty<number> = storage.setAndLink('PropB', 49); // 用默认值49创建PropB
let link2: SubscribedAbstractProperty<number> = storage.setAndLink('PropA', 50); // PropA已存在，值为47
```

## setAndProp

```TypeScript
setAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>
```

与[prop](#prop)接口类似，如果给定的propName在 [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在，则返回该propName对应的属性的单向绑定数据。如果不存在，则使用 defaultValue在LocalStorage中创建和初始化propName对应的属性，返回其单向绑定数据。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-setAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>--><!--Device-LocalStorage-setAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |
| defaultValue | S | 是 | 当propName在LocalStorage中不存在时，使用defaultValue在LocalStorage中初始化propName对应属性的值。从API version 12开始，defaultValue可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;S&gt; | SubscribedAbstractProperty&lt;S&gt;的实例，为LocalStorage中propName对应属性的单向绑定的数据。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let prop: SubscribedAbstractProperty<number> = storage.setAndProp('PropB', 49); // PropA -> 47, PropB -> 49
```

## setAndRef

```TypeScript
public setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>
```

与[ref](arkts-arkui-appstorage-c.md#ref)接口类似，如果给定的propName在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中 存在，则返回LocalStorage中propName对应属性的引用。如果不存在，则使用defaultValue在LocalStorage中创建和初始化propName对应的属性，并返回其引用。 与[setAndLink](#setAndLink)的功能基本一致，区别在于不需要手动释放返回的 [AbstractProperty&lt;T&gt;](arkts-arkui-abstractproperty-i.md#AbstractProperty)类型的变量。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LocalStorage-public setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>--><!--Device-LocalStorage-public setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |
| defaultValue | T | 是 | 当propName在LocalStorage中不存在时，使用defaultValue在LocalStorage中初始化propName对应属性的值，defaultValue可 以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbstractProperty](arkts-arkui-abstractproperty-i.md)&lt;T&gt; | AbstractProperty&lt;T&gt;的实例，为LocalStorage中propName对应属性的引用。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let ref1: AbstractProperty<number> = storage.setAndRef('PropB', 49); // 用默认值49创建PropB
let ref2: AbstractProperty<number> = storage.setAndRef('PropA', 50); // PropA已存在，值为47
```

## setOrCreate

```TypeScript
setOrCreate<T>(propName: string, newValue: T): boolean
```

如果propName已经在[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中存在，并且newValue和propName对应属性的值不同，则设置 propName对应属性的值为newValue，否则状态变量不会通知UI刷新propName对应属性的值。 如果propName不存在，则创建propName属性，值为newValue。setOrCreate仅可创建单个LocalStorage的键值对，如需创建多个LocalStorage键值对，可多次调用此方法。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-setOrCreate<T>(propName: string, newValue: T): boolean--><!--Device-LocalStorage-setOrCreate<T>(propName: string, newValue: T): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propName | string | 是 | LocalStorage中的属性名。 |
| newValue | T | 是 | propName对应属性的新值，从API version 12开始可以为null或undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果LocalStorage中存在propName，则更新其值为newValue，返回true。 &lt;br&gt;如果LocalStorage中不存在propName，则创建propName，并初始化其值为newValue，返回true。 &lt;br&gt;API version 12之前，当newValue为null或undefined时返回false。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let res: boolean = storage.setOrCreate('PropA', 121); // true
let res1: boolean = storage.setOrCreate('PropB', 111); // true
let res2: boolean = storage.setOrCreate('PropB', null); // true（API version 12及之后返回true，API version 11及之前返回false）
```

## size

```TypeScript
size(): number
```

返回[LocalStorage](../../../ui/state-management/arkts-localstorage.md)中的属性数量。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-LocalStorage-size(): number--><!--Device-LocalStorage-size(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | LocalStorage中属性的数量。 |

## 示例

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let res: number = storage.size(); // 1
```

