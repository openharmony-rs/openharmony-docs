# 应用级变量的状态管理（系统接口）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhushilin0206-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->


状态管理模块提供了应用程序的数据存储能力、持久化数据管理能力、UIAbility数据存储能力和环境状态管理能力，适用于跨组件状态共享、数据持久化存储、UIAbility数据管理等场景。


>**说明：**
>
>本模块首批接口从API version 7开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>当前页面仅包含本模块的系统接口，其他公开接口参见[应用级变量的状态管理](./ts-state-management.md)。

## SubscribedAbstractProperty\<T\>

状态管理模块的抽象属性基类，提供属性变化通知和订阅者管理能力，支持创建单向/双向同步属性。

**卡片能力：** 从API version 9开始，支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### subscribers\_

protected subscribers_: Set\<number\>

订阅者集合。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型   |说明       |
|-----------|--------------|
|Set\<number\>  |返回订阅者ID的Set集合。 |

### id\_

private id_

订阅属性的唯一标识ID，用于在订阅关系管理中区分不同的订阅属性实例。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### info\_

private info_?

变量信息，用于标识该订阅关系。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(subscribeMe?: IPropertySubscriber,info?: string)

构造函数。若传入了subscribeMe参数建立了订阅关系，订阅关系不再需要时，应调用[unlinkSuscriber()](#unlinksuscriber)解除订阅（订阅者ID通过[IPropertySubscriber](#ipropertysubscriber).[id()](#id-1)获取）。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|subscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |否   |订阅者，用于接收属性变化通知；不传入则不建立订阅关系。    |
|info   |string   |否   |变量信息，用于标识该订阅关系；不传入时默认为undefined。   |

### id

id(): number

获取ID时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型   |说明       |
|-----------|--------------|
|number  |返回该订阅属性的唯一标识ID。 |

### createTwoWaySync

createTwoWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyTwoWay\<T\>

创建双向同步属性。数据变更在数据源与订阅者之间双向传播。与[createOneWaySync](#createonewaysync)相比，该方法支持数据源与订阅者之间的双向同步，适用于订阅者也需要反向修改数据源的场景；若仅需数据源向订阅者单向同步，请使用[createOneWaySync](#createonewaysync)。订阅关系不再需要时，应调用[unlinkSuscriber()](#unlinksuscriber)解除订阅（订阅者ID通过[IPropertySubscriber](#ipropertysubscriber).[id()](#id-1)获取），或由返回的[SyncedPropertyTwoWay](#syncedpropertytwowayt)对象的[aboutToBeDeleted()](#abouttobedeleted-1)方法处理取消订阅。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|subscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |否   |订阅者，用于接收属性变化通知；不传入则不建立订阅关系。    |
|info   |string   |否   |变量信息，用于标识该订阅关系；不传入时默认为undefined。   |

**返回值：**

|类型   |说明       |
|-----------|--------------|
|[SyncedPropertyTwoWay\<T\>](#syncedpropertytwowayt)  |返回创建的双向同步属性对象，用于在数据源与订阅者之间进行双向数据同步和读写操作。 |

### createOneWaySync

createOneWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyOneWay\<T\>

创建单向同步属性。数据变更仅从数据源向订阅者单向传播。订阅关系不再需要时，应调用[unlinkSuscriber()](#unlinksuscriber)解除订阅（订阅者ID通过[IPropertySubscriber](#ipropertysubscriber).[id()](#id-1)获取），或由返回的[SyncedPropertyOneWay](#syncedpropertyonewayt)对象的[aboutToBeDeleted()](#abouttobedeleted-2)方法处理取消订阅。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|subscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |否   |订阅者，用于接收属性变化通知；不传入则不建立订阅关系。    |
|info   |string   |否   |变量信息，用于标识该订阅关系；不传入时默认为undefined。   |

**返回值：**

|类型   |说明       |
|-----------|--------------|
|[SyncedPropertyOneWay\<T\>](#syncedpropertyonewayt)  |返回创建的单向同步属性对象，用于接收父组件状态值的单向同步，当父组件状态变化时更新自身值。 |

### unlinkSuscriber

unlinkSuscriber(subscriberId: number): void

根据订阅者ID解除订阅时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|subscriberId   |number   |是   |要解除订阅的订阅者ID，需为已通过[createTwoWaySync](#createtwowaysync)或[createOneWaySync](#createonewaysync)建立订阅关系的订阅者ID，通过[IPropertySubscriber](#ipropertysubscriber).[id()](#id-1)方法获取。    |

### notifyHasChanged

protected notifyHasChanged(newValue: T): void

通知变化时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|newValue   |T   |是   |更改后的新值。    |

### notifyPropertyRead

protected notifyPropertyRead(): void

通知读取时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### numberOfSubscrbers

numberOfSubscrbers(): number

获取订阅者数量时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型   |说明       |
|-----------|--------------|
|number  |返回订阅者数量。 |

## IPropertySubscriber

属性订阅者接口，定义订阅者需要实现的方法，用于接收属性变化通知和生命周期回调。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### id

id(): number

获取ID时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型   |说明       |
|-----------|--------------|
|number  |返回订阅者的唯一标识ID。 |

### aboutToBeDeleted

aboutToBeDeleted(owningView?: IPropertySubscriber): void

销毁时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|owningView   |[IPropertySubscriber](#ipropertysubscriber)   |否   |所在自定义组件；不传入则不指定关联的自定义组件。    |

## SyncedPropertyTwoWay\<T\>

继承自[SubscribedAbstractProperty\<T\>](#subscribedabstractpropertyt)。用于实现父子组件之间的双向状态数据同步。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### source\_

private source_

双向同步属性的数据源。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(source: SubscribedAbstractProperty\<T\>, subscribeMe?: IPropertySubscriber, info?: string)

构造函数。订阅关系不再需要时，应调用[unlinkSuscriber()](#unlinksuscriber)解除订阅（订阅者ID通过[IPropertySubscriber](#ipropertysubscriber).[id()](#id-1)获取），或调用本对象的[aboutToBeDeleted()](#abouttobedeleted-1)方法处理取消订阅。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|source   |[SubscribedAbstractProperty\<T\>](#subscribedabstractpropertyt)   |是   |双向同步属性的数据源。    |
|subscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |否   |订阅者，用于接收属性变化通知；不传入则不建立订阅关系。   |
|info  |string   |否   |变量信息，用于标识该订阅关系；不传入时默认为undefined。   |

### aboutToBeDeleted

aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void

销毁时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|unsubscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |否   |被取消的订阅者，需为已订阅的订阅者；不传入则取消所有订阅者。    |

### hasChanged

hasChanged(newValue: T): void

变化时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明   |
|---------|-----------|------------|--------------|
|newValue   |T   |是   |更改后的新值。     |

### get

get(): T

获取数据时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型   |说明     |
|------|------------|
|T   |返回双向同步属性当前的数据值。    |

### set

set(newValue: T): void

赋值时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|newValue   |T   |是   |要设置的新值。    |

## SyncedPropertyOneWay\<T\>

继承自[SubscribedAbstractProperty\<T\>](#subscribedabstractpropertyt)。用于接收父组件状态值的单向同步，当父组件状态变化时更新自身值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### wrappedValue\_

private wrappedValue_

单向绑定时的值。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### source\_

private source_

单向同步属性的数据源。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(source: SubscribedAbstractProperty\<T\>, subscribeMe?: IPropertySubscriber, info?: string)

构造函数。订阅关系不再需要时，应调用[unlinkSuscriber()](#unlinksuscriber)解除订阅（订阅者ID通过[IPropertySubscriber](#ipropertysubscriber).[id()](#id-1)获取），或调用本对象的[aboutToBeDeleted()](#abouttobedeleted-2)方法处理取消订阅。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|source   |[SubscribedAbstractProperty\<T\>](#subscribedabstractpropertyt)   |是   |单向同步属性的数据源。    |
|subscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |否   |订阅者，用于接收属性变化通知；不传入则不建立订阅关系。   |
|info  |string   |否   |变量信息，用于标识该订阅关系；不传入时默认为undefined。   |

### aboutToBeDeleted

aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void

销毁时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|unsubscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |否   |被取消的订阅者，需为已订阅的订阅者；不传入则取消所有订阅者。    |

### hasChanged

hasChanged(newValue: T): void

变化时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明   |
|---------|-----------|------------|--------------|
|newValue   |T   |是   |更改后的新值。     |

### get

get(): T

获取数据时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型   |说明     |
|------|------------|
|T   |返回单向同步属性当前的数据值。    |

### set

set(newValue: T): void

赋值时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|newValue   |T   |是   |要设置的新值。    |

## ISinglePropertyChangeSubscriber\<T\>

继承自[IPropertySubscriber](#ipropertysubscriber)。用于订阅单个属性值的变化，当被订阅的属性发生变化时接收通知。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### hasChanged

hasChanged(newValue: T): void

变化时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|newValue   |T   |是   |更改后的新值。    |

## SubscribaleAbstract

可订阅抽象类，用于管理所持有的属性集合，提供属性的添加、删除和变更通知能力。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### owningProperties\_

private owningProperties_: Set\<number\>

所持有的属性集合。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型   |说明     |
|------|------------|
|Set\<number\>   |返回所持有属性的订阅者ID的Set集合。    |

### constructor

constructor()

构造函数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### notifyPropertyHasChanged

protected notifyPropertyHasChanged(propName: string, newValue: any): void

通知属性更改时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|propName   |string   |是   |要通知变更的属性名称。    |
|newValue   |any   |是   |更改后的新值。   |

### addOwningProperty

public addOwningProperty(subscriber: IPropertySubscriber): void

添加持有的属性。属性不再使用时，应调用[removeOwningProperty](#removeowningproperty)或[removeOwningPropertyById](#removeowningpropertybyid)移除。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|subscriber   |[IPropertySubscriber](#ipropertysubscriber)   |是   |要添加的订阅者，该订阅者将接收属性变化通知。    |

### removeOwningProperty

public removeOwningProperty(property: IPropertySubscriber): void

删除持有的属性时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|property   |[IPropertySubscriber](#ipropertysubscriber)   |是   |要删除的订阅者，需为已通过[addOwningProperty](#addowningproperty)添加的订阅者。    |

### removeOwningPropertyById

public removeOwningPropertyById(subscriberId: number): void

使用ID删除持有的属性时调用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|subscriberId   |number   |是   |要删除的订阅者ID，需为已通过[addOwningProperty](#addowningproperty)添加的订阅者ID，通过[IPropertySubscriber](#ipropertysubscriber).[id()](#id-1)方法获取。    |

## Environment

环境类，用于管理应用程序运行时的环境状态，提供对设备环境属性的访问能力。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor()

构造函数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PersistentStorage

持久化存储类，用于管理应用程序的持久化数据，可将指定的AppStorage属性与持久化存储关联，实现数据的持久化保存和恢复。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(appStorage: AppStorage, storage: Storage)

构造函数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名   |类型   |必填   |说明             |
|---------|-----------|------------|--------------|
|appStorage   |AppStorage   |是   |应用级存储对象，PersistentStorage将基于此对象进行持久化管理。    |
|storage   |Storage   |是   |持久化存储对象，用于实际读写持久化数据。    |

## appStorage

declare const appStorage: AppStorage

应用级全局状态存储实例，提供应用范围内的状态数据存储和访问能力。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

|类型    |说明          |
|----------|------------|
|AppStorage   |应用级全局状态存储实例。  |