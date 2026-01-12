# 应用级变量的状态管理(ArkTS1.2)

状态管理模块提供了应用程序的数据存储能力、持久化数据管理能力、UIAbility数据存储能力和应用程序需要的环境状态。

>**说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 首批接口从API version 23开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { AppStorage, LocalStorage, PersistentStorage, Environment, LayoutDirection, ColorMode } from '@ohos.arkui.stateManagement';
```

## AppStorage

AppStorage具体UI使用说明，详见[AppStorage(应用全局的UI状态存储)](../../../ui/state-management-static/arkts-static-appstorage.md)

### ref

static ref\<T\>(propName: string): AbstractProperty\<T\>&nbsp;|&nbsp;undefined

如果给定的propName在[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中存在，则获得AppStorage中propName对应数据的引用。否则，返回undefined。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型   | 必填 | 说明               |
| -------- | ------ | ---- | ---------------------- |
| propName | string | 是   | AppStorage中的属性名。 |

**返回值：**

| 类型                                   | 说明                                                         |
| -------------------------------------- | ------------------------------------------------------------ |
| [AbstractProperty&lt;T&gt;](#abstractproperty) \| undefined | AppStorage中propName对应属性的引用，如果AppStorage中不存在对应的propName，则返回undefined。 |

**示例：**

```ts
import { AppStorage, AbstractProperty } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate('PropA', 47);
let refToPropA1: AbstractProperty<int> | undefined = AppStorage.ref<int>('PropA');
let refToPropA2: AbstractProperty<int> | undefined = AppStorage.ref<int>('PropA'); // refToPropA2.get() == 47
refToPropA1?.set(48); // 同步修改AppStorage: refToPropA1.get() == refToPropA2.get() == 48
```

### setAndRef

static setAndRef&lt;T&gt;(propName: string, defaultValue: T): AbstractProperty&lt;T&gt;

与[ref](#ref)接口类似，如果给定的propName在[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中存在，则获得AppStorage中propName对应数据的引用。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，并返回其引用。defaultValue须为T类型，可以为null或undefined。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名       | 类型   | 必填 | 说明                                                     |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | 是   | AppStorage中的属性名。                                       |
| defaultValue | T      | 是   | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化对应的propName，defaultValue可以为null或undefined。 |

**返回值：**

| 类型                      | 说明                                                         |
| ------------------------- | ------------------------------------------------------------ |
| [AbstractProperty&lt;T&gt;](#abstractproperty) | AbstractProperty&lt;T&gt;的实例，为AppStorage中propName对应属性的引用。 |

**示例：**

```ts
import { AppStorage, AbstractProperty } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate('PropA', 47);
let ref1: AbstractProperty<int> = AppStorage.setAndRef<int>('PropB', 49)!; // 用默认值49创建PropB
let ref2: AbstractProperty<int> = AppStorage.setAndRef<int>('PropA', 50)!; // PropA已存在，值为47
```
### link

static link&lt;T&gt;(propName: string): SubscribedAbstractProperty&lt;T&gt;&nbsp;|&nbsp;undefined

与[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中对应的propName建立双向数据绑定。如果给定的propName在AppStorage中存在，返回AppStorage中propName对应属性的双向绑定数据。

双向绑定数据的修改会同步回AppStorage中，AppStorage会将变化同步到所有绑定该propName的数据和自定义组件中。

如果AppStorage中不存在propName，则返回undefined。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明             |
| -------- | ------ | ---- | ---------------- |
| propName | string | 是    | AppStorage中的属性名。 |

**返回值：**

| 类型                                | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| [SubscribedAbstractProperty&lt;T&gt;](#subscribedabstractproperty) \| undefined | 返回双向绑定的数据，如果AppStorage中不存在对应的propName，则返回undefined。 |

**示例：**
```ts
import { AppStorage, SubscribedAbstractProperty } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate('PropA', 47);
let linkToPropA1: SubscribedAbstractProperty<int> = AppStorage.link<int>('PropA')!;
let linkToPropA2: SubscribedAbstractProperty<int> = AppStorage.link<int>('PropA')!; // linkToPropA2.get() == 47
linkToPropA1.set(48); // 双向同步: linkToPropA1.get() == linkToPropA2.get() == 48
```

### setAndLink

static setAndLink&lt;T&gt;(propName: string, defaultValue: T): SubscribedAbstractProperty&lt;T&gt;

与[link](#link)接口类似，如果给定的propName在[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中存在，则返回该propName对应的属性的双向绑定数据。如果不存在，则使用defaultValue在AppStorage中创建和初始化propName对应的属性，返回其双向绑定数据。defaultValue必须为T类型，defaultValue可以为null或undefined。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名       | 类型   | 必填 | 说明                                                     |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | 是   | AppStorage中的属性名。                                       |
| defaultValue | T      | 是   | 当propName在AppStorage中不存在时，使用defaultValue在AppStorage中初始化对应的propName，defaultValue可以为null或undefined。 |

**返回值：**

| 类型                                  | 说明                                       |
| ----------------------------------- | ---------------------------------------- |
| [SubscribedAbstractProperty&lt;T&gt;](#subscribedabstractproperty) | SubscribedAbstractProperty&lt;T&gt;的实例，为AppStorage中propName对应属性的双向绑定的数据。 |

**示例：**
```ts
import { AppStorage, SubscribedAbstractProperty } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropA', 47);
let link1: SubscribedAbstractProperty<int> = AppStorage.setAndLink<int>('PropB', 49); // 用默认值49创建PropB
let link2: SubscribedAbstractProperty<int> = AppStorage.setAndLink<int>('PropA', 50); // PropA已存在，值为47
```

### has

static has(propName: string): boolean

判断propName对应的属性是否在[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中存在。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明             |
| -------- | ------ | ---- | ---------------- |
| propName | string | 是    | AppStorage中的属性名。 |

**返回值：**

| 类型      | 说明                                       |
| ------- | ---------------------------------------- |
| boolean | 如果propName对应的属性在AppStorage中存在，则返回true。不存在则返回false。 |

**示例：**
```ts
import { AppStorage } from '@ohos.arkui.stateManagement';

