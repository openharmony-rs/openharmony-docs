# AppStorageV2

AppStorageV2提供应用级全局共享状态变量的能力，开发者可以通过connect绑定同一个key，进行跨Ability的数据共享。具体UI使用说明，详见 [AppStorageV2(应用全局的UI状态存储)](../../../ui/state-management/arkts-new-appstoragev2.md)。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo } from '@kit.ArkUI';
```

## connect

```TypeScript
static connect<T extends object>(
    type: TypeConstructorWithArgs<T>,
    keyOrDefaultCreator?: string | StorageDefaultCreator<T>,
    defaultCreator?: StorageDefaultCreator<T>
  ): T | undefined
```

将键值对数据存储在应用内存中。如果给定的key已经存在于[AppStorageV2](../../../ui/state-management/arkts-new-appstoragev2.md)中，返回对应的值；否则，通过获取 默认值的构造器构造默认值，并返回。

> **说明：**
> 
> 1、若未指定key，使用第二个参数作为默认构造器；否则使用第三个参数（第二个参数非法也使用第三个参数作为默认构造器）。
> 
> 2、确保数据已经存储在AppStorageV2中，可省略默认构造器，获取存储的数据；否则必须指定默认构造器，不指定将导致应用异常。
> 
> 3、同一个key，connect不同类型的数据会导致应用异常，应用需要确保类型匹配。
> 
> 4、key建议使用有意义的值，可由字母、数字、下划线组成，长度不超过255个字符，使用非法字符或空字符的行为是未定义的。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt; | 是 | 指定的类型，若未指定key，则使用type的name作为key。 |
| keyOrDefaultCreator | string \| [StorageDefaultCreator](arkts-arkui-storagedefaultcreator-t.md)&lt;T&gt; | 否 | 指定的key，或者是获取默认值的构造器。默认值为undefined。 |
| defaultCreator | [StorageDefaultCreator](arkts-arkui-storagedefaultcreator-t.md)&lt;T&gt; | 否 | 获取默认值的构造器。默认值为undefined。如果数据未存储在AppStorageV2中，且没有传递默认构造器，则返回 undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T \| undefined | 创建或获取AppStorageV2数据成功时，返回数据；否则返回undefined。 |

**示例**

```TypeScript
import { AppStorageV2 } from '@kit.ArkUI';

@ObservedV2
class SampleClass {
  @Trace value: number = 0;
}

// 将key为SampleClass、value为new SampleClass()对象的键值对存储到内存中，并赋值给sampleData1
const sampleData1: SampleClass | undefined = AppStorageV2.connect(SampleClass, () => new SampleClass());

// 将key为key_as2、value为new SampleClass()对象的键值对存储到内存中，并赋值给sampleData2
const sampleData2: SampleClass = AppStorageV2.connect(SampleClass, 'key_as2', () => new SampleClass())!;

// key为SampleClass已经在AppStorageV2中，将key为SampleClass的值返回给sampleData3
const sampleData3: SampleClass = AppStorageV2.connect(SampleClass) as SampleClass;
```

## keys

```TypeScript
static keys(): Array<string>
```

获取[AppStorageV2](../../../ui/state-management/arkts-new-appstoragev2.md)中的所有key。

> **说明：**
> 
> key在Array中的顺序是无序的，与key插入到AppStorageV2中的顺序无关。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;string & gt; | 所有AppStorageV2中的key。 |

**示例**

```TypeScript
// 假设AppStorageV2中存在两个key（key_as1、key_as2），返回[key_as1、key_as2]赋值给keys
const keys: Array<string> = AppStorageV2.keys();
```

## remove

```TypeScript
static remove<T>(keyOrType: string | TypeConstructorWithArgs<T>): void
```

将指定的键值对数据从[AppStorageV2](../../../ui/state-management/arkts-new-appstoragev2.md)里面删除。如果指定的键值不存在于AppStorageV2中，将删除失 败。

> **说明：**
> 
> 删除AppStorageV2中不存在的key会报警告。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyOrType | string \| [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt; | 是 | 需要删除的key；如果指定的是type类型，删除的key为type的name。 |

**示例**

```TypeScript
// 假设AppStorageV2中存在key为key_as2的键，从AppStorageV2中删除该键值对数据
AppStorageV2.remove('key_as2');

// 假设AppStorageV2中存在key为SampleClass的键，从AppStorageV2中删除该键值对数据
AppStorageV2.remove(SampleClass);

// 假设AppStorageV2中不存在key为key_as1的键，报警告
AppStorageV2.remove('key_as1');
```
