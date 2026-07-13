# SubscribedAbstractProperty（系统接口）

SubscribedAbstractProperty是[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/
[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)中同步的属性。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor(
    /**
     * Subscriber IPropertySubscriber.
     *
     **** 
     */
    subscribeMe?: IPropertySubscriber,
    /**
     * Subscriber info.
     *
     **** 
     */
    info?: string,
  )
```

Constructor.

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeMe | IPropertySubscriber | 否 | Variable properties. |
| info | string | 否 | Variable information. |

## createOneWaySync

```TypeScript
createOneWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyOneWay<T>
```

创建单向同步时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeMe | IPropertySubscriber | 否 | 变量属性。 |
| info | string | 否 | 变量信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SyncedPropertyOneWay&lt;T&gt; | 返回单向同步属性。 |

## createTwoWaySync

```TypeScript
createTwoWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyTwoWay<T>
```

创建双向同步时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeMe | IPropertySubscriber | 否 | 变量属性。 |
| info | string | 否 | 变量信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SyncedPropertyTwoWay&lt;T&gt; | 返回双向同步属性。 |

## id

```TypeScript
id(): number
```

当输入用户ID时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | @syscap SystemCapability.ArkUI.ArkUI.Full@systemapi@FaAndStageModel |

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

变量解除订阅时调用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriberId | number | 是 | 变量id。 |

## id_

```TypeScript
private id_
```

私有成员变量id_。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## info_

```TypeScript
private info_?
```

变量信息。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## subscribers_

```TypeScript
protected subscribers_: Set<number>
```

订阅者集合。

**类型：** Set<number>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