AppStorage.has('simpleProp');
```

### get

static get&lt;T&gt;(propName: string): T | undefined

获取propName在[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中对应的属性值。如果不存在则返回undefined。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明             |
| -------- | ------ | ---- | ---------------- |
| propName | string | 是    | AppStorage中的属性名。 |

**返回值：**

| 类型                     | 说明                                                        |
| ------------------------ | ----------------------------------------------------------- |
| T&nbsp;\|&nbsp;undefined | AppStorage中propName对应的属性，如果不存在则返回undefined。 |

**示例：**
```ts
import { AppStorage } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropA', 47);
let value: int = AppStorage.get<int>('PropA') as int; // 47
```

### set

static set&lt;T&gt;(propName: string, newValue: T): boolean

在[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中设置propName对应属性的值。如果newValue的值和propName对应属性的值相同，即不需要做赋值操作，状态变量不会通知UI刷新propName对应属性的值，newValue可以为null或undefined。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明                   |
| -------- | ------ | ---- | ---------------------- |
| propName | string | 是    | AppStorage中的属性名。       |
| newValue | T      | 是    | 属性值，开始可以为null或undefined。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 如果AppStorage中不存在propName对应的属性，或设值失败，则返回false。设置成功则返回true。 |

**示例：**
```ts
import { AppStorage } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropA', 48);
let res: boolean = AppStorage.set<int>('PropA', 47) // true
let res1: boolean = AppStorage.set<int>('PropB', 47) // false
```

### setOrCreate

static setOrCreate&lt;T&gt;(propName: string, newValue: T): void

如果propName已经在[AppStorage](../../../ui/state--static/arkts-static-appstorage.md)中存在，并且newValue和propName对应属性的值不同，则设置propName对应属性的值为newValue，否则状态变量不会通知UI刷新propName对应属性的值。
如果propName不存在，则创建propName属性，值为newValue。setOrCreate只可以创建单个AppStorage的键值对，如果想创建多个AppStorage键值对，可以多次调用此方法。newValue可以为null或undefined。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明                   |
| -------- | ------ | ---- | ---------------------- |
| propName | string | 是    | AppStorage中的属性名。       |
| newValue | T      | 是    | 属性值，可以为null或undefined。 |

**示例：**
```ts
import { AppStorage } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('simpleProp', 121);
```

### delete

static delete(propName: string): boolean

在[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中删除propName对应的属性。

在AppStorage中删除该属性的前提是必须保证该属性没有订阅者。如果有订阅者，则返回false。如果没有订阅者，则删除成功并返回true。

属性的订阅者为：

- [\@StorageLink](../../../ui/state-management-static/arkts-static-appstorage.md#storagelink)、[\@StoragePropRef](../../../ui/state-management-static/arkts-static-appstorage.md#storageprop)装饰的变量。

如果想要删除这些订阅者：
需要等待自定义组件回收之后自动释放。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明             |
| -------- | ------ | ---- | ---------------- |
| propName | string | 是    | AppStorage中的属性名。 |

**返回值：**

| 类型      | 说明                                       |
| ------- | ---------------------------------------- |
| boolean | 如果AppStorage中有对应的属性，且该属性已经没有订阅者，则删除成功，返回true。如果属性不存在，或者该属性还存在订阅者，则返回false。 |

**示例：**
```ts
import { AppStorage } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropA', 47);
AppStorage.link<int>('PropA');
let res: boolean = AppStorage.delete('PropA'); // false，PropA 还存在订阅者

