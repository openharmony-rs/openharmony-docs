# AbstractProperty

AbstractProperty是[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/
[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)中属性的引用。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## get

```TypeScript
get(): T
```

读取[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/
[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)中所引用属性的数据。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | AppStorage/LocalStorage中所引用属性的数据。 |

## info

```TypeScript
info(): string
```

读取[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/
[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)中所引用属性的属性名。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | AppStorage/LocalStorage中所引用属性的属性名。 |

## set

```TypeScript
set(newValue: T): void
```

更新[AppStorage](../../../../ui/state-management/arkts-appstorage.md)/
[LocalStorage](../../../../ui/state-management/arkts-localstorage.md)中所引用属性的数据，newValue必须是T类型，可以为null或undefined。

> **说明：**

> 从API version 12开始，AppStorage/LocalStorage支持Map、Set、Date类型，支持null、undefined以及联合类型。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | 要更新的数据，可以为null或undefined。 |

