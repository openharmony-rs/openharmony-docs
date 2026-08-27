# SubscribedAbstractProperty

SubscribedAbstractProperty是[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中属性的单/双向同步绑定对象，用于与AppStorage/LocalStorage中的属性建立数据同 步关系。SubscribedAbstractProperty实例需要通过[aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#abouttobedeleted)接口手动释放，以取消同步 关系并无效化实例。

> **说明：**
> 
> 从API version 12开始，AppStorage/LocalStorage支持Map、Set、Date类型，支持null、undefined以及联合类型。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(
    /**
     * 订阅者，用于接收属性变化通知；不传入则不建立订阅关系。
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @systemapi
     * @since 7
     * 
     */
    subscribeMe?: IPropertySubscriber,
    /**
     * 变量信息，用于标识该订阅关系；不传入时默认为undefined。
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @systemapi
     * @since 7
     * 
     */
    info?: string,
  )
```

构造函数。若传入了subscribeMe参数建立了订阅关系，订阅关系不再需要时，应调用[unlinkSuscriber()](#unlinksuscriber)解除 订阅（订阅者ID通过[IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id)获取）。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeMe | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | 否 | 订阅者，用于接收属性变化通知；不传入则不建立订阅关系。 |
| info | string | 否 | 变量信息，用于标识该订阅关系；不传入时默认为undefined。 |

**示例**

```TypeScript
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
```

## createOneWaySync

```TypeScript
createOneWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyOneWay<T>
```

创建单向同步属性。数据变更仅从数据源向订阅者单向传播。订阅关系不再需要时，应调用[unlinkSuscriber()](#unlinksuscriber)解除 订阅（订阅者ID通过[IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id)获取）， 或由返回的[SyncedPropertyOneWay](arkts-arkui-syncedpropertyoneway-c-sys.md)对象 的[aboutToBeDeleted()](arkts-arkui-syncedpropertyoneway-c-sys.md#abouttobedeleted)方法处理取消订阅。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeMe | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | 否 | 订阅者，用于接收属性变化通知；不传入则不建立订阅关系。 |
| info | string | 否 | 变量信息，用于标识该订阅关系；不传入时默认为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SyncedPropertyOneWay](arkts-arkui-syncedpropertyoneway-c-sys.md)&lt;T&gt; | 返回创建的单向同步属性对象，用于接收父组件状态值的单向同步，当父组件状态变化时更新自身值。 |

## createTwoWaySync

```TypeScript
createTwoWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyTwoWay<T>
```

创建双向同步属性。数据变更在数据源与订阅者之间双向传播。与[createOneWaySync](#createonewaysync)相比，该方法支持 数据源与订阅者之间的双向同步，适用于订阅者也需要反向修改数据源的场景；若仅需数据源向订阅者单向同步， 请使用[createOneWaySync](#createonewaysync)。订阅关系不再需要时， 应调用[unlinkSuscriber()](#unlinksuscriber)解除订阅（订阅者ID 通过[IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id)获取）， 或由返回的[SyncedPropertyTwoWay](arkts-arkui-syncedpropertytwoway-c-sys.md)对象 的[aboutToBeDeleted()](arkts-arkui-syncedpropertytwoway-c-sys.md#abouttobedeleted)方法处理取消订阅。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeMe | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | 否 | 订阅者，用于接收属性变化通知；不传入则不建立订阅关系。 |
| info | string | 否 | 变量信息，用于标识该订阅关系；不传入时默认为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SyncedPropertyTwoWay](arkts-arkui-syncedpropertytwoway-c-sys.md)&lt;T&gt; | Two-way synchronized property. |

## id

```TypeScript
id(): number
```

获取ID时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回该订阅属性的唯一标识ID。 |

## notifyHasChanged

```TypeScript
protected notifyHasChanged(newValue: T): void
```

通知变化时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | 更改后的新值。 |

## notifyPropertyRead

```TypeScript
protected notifyPropertyRead(): void
```

通知读取时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## numberOfSubscrbers

```TypeScript
numberOfSubscrbers(): number
```

获取订阅者数量时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回订阅者数量。 |

## unlinkSuscriber

```TypeScript
unlinkSuscriber(subscriberId: number): void
```

根据订阅者ID解除订阅时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriberId | number | 是 | 要解除订阅的订阅者ID，需为已通过[createTwoWaySync](#createtwowaysync) 或[createOneWaySync](#createonewaysync)建立订阅关系的订阅者ID， 通过[IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id)方法获取。 |

## id_

```TypeScript
private id_
```

订阅属性的唯一标识ID，用于在订阅关系管理中区分不同的订阅属性实例。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## info_

```TypeScript
private info_?
```

变量信息，用于标识该订阅关系。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## subscribers_

```TypeScript
protected subscribers_: Set<number>
```

订阅者集合。

**类型：** Set&lt;number&gt;

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