AppStorage.setOrCreate<int>('PropB', 48);
let res1: boolean = AppStorage.delete('PropB'); // true，PropB 已从AppStorage成功删除
```

### keys

static keys(): IterableIterator&lt;string&gt;

返回[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中所有的属性名。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                             | 说明                 |
| ------------------------------ | ------------------ |
| IterableIterator&lt;string&gt; | AppStorage中所有的属性名。 |

**示例：**
```ts
import { AppStorage } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropB', 48);
let keys: IterableIterator<string> = AppStorage.keys();
```

### clear

static clear(): boolean

删除[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中所有属性。删除所有属性的前提是，AppStorage已经没有任何订阅者。如果有订阅者，clear将不会生效并返回false。如果没有订阅者，则删除成功，并返回true。

订阅者的含义参考[delete](#delete)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 如果AppStorage中的属性已经没有订阅者则删除成功，返回true；如果当前仍有订阅者，返回false。|

**示例：**
```ts
import { AppStorage } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropA', 47);
let res: boolean = AppStorage.clear(); // true，已经没有订阅者
```

### size

static size(): int

返回[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中的属性数量。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型     | 说明                  |
| ------ | ------------------- |
| int | 返回AppStorage中属性的数量。 |

**示例：**
```ts
import { AppStorage } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropB', 48);
let res: int = AppStorage.size(); // 1
```

## LocalStorage

LocalStorage具体UI使用说明，详见[LocalStorage(页面级UI状态存储)](../../../ui/state-management-static/arkts-static-localstorage.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(initializingProperties?: RecordData)

创建一个新的[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)实例。使用initializingProperties中的属性和其数值，初始化LocalStorage实例。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名                    | 类型     | 必填   | 说明                                     |
| ---------------------- | ------ | ---- | ---------------------------------------- |
| initializingProperties | [RecordData](../../apis-arkts/js-apis-util.md#recorddata20) | 否    | 用initializingProperties包含的属性和数值初始化LocalStorage。initializingProperties不能为undefined。 |

**示例：**
```ts
import { LocalStorage } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(para);
```

### has

has(propName: string): boolean

判断propName对应的属性是否在[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中存在。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明               |
| -------- | ------ | ---- | ------------------ |
| propName | string | 是    | LocalStorage中的属性名。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 如果propName对应的属性在LocalStorage中存在，则返回true。不存在则返回false。 |

**示例：**
```ts
import { LocalStorage } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(para);
storage.has('PropA'); // true
```

### get

get&lt;T&gt;(propName: string): T | undefined

获取propName在[LocalStorage](../../../ui/state-management-static/arkts-staic-localstorage.md)中对应的属性值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明               |
| -------- | ------ | ---- | ------------------ |
| propName | string | 是    | LocalStorage中的属性名。 |

**返回值：**

| 类型                     | 说明                                                         |
| ------------------------ | ------------------------------------------------------------ |
| T&nbsp;\|&nbsp;undefined | LocalStorage中propName对应的属性值，如果不存在则返回undefined。 |

**示例：**
```ts
import { LocalStorage } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47}
let storage: LocalStorage = new LocalStorage(para);
let value: int = storage.get<int>('PropA') as int; // 47
```

### set

set&lt;T&gt;(propName: string, newValue: T): boolean

在[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中设置propName对应属性的值。如果newValue的值和propName对应属性的值相同，即不需要做赋值操作，状态变量不会通知UI刷新propName对应属性的值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明                    |
| -------- | ------ | ---- | ----------------------- |
| propName | string | 是    | LocalStorage中的属性名。      |
| newValue | T      | 是    | 属性值。|

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 如果LocalStorage中不存在propName对应的属性，返回false。设置成功返回true。 |

**示例：**

```ts
import { LocalStorage } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47}
let storage: LocalStorage = new LocalStorage(para);
let res: boolean = storage.set<int>('PropA', 47); // true
let res1: boolean = storage.set<int>('PropB', 47); // false
```

### setOrCreate

setOrCreate&lt;T&gt;(propName: string, newValue: T): boolean

如果propName已经在[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中存在，并且newValue和propName对应属性的值不同，则设置propName对应属性的值为newValue，否则状态变量不会通知UI刷新propName对应属性的值。
如果propName不存在，则创建propName属性，值为newValue。setOrCreate只可以创建单个LocalStorage的键值对，如果想创建多个LocalStorage键值对，可以多次调用此方法。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明                    |
| -------- | ------ | ---- | ----------------------- |
| propName | string | 是    | LocalStorage中的属性名。      |
| newValue | T      | 是    | 属性值。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 如果LocalStorage中存在propName，则更新其值为newValue，返回true。<br/>如果LocalStorage中不存在propName，则创建propName，并初始化其值为newValue，返回true。 |

**示例：**

```ts
import { LocalStorage } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47}
let storage: LocalStorage = new LocalStorage(para);
let res: boolean = storage.setOrCreate<int>('PropA', 121); // true
let res1: boolean = storage.setOrCreate<int | null>('PropB', 111); // true
let res2: boolean = storage.setOrCreate<int | null>('PropB', null); // true 
```

### ref

public ref\<T\>(propName: string): AbstractProperty\<T\>&nbsp;|&nbsp;undefined

如果给定的propName在[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中存在，则获得LocalStorage中propName对应数据的引用。否则，返回undefined。

**参数：**

| 参数名   | 类型   | 必填 | 说明                 |
| -------- | ------ | ---- | ------------------------ |
| propName | string | 是   | LocalStorage中的属性名。 |

**返回值：**

| 类型                                   | 说明                                                         |
| -------------------------------------- | ------------------------------------------------------------ |
| [AbstractProperty&lt;T&gt;](#abstractproperty) \| undefined | LocalStorage中propName对应属性的引用，如果LocalStorage中不存在对应的propName，则返回undefined。 |

**示例：**

```ts
import { LocalStorage, AbstractProperty } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47}
let storage: LocalStorage = new LocalStorage(para);
let refToPropA1: AbstractProperty<int> | undefined = storage.ref<int>('PropA');
let refToPropA2: AbstractProperty<int> | undefined = storage.ref<int>('PropA'); // refToPropA2.get() == 47
refToPropA1?.set(48); // refToPropA1.get() == refToPropA2.get() == 48
```

### setAndRef

public setAndRef&lt;T&gt;(propName: string, defaultValue: T): AbstractProperty&lt;T&gt;

与[ref](#ref-1)接口类似，如果给定的propName在[LocalStorage](../../../ui/state-management-static/arkts--static-localstorage.md)中存在，则获得LocalStorage中propName对应数据的引用。如果不存在，则使用defaultValue在LocalStorage中创建和初始化propName对应的属性，并返回其引用。defaultValue须为T类型，可以为null或undefined。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名       | 类型   | 必填 | 说明                                                     |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | 是   | LocalStorage中的属性名。                                     |
| defaultValue | T      | 是   | 当propName在LocalStorage中不存在时，使用defaultValue在LocalStorage中初始化对应的propName，defaultValue可以为null或undefined。 |

**返回值：**

| 类型                      | 说明                                                         |
| ------------------------- | ------------------------------------------------------------ |
| [AbstractProperty&lt;T&gt;](#abstractproperty) | AbstractProperty&lt;T&gt;的实例，为LocalStorage中propName对应属性的引用。 |

**示例：**

```ts
import { LocalStorage, AbstractProperty } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47}
let storage: LocalStorage = new LocalStorage(para);
let ref1: AbstractProperty<int> = storage.setAndRef<int>('PropB', 49); // 用默认值49创建PropB
let ref2: AbstractProperty<int> = storage.setAndRef<int>('PropA', 50); // PropA已存在，值为47
```

### link

link&lt;T&gt;(propName: string): SubscribedAbstractProperty&lt;T&gt;&nbsp;|&nbsp;undefined

如果给定的propName在[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)实例中存在，则返回与LocalStorage中propName对应属性的双向绑定数据。

双向绑定数据的修改会被同步回LocalStorage中，LocalStorage会将变化同步到所有绑定该propName的数据和Component中。

如果LocalStorage中不存在propName，则返回undefined。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明               |
| -------- | ------ | ---- | ------------------ |
| propName | string | 是    | LocalStorage中的属性名。 |

**返回值：**

| 类型                                | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| [SubscribedAbstractProperty&lt;T&gt;](#subscribedabstractproperty) \| undefined | SubscribedAbstractProperty&lt;T&gt;的实例，与LocalStorage中propName对应属性的双向绑定的数据，如果LocalStorage中不存在对应的propName，则返回undefined。 |

**示例：**
```ts
import { LocalStorage, SubscribedAbstractProperty } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47}
let storage: LocalStorage = new LocalStorage(para);
let linkToPropA1: SubscribedAbstractProperty<int> = storage.link<int>('PropA')!;
let linkToPropA2: SubscribedAbstractProperty<int> = storage.link<int>('PropA')!; // linkToPropA2.get() == 47
linkToPropA1.set(48); // 双向同步: linkToPropA1.get() == linkToPropA2.get() == 48
```

### setAndLink

setAndLink&lt;T&gt;(propName: string, defaultValue: T): SubscribedAbstractProperty&lt;T&gt;

与[link](#link)接口类似，如果给定的propName在[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中存在，则返回该propName对应的属性的双向绑定数据。如果不存在，则使用defaultValue在LocalStorage中创建和初始化propName对应的属性，返回其双向绑定数据。defaultValue必须为T类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名       | 类型   | 必填 | 说明                                                     |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | 是   | LocalStorage中的属性名。                                     |
| defaultValue | T      | 是   | 当propName在LocalStorage中不存在时，使用defaultValue在LocalStorage中初始化对应的propName。 |

**返回值：**

| 类型                                | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| [SubscribedAbstractProperty&lt;T&gt;](#subscribedabstractproperty) | SubscribedAbstractProperty&lt;T&gt;的实例，与LocalStorage中propName对应属性的双向绑定的数据。 |

**示例：**
```ts
import { LocalStorage, SubscribedAbstractProperty } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47}
let storage: LocalStorage = new LocalStorage(para);
let link1: SubscribedAbstractProperty<int> = storage.setAndLink<int>('PropB', 49); // 用默认值49创建PropB
let link2: SubscribedAbstractProperty<int> = storage.setAndLink<int>('PropA', 50); // PropA已存在，值为47
```

### delete

delete(propName: string): boolean

在[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中删除propName对应的属性。在LocalStorage中删除属性的前提是该属性已经没有订阅者，如果有订阅者，则返回false。如果没有订阅者则删除成功并返回true。

属性的订阅者为：
[\@LocalStorageLink](../../../ui/state-management-static/arkts-static-localstorage.md#localstoragelink)、[\@LocalStoragePropRef](../../../ui/state-management-static/arkts-static-localstorage.md#localstorageprop)装饰的变量。

删除订阅者：
需要等待使用\@LocalStorageLink/\@LocalStoragePropRef的自定义组件被垃圾回收。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型     | 必填   | 说明               |
| -------- | ------ | ---- | ------------------ |
| propName | string | 是    | LocalStorage中的属性名。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 如果LocalStorage中有对应的属性，且该属性已经没有订阅者，则删除成功，返回true。如果属性不存在，或者该属性还存在订阅者，则返回false。 |

**示例：**
```ts
import { LocalStorage } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47}
let storage: LocalStorage = new LocalStorage(para);
let res: boolean = storage.delete('PropA'); // false，PropA 还存在订阅者
let res1: boolean = storage.delete('PropB'); // false，PropB 不存在于storage中
storage.setOrCreate<int>('PropB', 48);
let res2: boolean = storage.delete('PropB'); // true，PropB 已从storage成功删除
```

### keys

keys(): IterableIterator&lt;string&gt;

返回[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中所有的属性名。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                             | 说明                   |
| ------------------------------ | -------------------- |
| IterableIterator&lt;string&gt; | LocalStorage中所有的属性名。 |

**示例：**
```ts
import { LocalStorage } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47}
let storage: LocalStorage = new LocalStorage(para);
let keys: IterableIterator<string> = storage.keys();
```

### size

size(): int

返回[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中的属性数量。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型   | 说明                         |
| ------ | ---------------------------- |
| int | LocalStorage中属性的数量。 |

**示例：**
```ts
import { LocalStorage } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47}
let storage: LocalStorage = new LocalStorage(para);
let res: int = storage.size(); // 1
```

### clear

clear(): boolean

删除[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中所有的属性。删除所有属性的前提是已经没有任何订阅者。如果有订阅者，clear不会生效并返回false。如果没有订阅者则删除成功并返回true。

订阅者的含义参考[delete](#delete)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 如果LocalStorage中的属性已经没有任何订阅者，则删除成功，并返回true。否则返回false。 |

**示例：**
```ts
import { LocalStorage } from '@ohos.arkui.stateManagement';

