# RecoverableStorage

```TypeScript
export declare class RecoverableStorage
```

提供在应用被资源管控终止或异常退出时自动保存与恢复所声明的状态变量的能力。通过[connect](#connect)声明变量后，其值在系统恢复链路的保存时机自动保存，并在下一次恢复重启时自动恢复。

> **说明：** 
> 
> 1. 资源管控终止（如低内存）场景：恢复退后台时保存的值。
> 
> 2. **JS_ERROR**与**APP_FREEZE**异常退出场景：异常发生时刻的值被保存，并在系统自动重启后恢复。前提是应用已调用**enableAppRecovery**（默认参数即可满足）且未注册错误观察者。
> 
> 3. 仅系统携带恢复重启参数拉起的启动会执行恢复。用户手动启动应用始终为冷启动，**connect**返回默认值。

**起始版本：** 26.1.0

<!--Device-unnamed-export declare class RecoverableStorage--><!--Device-unnamed-export declare class RecoverableStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IDefaultReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo, RecoverableStorage, RecoverableConnectOptions, RecoverableStorageError, NotifyOnErrorCallback } from '@kit.ArkUI';
```

## connect

```TypeScript
static connect<T extends object, S extends object>(
    params: RecoverableConnectOptions<T, S>
  ): T
```

声明一个可恢复的状态变量。若该变量已存在（内存或快照中），返回已存的值；否则通过**defaultCreator**构造默认值并返回。

> **说明：** 
> 
> 1. 仅支持对象类型。连接**number**、**string**、**boolean**等简单类型会**抛出**
> **BusinessError(140124)**（与PersistenceV2同款）。
> 
> 2. 同一实例的同一key以相同类型重复连接时，返回已有引用；类型不匹配时**抛出**
> **BusinessError(140124)**。
> 
> 3. 恢复重启时恢复值优先于默认值；恢复失败时返回通过**defaultCreator**构造的默认值，并经
> **notifyOnError**上报错误。
> 
> 4. 典型用法为修改所连接对象的属性。对V1 **\@State**变量整体重新赋值会导致已存引用失效，不被跟踪。
> 
> 5. 变量按**component**获取的窗口级实例ID隔离，不同实例的变量互不影响。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableStorage-static connect<T extends object, S extends object>(    params: RecoverableConnectOptions<T, S>  ): T--><!--Device-RecoverableStorage-static connect<T extends object, S extends object>(    params: RecoverableConnectOptions<T, S>  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [RecoverableConnectOptions](arkts-arkui-arkui-statemanagement-recoverableconnectoptions-c.md)&lt;T, S&gt; | 是 | 连接选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 连接成功时返回恢复值或默认值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 140124 | Unsupported type or parameters. |

## keys

```TypeScript
static keys(component: BaseCustomComponent): Array<string>
```

获取当前实例（以**component**的窗口级实例ID标识）注册的所有可恢复状态变量的key。

> **说明：** 
> 
> key在Array中的顺序是无序的，与key注册的顺序无关。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableStorage-static keys(component: BaseCustomComponent): Array<string>--><!--Device-RecoverableStorage-static keys(component: BaseCustomComponent): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| component | [BaseCustomComponent](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md) | 是 | 自定义组件实例，传入**this**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 当前实例注册的所有key。未注册变量时返回空数组。 |

## remove

```TypeScript
static remove<T>(component: BaseCustomComponent, keyOrType: string | TypeConstructorWithArgs<T>): void
```

注销当前实例（以**component**的窗口级实例ID标识）指定key的可恢复状态变量。注销后该变量不再保存与恢复，再次连接该key时返回默认值。

> **说明：** 
> 
> 注销不存在的key时会报告警告。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-RecoverableStorage-static remove<T>(component: BaseCustomComponent, keyOrType: string | TypeConstructorWithArgs<T>): void--><!--Device-RecoverableStorage-static remove<T>(component: BaseCustomComponent, keyOrType: string | TypeConstructorWithArgs<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| component | [BaseCustomComponent](../arkts-components/arkts-arkui-common-comp-basecustomcomponent-c.md) | 是 | 自定义组件实例，传入**this**。 |
| keyOrType | string &#124; [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt; | 是 | 待注销的key。若传入类型，则注销以该类型名为key的变量。 |
