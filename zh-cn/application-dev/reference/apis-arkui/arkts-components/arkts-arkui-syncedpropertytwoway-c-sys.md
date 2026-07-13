# SyncedPropertyTwoWay（系统接口）

继承自[SubscribedAbstractProperty<T>](arkts-arkui-subscribedabstractproperty-c.md)。用来定义变量状态的值。

**继承/实现关系：** SyncedPropertyTwoWay extends [SubscribedAbstractProperty<T>](SubscribedAbstractProperty<T>) implements [ISinglePropertyChangeSubscriber<T>](ISinglePropertyChangeSubscriber<T>)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## aboutToBeDeleted

```TypeScript
aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void
```

销毁时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unsubscribeMe | IPropertySubscriber | 否 | 被取消的订阅者。 |

## constructor

```TypeScript
constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)
```

构造函数。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | SubscribedAbstractProperty&lt;T&gt; | 是 | 双向同步属性的数据源。 |
| subscribeMe | IPropertySubscriber | 否 | 订阅者。 |
| info | string | 否 | 订阅者信息。 |

## get

```TypeScript
get(): T
```

获取数据时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | T类型实例。 |

## hasChanged

```TypeScript
hasChanged(newValue: T): void
```

变化时调用。

**起始版本：** 7

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

