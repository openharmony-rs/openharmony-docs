# SyncedPropertyTwoWay(System API)（系统接口）

继承自[SubscribedAbstractProperty\&lt;T\&gt;](arkts-arkui-subscribedabstractproperty-c.md)。用于实现父子组件之间的双向状态数据同步。

**继承/实现关系：** SyncedPropertyTwoWay extends SubscribedAbstractProperty<T> implements ISinglePropertyChangeSubscriber<T>

**起始版本：** 7

<!--Device-unnamed-declare class SyncedPropertyTwoWay--><!--Device-unnamed-declare class SyncedPropertyTwoWay-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## aboutToBeDeleted

```TypeScript
aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void
```

销毁时调用。

**起始版本：** 7

<!--Device-SyncedPropertyTwoWay-aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void--><!--Device-SyncedPropertyTwoWay-aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unsubscribeMe | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | 否 | 被取消的订阅者，需为已订阅的订阅者；不传入则取消所有订阅者。 |

## constructor

```TypeScript
constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)
```

构造函数。订阅关系不再需要时，应调用[unlinkSuscriber()](arkts-arkui-subscribedabstractproperty-c-sys.md#unlinksuscriber)解除 订阅（订阅者ID通过[IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id)获取）， 或调用本对象的[aboutToBeDeleted()](#abouttobedeleted)方法处理取消订阅。

**起始版本：** 7

<!--Device-SyncedPropertyTwoWay-constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)--><!--Device-SyncedPropertyTwoWay-constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | 是 | 双向同步属性的数据源。 |
| subscribeMe | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | 否 | 订阅者，用于接收属性变化通知；不传入则不建立订阅关系。 |
| info | string | 否 | 变量信息，用于标识该订阅关系；不传入时默认为undefined。 |

## get

```TypeScript
get(): T
```

获取数据时调用。

**起始版本：** 7

<!--Device-SyncedPropertyTwoWay-get(): T--><!--Device-SyncedPropertyTwoWay-get(): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回双向同步属性当前的数据值。 |

## hasChanged

```TypeScript
hasChanged(newValue: T): void
```

变化时调用。

**起始版本：** 7

<!--Device-SyncedPropertyTwoWay-hasChanged(newValue: T): void--><!--Device-SyncedPropertyTwoWay-hasChanged(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | 更改后的新值。 |

## set

```TypeScript
set(newValue: T): void
```

赋值时调用。

**起始版本：** 7

<!--Device-SyncedPropertyTwoWay-set(newValue: T): void--><!--Device-SyncedPropertyTwoWay-set(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | 要设置的新值。 |

## source_

```TypeScript
private source_
```

双向同步属性的数据源。

**起始版本：** 7

<!--Device-SyncedPropertyTwoWay-private source_--><!--Device-SyncedPropertyTwoWay-private source_-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

