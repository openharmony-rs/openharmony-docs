# SubscribedAbstractProperty(System API)（系统接口）

SubscribedAbstractProperty是[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中属性的单/双向同步绑定对象，用于与AppStorage/LocalStorage中的属性建立数据同 步关系。SubscribedAbstractProperty实例需要通过[aboutToBeDeleted](#abouttobedeleted)接口手动释放，以取消同步 关系并无效化实例。 > **说明：** > > 从API version 12开始，AppStorage/LocalStorage支持Map、Set、Date类型，支持null、undefined以及联合类型。

**起始版本：** 7

<!--Device-unnamed-declare abstract class SubscribedAbstractProperty--><!--Device-unnamed-declare abstract class SubscribedAbstractProperty-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## aboutToBeDeleted

```TypeScript
abstract aboutToBeDeleted(): void
```

取消SubscribedAbstractProperty实例对 [AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)的单向或双向同步关系，并无效化SubscribedAbstractProperty实例。即调用 aboutToBeDeleted方法之后，不能再使用SubscribedAbstractProperty实例调用[set](arkts-arkui-localstorage-c.md#set)或[get](arkts-arkui-localstorage-c.md#get) 方法。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SubscribedAbstractProperty-abstract aboutToBeDeleted(): void--><!--Device-SubscribedAbstractProperty-abstract aboutToBeDeleted(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## get

```TypeScript
abstract get(): T
```

读取[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中所同步属性的数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SubscribedAbstractProperty-abstract get(): T--><!--Device-SubscribedAbstractProperty-abstract get(): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | AppStorage/LocalStorage同步属性的数据。 |

## info

```TypeScript
info(): string
```

返回[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中所同步属性的属性名。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SubscribedAbstractProperty-info(): string--><!--Device-SubscribedAbstractProperty-info(): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | AppStorage/LocalStorage中所同步属性的属性名。 |

## set

```TypeScript
abstract set(newValue: T): void
```

设置[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中所同步属性的数据，newValue必须是T类型，从API version 12开始可以为 null或undefined。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SubscribedAbstractProperty-abstract set(newValue: T): void--><!--Device-SubscribedAbstractProperty-abstract set(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | AppStorage/LocalStorage中所同步属性的新值，从API version 12开始可以为null或undefined。 |