let para: Record<string, Any> = { 'PropA': 47}
let storage: LocalStorage = new LocalStorage(para);
let res: boolean = storage.clear(); // true，已经没有订阅者
```

## AbstractProperty\<T\>

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### get

get(): T

读取[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)/[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中所引用属性的数据。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明                                        |
| ---- | ------------------------------------------- |
| T    | AppStorage/LocalStorage中所引用属性的数据。 |

**示例：**

```ts
import { AppStorage, AbstractProperty } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate('PropA', 47);
let ref1: AbstractProperty<int> | undefined = AppStorage.ref<int>('PropA');
ref1?.get(); //  ref1.get()=47
```

### set

set(newValue: T): void

更新[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)/[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中所引用属性的数据，newValue必须是T类型，可以为null或undefined。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型 | 必填 | 说明                              |
| -------- | ---- | ---- | ------------------------------------- |
| newValue | T    | 是   | 要更新的数据，可以为null或undefined。 |

**示例：**

```ts
import { AppStorage, AbstractProperty } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropA', 47);
let ref1: AbstractProperty<int> | undefined = AppStorage.ref<int>('PropA');
ref1?.set(1); //  ref1.get()=1
let a: Map<string, int> = new Map([['1', 0]]);
let ref2 = AppStorage.setAndRef<Map<string, int>>('MapA', a);
ref2.set(a);
let b: Set<string> = new Set<string>('1');
let ref3 = AppStorage.setAndRef<Set<string>>('SetB', b);
ref3.set(b);
let c: Date = new Date('2024');
let ref4 = AppStorage.setAndRef<Date>('DateC', c);
ref4.set(c);
```

### info

info(): string

读取[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)/[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中所引用属性的属性名。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型   | 说明                                          |
| ------ | --------------------------------------------- |
| string | AppStorage/LocalStorage中所引用属性的属性名。 |

**示例：**

```ts
import { AppStorage, AbstractProperty } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropA', 47);
let ref1: AbstractProperty<int> | undefined = AppStorage.ref<int>('PropA');
ref1?.info(); //  ref1.info()='PropA'
```

### onChange
onChange(onChangeFunc: OnChangeType\<T\> | undefined): void

注册[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)/[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中所引用属性变化的事件。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型 | 必填 | 说明                              |
| -------- | ---- | ---- | ------------------------------------- |
| onChangeFunc | [OnChangeType\<T\>](#onchangetype) \| undefined    | 否   | 属性变化回调函数。</br>如果传入有效值，则添加到监听属性变化的函数列表中。</br>如果传入undefined，则清除所有监听回调。 |

**示例：**

```ts
'use static'
import { AppStorage, AbstractProperty } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<number>('PropA', 47);
let ref1: AbstractProperty<number> | undefined = AppStorage.ref<number>('PropA');
ref1?.onChange((propertyName: string, value: number) => {
  console.info(`ref for ${propertyName} has changed to ${value}.`);
});
```

## SubscribedAbstractProperty

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### get

abstract get(): T

读取从[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)/[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)同步属性的数据。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型   | 说明                              |
| ---- | ------------------------------- |
| T    | AppStorage/LocalStorage同步属性的数据。 |

**示例：**
```ts
import { AppStorage, SubscribedAbstractProperty } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropA', 47); 
let link: SubscribedAbstractProperty<int> = AppStorage.link<int>('PropA')!;    
link.get(); //  prop1.get()=47
```

### set

abstract set(newValue: T): void

设置[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)/[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)同步属性的数据，newValue必须是T类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型 | 必填 | 说明                                                  |
| -------- | ---- | ---- | --------------------------------------------------------- |
| newValue | T    | 是   | 要设置的数据。 |

**示例：**
```ts
import { AppStorage, SubscribedAbstractProperty } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropA', 47);
let link: SubscribedAbstractProperty<int> = AppStorage.link<int>('PropA')!;
link.set(1); //  link.get()=1
```

### aboutToBeDeleted

abstract aboutToBeDeleted(): void

>**说明：**
>
>仅为了和动态Arkts接口保持一致，无实际功能。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**
```ts
import { AppStorage } from '@ohos.arkui.stateManagement';

