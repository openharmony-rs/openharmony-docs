# SyncedPropertyOneWay（系统接口）

继承自[SubscribedAbstractProperty<T>](arkts-arkui-common-ts-ets-api-subscribedabstractproperty-c-sys.md)。用来定义父组件的状态值。

**继承/实现关系：** SyncedPropertyOneWay extends [SubscribedAbstractProperty<T>](SubscribedAbstractProperty<T>) implements [ISinglePropertyChangeSubscriber<T>](ISinglePropertyChangeSubscriber<T>)

**起始版本：** 7

<!--Device-unnamed-declare class SyncedPropertyOneWay<T> extends SubscribedAbstractProperty<T>  implements ISinglePropertyChangeSubscriber<T>--><!--Device-unnamed-declare class SyncedPropertyOneWay<T> extends SubscribedAbstractProperty<T>  implements ISinglePropertyChangeSubscriber<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## aboutToBeDeleted

```TypeScript
aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void
```

销毁时调用。

**起始版本：** 7

<!--Device-SyncedPropertyOneWay-aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void--><!--Device-SyncedPropertyOneWay-aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unsubscribeMe | [IPropertySubscriber](arkts-arkui-common-ts-ets-api-ipropertysubscriber-i-sys.md) | 否 | 被取消的订阅者。 |

## constructor

```TypeScript
constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)
```

构造函数。

**起始版本：** 7

<!--Device-SyncedPropertyOneWay-constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)--><!--Device-SyncedPropertyOneWay-constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [SubscribedAbstractProperty](arkts-arkui-common-ts-ets-api-subscribedabstractproperty-c-sys.md)<T> | 是 | 单向同步属性的数据源。 |
| subscribeMe | [IPropertySubscriber](arkts-arkui-common-ts-ets-api-ipropertysubscriber-i-sys.md) | 否 | 订阅者。 |
| info | string | 否 | 订阅者信息。 |

## get

```TypeScript
get(): T
```

获取数据源时调用。

**起始版本：** 7

<!--Device-SyncedPropertyOneWay-get(): T--><!--Device-SyncedPropertyOneWay-get(): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | - T类型实例。 |

## hasChanged

```TypeScript
hasChanged(newValue: T): void
```

变化时调用。

**起始版本：** 7

<!--Device-SyncedPropertyOneWay-hasChanged(newValue: T): void--><!--Device-SyncedPropertyOneWay-hasChanged(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | T类型实例。 |

## set

```TypeScript
set(newValue: T): void
```

赋值时调用。

**起始版本：** 7

<!--Device-SyncedPropertyOneWay-set(newValue: T): void--><!--Device-SyncedPropertyOneWay-set(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | T类型实例。 |

## source_

```TypeScript
private source_
```

双向同步属性的数据源。

**起始版本：** 7

<!--Device-SyncedPropertyOneWay-private source_--><!--Device-SyncedPropertyOneWay-private source_-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## wrappedValue_

```TypeScript
private wrappedValue_
```

单向绑定时的值。

**起始版本：** 7

<!--Device-SyncedPropertyOneWay-private wrappedValue_--><!--Device-SyncedPropertyOneWay-private wrappedValue_-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

