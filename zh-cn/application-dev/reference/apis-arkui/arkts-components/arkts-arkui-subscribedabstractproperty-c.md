# SubscribedAbstractProperty（系统接口）

SubscribedAbstractProperty是[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/
[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)中同步的属性。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## aboutToBeDeleted

```TypeScript
abstract aboutToBeDeleted(): void
```

取消[SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)实例对
[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/
[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)的单/双向同步关系，并无效化SubscribedAbstractProperty实例，即当调用
aboutToBeDeleted方法之后不能再使用SubscribedAbstractProperty实例调用[set](arkts-arkui-localstorage-c.md#set-1)或[get](arkts-arkui-localstorage-c.md#get-1)方
法。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## get

```TypeScript
abstract get(): T
```

读取从[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/
[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)同步属性的数据。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | AppStorage/LocalStorage同步属性的数据。 |

## info

```TypeScript
info(): string
```

返回属性名称。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 属性名称。 |

## set

```TypeScript
abstract set(newValue: T): void
```

设置[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/
[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)同步属性的数据，newValue必须是T类型，从API version 12开始可以为null或
undefined。

> **说明：**

> 从API version 12开始，AppStorage/LocalStorage支持Map、Set、Date类型，支持null、undefined以及联合类型。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | 要设置的数据，从API version 12开始可以为null或undefined。 |