AppStorage.setOrCreate<int>('PropA', 47);
let link = AppStorage.setAndLink<int>('PropB', 49); // PropA -> 47, PropB -> 49
link.aboutToBeDeleted();
```

### info

info(): string

返回属性名称。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型   |说明     |
|---------|-------------|
|string    |属性名称。    |

## PersistPropsOptions\<T\>

指定持久化属性及其默认值的键值对对象，作为[persistProps](#persistprops)参数传入。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称       | 类型                                  | 只读 | 可选 | 说明                                                     |
| ------------ | ------------------------------------- | --- | ---- | ------------------------------------------------------------ |
| key          | string                                | 否 | 否   | 属性名。                                                     |
| defaultValue | T | 否 | 否 | 当在[PersistentStorage](#PersistentStorage)和[AppStorage](#AppStorage)中未查询到key时，使用defaultValue中。 |
| toJson       | ToJsonType\<T\> | 否 | 是 | 默认值为undefined。见[ToJsonType](#ToJsonType\<T\>)，用于序列化。对于复杂类型（除boolean、int、double、long、string外），开发者必须实现该方法才能成功序列化。|
| fromJson     | FromJsonType\<T\> | 否 | 是 | 默认值为undefined。见[FromJsonType](#FromJsonType\<T\>)，用于反序列化。对于复杂类型（除boolean、int、double、long、string外），开发者必须实现该方法才能成功反序列化。|

## ToJsonType\<T\>

type ToJsonType\<T\> = (value: T) => jsonx.JsonElement

>**说明：**
>
>静态ArkTS序列化接口，需开发者自己实现。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FromJsonType\<T\>

type FromJsonType\<T\> = (element: jsonx.JsonElement) => T

>**说明：**
>
>静态ArkTS反序列化接口，需开发者自己实现。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PersistentStorage

PersistentStorage具体UI使用说明，详见[PersistentStorage(持久化存储UI状态)](../../../ui/state-management-static/arkts-static-persiststorage.md)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### persistProp

static persistProp&lt;T&gt;(key: string, defaultValue: T, ToJson?: ToJsonType\<T\>, fromJson?: FromJsonType\<T\>): boolean

将[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中key对应的属性持久化到文件中。该接口的调用通常在访问AppStorage之前。

确定属性的类型和值的顺序如下：

1. 如果[PersistentStorage](../../../ui/state-management-static/arkts-static-persiststorage.md)文件中存在key对应的属性，则返回false。

2. 如果PersistentStorage文件中没有查询到key对应的属性，则在AppStorage中查找key对应的属性。如果找到key对应的属性，则将该属性持久化，并返回true。

3. 如果AppStorage中也没查找到key对应的属性，则在磁盘中查找key对应的属性。如果找到key对应的属性，则在AppStorage中创建和初始化key对应的属性，并将该属性持久化，最终返回true。

4. 如果磁盘中不存在对应属性，则在AppStorage中创建和初始化key对应的属性，并将该属性持久化，最终返回true。

根据上述的初始化流程，如果AppStorage中有该属性，则会使用其值，覆盖掉PersistentStorage文件中的值。由于AppStorage是内存内数据，该行为会导致数据丧失持久化能力。

4. 对于复杂类型(联合类型都是复杂类型)，开发者必须实现toJson和fromJson才能实现持久化，只有boolean、int、double、long、string，开发者可以不传入toJson和fromJson。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名       | 类型   | 必填 | 说明                                                     |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| key          | string | 是   | 属性名。                                                     |
| defaultValue | T      | 是   | 当在[PersistentStorage](#PersistentStorage)和[AppStorage](#AppStorage)中未查询到key时，使用defaultValue中。|
| toJson       | ToJsonType\<T\> | 否 | 见[ToJsonType](#ToJsonType\<T\>)，用于序列化。对于复杂类型（除boolean、int、double、long、string外），开发者必须实现该方法才能成功序列化。|
| fromJson     | FromJsonType\<T\> | 否 | 见[FromJsonType](#FromJsonType\<T\>)，用于反序列化。对于复杂类型（除boolean、int、double、long、string外），开发者必须实现该方法才能成功反序列化。|

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 如果PersistentStorage文件中存在key对应的属性，则返回false。否则将依次从AppStorage、磁盘中查找对应属性，若存在，则返回true，若不存在，则创建并持久化key对应的属性，并返回true。|

**示例：**

persistProp具体使用，见[从AppStorage中访问PersistentStorage初始化的属性](../../../ui/state-management-static/arkts-static-persiststorage.md#从appstorage中访问persistentstorage初始化的属性)

### deleteProp

static deleteProp(key: string): void

[persistProp](#persistprop)的逆向操作。将key对应的属性从PersistentStorage中删除，后续[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)的操作，对[PersistentStorage](../../../ui/state-management-static/arkts-static-persiststorage.md)不会再有影响。该操作会将对应的key从持久化文件中删除，如果希望再次持久化，可以再次调用[persistProp](#persistprop)接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填   | 说明                    |
| ---- | ------ | ---- | ----------------------- |
| key  | string | 是    | PersistentStorage中的属性名。 |

**示例：**

```ts
import { PersistentStorage } from '@ohos.arkui.stateManagement';

