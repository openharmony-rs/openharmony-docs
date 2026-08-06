# SubscribedAbstractProperty

SubscribedAbstractProperty是\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_/ \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中属性的单/双向同步绑定对象，用于与AppStorage/LocalStorage中的属性建立数据同 步关系。SubscribedAbstractProperty实例需要通过[aboutToBeDeleted]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口手动释放，以取消同步 关系并无效化实例。 > **说明：** > > 从API version 12开始，AppStorage/LocalStorage支持Map、Set、Date类型，支持null、undefined以及联合类型。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-unnamed-declare abstract class SubscribedAbstractProperty<T>--><!--Device-unnamed-declare abstract class SubscribedAbstractProperty<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToBeDeleted

```TypeScript
abstract aboutToBeDeleted(): void
```

取消[SubscribedAbstractProperty]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_实例对 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_/ \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_的单向或双向同步关系，并无效化SubscribedAbstractProperty实例。即调用 aboutToBeDeleted方法之后，不能再使用SubscribedAbstractProperty实例调用[set]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_或[get]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_ 方法。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SubscribedAbstractProperty-abstract aboutToBeDeleted(): void--><!--Device-SubscribedAbstractProperty-abstract aboutToBeDeleted(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(
    /**
     * 订阅者，用于接收属性变化通知；不传入则不建立订阅关系。
     *
     **** 
     */
    subscribeMe?: IPropertySubscriber,
    /**
     * 变量信息，用于标识该订阅关系；不传入时默认为undefined。
     *
     **** 
     */
    info?: string,
  )
```

构造函数。若传入了subscribeMe参数建立了订阅关系，订阅关系不再需要时，应调用[unlinkSuscriber()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_解除 订阅（订阅者ID通过[IPropertySubscriber]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_.[id()]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_获取）。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-SubscribedAbstractProperty-constructor(    /**     * 订阅者，用于接收属性变化通知；不传入则不建立订阅关系。     *     ****      */    subscribeMe?: IPropertySubscriber,    /**     * 变量信息，用于标识该订阅关系；不传入时默认为undefined。     *     ****      */    info?: string,  )--><!--Device-SubscribedAbstractProperty-constructor(    /**     * 订阅者，用于接收属性变化通知；不传入则不建立订阅关系。     *     ****      */    subscribeMe?: IPropertySubscriber,    /**     * 变量信息，用于标识该订阅关系；不传入时默认为undefined。     *     ****      */    info?: string,  )-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeMe | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 订阅者，用于接收属性变化通知；不传入则不建立订阅关系。 |
| info | string | 否 | 变量信息，用于标识该订阅关系；不传入时默认为undefined。 |

## createOneWaySync

```TypeScript
createOneWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyOneWay<T>
```

创建单向同步属性。数据变更仅从数据源向订阅者单向传播。订阅关系不再需要时，应调用[unlinkSuscriber()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_解除 订阅（订阅者ID通过[IPropertySubscriber]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_.[id()]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_获取）， 或由返回的[SyncedPropertyOneWay]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_对象 的[aboutToBeDeleted()]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_方法处理取消订阅。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-SubscribedAbstractProperty-createOneWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyOneWay<T>--><!--Device-SubscribedAbstractProperty-createOneWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyOneWay<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeMe | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 订阅者，用于接收属性变化通知；不传入则不建立订阅关系。 |
| info | string | 否 | 变量信息，用于标识该订阅关系；不传入时默认为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 返回创建的单向同步属性对象，用于接收父组件状态值的单向同步，当父组件状态变化时更新自身值。 |

## createTwoWaySync

```TypeScript
createTwoWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyTwoWay<T>
```

创建双向同步属性。数据变更在数据源与订阅者之间双向传播。与[createOneWaySync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_相比，该方法支持 数据源与订阅者之间的双向同步，适用于订阅者也需要反向修改数据源的场景；若仅需数据源向订阅者单向同步， 请使用[createOneWaySync]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。订阅关系不再需要时， 应调用[unlinkSuscriber()]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_解除订阅（订阅者ID 通过[IPropertySubscriber]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_.[id()]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_获取）， 或由返回的[SyncedPropertyTwoWay]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_对象 的[aboutToBeDeleted()]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_方法处理取消订阅。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-SubscribedAbstractProperty-createTwoWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyTwoWay<T>--><!--Device-SubscribedAbstractProperty-createTwoWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyTwoWay<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscribeMe | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 订阅者，用于接收属性变化通知；不传入则不建立订阅关系。 |
| info | string | 否 | 变量信息，用于标识该订阅关系；不传入时默认为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | Two-way synchronized property. |

## get

```TypeScript
abstract get(): T
```

读取\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_/ \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中所同步属性的数据。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SubscribedAbstractProperty-abstract get(): T--><!--Device-SubscribedAbstractProperty-abstract get(): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | AppStorage/LocalStorage同步属性的数据。 |

## id

```TypeScript
id(): number
```

获取ID时调用。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-SubscribedAbstractProperty-id(): number--><!--Device-SubscribedAbstractProperty-id(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回该订阅属性的唯一标识ID。 |

## info

```TypeScript
info(): string
```

返回\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_/ \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中所同步属性的属性名。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SubscribedAbstractProperty-info(): string--><!--Device-SubscribedAbstractProperty-info(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | AppStorage/LocalStorage中所同步属性的属性名。 |

## notifyHasChanged

```TypeScript
protected notifyHasChanged(newValue: T): void
```

通知变化时调用。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-SubscribedAbstractProperty-protected notifyHasChanged(newValue: T): void--><!--Device-SubscribedAbstractProperty-protected notifyHasChanged(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-SubscribedAbstractProperty-protected notifyPropertyRead(): void--><!--Device-SubscribedAbstractProperty-protected notifyPropertyRead(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## numberOfSubscrbers

```TypeScript
numberOfSubscrbers(): number
```

获取订阅者数量时调用。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-SubscribedAbstractProperty-numberOfSubscrbers(): number--><!--Device-SubscribedAbstractProperty-numberOfSubscrbers(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回订阅者数量。 |

## set

```TypeScript
abstract set(newValue: T): void
```

设置\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_/ \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_中所同步属性的数据，newValue必须是T类型，从API version 12开始可以为 null或undefined。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SubscribedAbstractProperty-abstract set(newValue: T): void--><!--Device-SubscribedAbstractProperty-abstract set(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | AppStorage/LocalStorage中所同步属性的新值，从API version 12开始可以为null或undefined。 |

## unlinkSuscriber

```TypeScript
unlinkSuscriber(subscriberId: number): void
```

根据订阅者ID解除订阅时调用。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-SubscribedAbstractProperty-unlinkSuscriber(subscriberId: number): void--><!--Device-SubscribedAbstractProperty-unlinkSuscriber(subscriberId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| subscriberId | number | 是 | 要解除订阅的订阅者ID，需为已通过[createTwoWaySync]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_或[createOneWaySync]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_建立订阅关系的订阅者ID，通过[IPropertySubscriber]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_.[id()]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法获取。 |

## id_

```TypeScript
private id_
```

订阅属性的唯一标识ID，用于在订阅关系管理中区分不同的订阅属性实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-SubscribedAbstractProperty-private id_--><!--Device-SubscribedAbstractProperty-private id_-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## info_

```TypeScript
private info_?
```

变量信息，用于标识该订阅关系。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-SubscribedAbstractProperty-private info_?--><!--Device-SubscribedAbstractProperty-private info_?-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subscribers_

```TypeScript
protected subscribers_: Set<number>
```

订阅者集合。

**类型：** Set&lt;number&gt;

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

<!--Device-SubscribedAbstractProperty-protected subscribers_: Set<number>--><!--Device-SubscribedAbstractProperty-protected subscribers_: Set<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

