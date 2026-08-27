# AbstractProperty

AbstractProperty是AppStorage/LocalStorage中属性的引用，提供读取、修改所引用属性数据及查询属性名的能力。与SubscribedAbstractProperty不同，AbstractProperty 实例无需手动释放。

> **说明：**
> 
> 从API version 12开始，AppStorage/LocalStorage支持Map、Set、Date类型，支持null、undefined以及联合类型。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## get

```TypeScript
get(): T
```

读取[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中所引用属性的数据。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | AppStorage/LocalStorage中所引用属性的数据。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let ref1: AbstractProperty<number> | undefined = AppStorage.ref('PropA');
ref1?.get(); // ref1.get()=47
```

## info

```TypeScript
info(): string
```

读取[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中所引用属性的属性名。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | AppStorage/LocalStorage中所引用属性的属性名。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let ref1: AbstractProperty<number> | undefined = AppStorage.ref('PropA');
ref1?.info(); // ref1.info()='PropA'
```

```TypeScript
AppStorage.setOrCreate('PropA', 47); 
let prop1: SubscribedAbstractProperty<number> = AppStorage.prop('PropA');
prop1.info(); // prop1.info() = 'PropA'
```

## set

```TypeScript
set(newValue: T): void
```

更新[AppStorage](../../../ui/state-management/arkts-appstorage.md)/ [LocalStorage](../../../ui/state-management/arkts-localstorage.md)中所引用属性的数据，newValue必须是T类型，可以为null或undefined。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | AppStorage/LocalStorage中所引用属性的新值，可以为null或undefined。 |

**示例**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let ref1: AbstractProperty<number> | undefined = AppStorage.ref('PropA');
ref1?.set(1); // ref1.get()=1
let mapValue: Map<string, number> = new Map([['1', 0]]);
let ref2 = AppStorage.setAndRef('MapA', mapValue);
ref2.set(mapValue);
let setValue: Set<string> = new Set(['1']);
let ref3 = AppStorage.setAndRef('SetB', setValue);
ref3.set(setValue);
let dateValue: Date = new Date('2024');
let ref4 = AppStorage.setAndRef('DateC', dateValue);
ref4.set(dateValue);
ref2.set(null);
ref3.set(undefined);
```