PersistentStorage.deleteProp('highScore');
```

### persistProps

static persistProps(props: PersistPropsOptions\<Any\>[]): void

将[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中key对应的属性持久化到文件中。与[persistProp](#persistprop)的区别在于可以一次性持久化多个数据，适用场景是：应用启动时调用持久化接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名        | 类型                                       | 必填   | 说明                                     |
| ---------- | ---------------------------------------- | ---- | ---------------------------------------- |
| props | [PersistPropsOptions](#persistpropsoptions)[] | 是 | 持久化数组。 |

**示例：**
```ts
import { PersistentStorage } from '@ohos.arkui.stateManagement';

PersistentStorage.persistProps([
  {
    key: 'intVal',
    defaultValue: '55',
  },
  {
    key: 'classVal',
    defaultValue: new Array<string>('1'),
    toJson: (array: Any): jsonx.JsonElement => {
      const root = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
      const arrayEle = new jsonx.JsonElement({} as Record<string, jsonx.JsonElement>);
      (array as Array<string>).forEach((v: string) => {
        arrayEle.setElement(v, jsonx.JsonElement.createString(v));
      });
      root.setElement('array', arrayEle);
      return root;
    }, 
    fromJson: (json: jsonx.JsonElement): Array<string> => {
      let arrayEle: jsonx.JsonElement = json.getElement('array');
      const array: Array<string> = new Array<string>();
      for (let ele of arrayEle) {
        array.push(ele[1].asString());
      }
      return array;
    }
  }
]);
```

### keys

static keys(): Array&lt;string&gt;

返回所有持久化属性的属性名的数组。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                | 说明                               |
| ------------------- | ---------------------------------- |
| Array&lt;string&gt; | 返回所有持久化属性的属性名的数组。 |

**示例：**
```ts
import { PersistentStorage } from '@ohos.arkui.stateManagement';

let keys: Array<string> = PersistentStorage.keys();
```

## EnvPropsOptions

用于指定环境变量名称及其默认值的键值对对象，作为[envProps](#envprops)参数传入。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称       | 类型                        | 必填 | 说明                                                     |
| ------------ | --------------------------- | ---- | ------------------------------------------------------------ |
| key          | string                      | 是   | 环境变量名称，支持的范围详见[内置环境变量说明](#内置环境变量说明)。 |
| defaultValue | int \| long \| double \| string \| boolean | 是   | 查询不到环境变量key，则使用defaultValue作为默认值存入AppStorage中。 |

## Environment

Environment具体使用说明，详见[Environment(设备环境查询)](../../../ui/state-management/arkts-environment.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### envProp

static envProp&lt;T&gt;(key: string, value: T): boolean

将[Environment](../../../ui/state-management/arkts-environment.md)的内置环境变量key存入[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中。如果系统中未查询到Environment环境变量key的值，则使用默认值value，存入成功，返回true。如果AppStorage中已经有对应的key，则返回false。

所以建议在程序启动的时候调用该接口。

在没有调用envProp的情况下，就使用AppStorage读取环境变量是错误的。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                     |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| key    | string | 是   | 环境变量名称，支持的范围详见[内置环境变量说明](#内置环境变量说明)。 |
| value  | T      | 是   | 查询不到环境变量key时，则使用value作为默认值存入AppStorage中。 |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 如果key对应的属性在AppStorage中存在，则返回false。不存在则在AppStorage中用value作为默认值创建key对应的属性，返回true。 |

**示例：**

envProp具体使用，详见[从UI中访问Environment参数](../../../ui/state-management/arkts-environment.md#从ui中访问environment参数)。

### envProps

static envProps(props: EnvPropsOptions[]): void

和[envProp](#envprop)类似，不同点在于参数为数组，可以一次性初始化多个数据。建议在应用启动时调用，将系统环境变量批量存入[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)中。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                          | 必填 | 说明                             |
| ------ | --------------------------------------------- | ---- | ------------------------------------ |
| props  | [EnvPropsOptions](#envpropsoptions)[] | 是   | 系统环境变量和默认值的键值对的数组。 |

**示例：**
```ts
import { Environment } from '@ohos.arkui.stateManagement';

Environment.envProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);
```

### keys

static keys(): Array&lt;string&gt;

返回环境变量的属性key的数组。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                  | 说明          |
| ------------------- | ----------- |
| Array&lt;string&gt; | 返回关联的系统项数组。 |

**示例：**

```ts
Environment.envProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);

let keys: Array<string> = Environment.keys(); // keys 包含 accessibilityEnabled，languageCode，prop
```

## 内置环境变量说明

| key                  | 类型            | 说明                                                         |
| -------------------- | --------------- | ------------------------------------------------------------ |
| accessibilityEnabled | boolean         | 无障碍屏幕朗读是否启用，可选值为：<br/>-&nbsp;true：启用；<br/>-&nbsp;false：不启用。<br/>当无法获取环境变量中的accessibilityEnabled的值时，将通过envProp、envProps等接口传入的开发者指定的默认值添加到AppStorage中。 |
| colorMode            | ColorMode       | 深浅色模式，可选值为：<br/>-&nbsp;ColorMode.LIGHT：浅色模式；<br/>-&nbsp;ColorMode.DARK：深色模式。 |
| fontScale            | int          | 字体大小比例。                                               |
| fontWeightScale      | double          | 字重比例。                                                   |
| layoutDirection      | LayoutDirection | 布局方向类型，可选值为：<br/>-&nbsp;LayoutDirection.LTR：从左到右；<br/>-&nbsp;LayoutDirection.RTL：从右到左。<br/>-&nbsp;Auto：跟随系统。 |
| languageCode         | string          | 当前系统语言，小写字母，例如zh。                             |

### ColorMode

系统当前深浅色模式。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称  | 值    | 说明      |
| ----- | -----| ----------|
| LIGHT | 0    | 浅色模式。 |
| DARK  | 1    | 深色模式。 |


### LayoutDirection

系统的布局方向类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称  | 值    | 说明      |
| ----- | -----| ----------|
| LTR   | 0    | 从左向右布局。 |
| RTL   | 1    | 从右向左布局。 |
| AUTO  | 2    | 自动布局，跟随系统。 |

## OnChangeType
type OnChangeType\<T\> = (propertyName: string, newValue: T) => void

注册[AppStorage](../../../ui/state-management-static/arkts-static-appstorage.md)/[LocalStorage](../../../ui/state-management-static/arkts-static-localstorage.md)中所引用属性变化事件的回调函数类型。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名 | 类型                                          | 必填 | 说明                             |
| ------ | --------------------------------------------- | ---- | ------------------------------------ |
| propertyName  | string | 是   | 修改的属性名称。 |
| newValue      | T      | 是   | 修改后属性的值。 |