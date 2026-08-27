# PersistentStorage

PersistentStorage提供了UI状态的持久化存储能力，将选定的AppStorage属性持久化到文件中，在应用重启时从文件中恢复这些属性值并写入到AppStorage。具体UI使用说明，详见 [PersistentStorage：持久化存储UI状态](../../../ui/state-management/arkts-persiststorage.md)。

> **说明：**
> 
> 从API version 12开始，PersistentStorage支持null、undefined。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## DeleteProp

```TypeScript
static DeleteProp(key: string): void
```

是[PersistProp](#persistprop)的逆向操作。将key对应的属性从 [PersistentStorage](../../../ui/state-management/arkts-persiststorage.md)中删除，后续 [AppStorage](../../../ui/state-management/arkts-appstorage.md)的操作对PersistentStorage不会再有影响。如需再次持久化，可再次调用 [PersistProp](#persistprop)接口。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [deleteProp](#deleteprop)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | PersistentStorage中的属性名。 |

**示例**

```TypeScript
PersistentStorage.DeleteProp('highScore');
```

## deleteProp

```TypeScript
static deleteProp(key: string): void
```

是[persistProp](#persistprop)的逆向操作。将key对应的属性从 [PersistentStorage](../../../ui/state-management/arkts-persiststorage.md)中删除，后续 [AppStorage](../../../ui/state-management/arkts-appstorage.md)的操作对PersistentStorage不会再有影响。如需再次持久化，可再次调用 [persistProp](#persistprop)接口。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | PersistentStorage中的属性名。 |

**示例**

```TypeScript
PersistentStorage.deleteProp('highScore');
```

## Keys

```TypeScript
static Keys(): Array<string>
```

返回所有持久化属性的属性名的数组。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [keys](#keys)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;string & gt; | 返回所有持久化属性的属性名的数组。 |

**示例**

```TypeScript
let keys: Array<string> = PersistentStorage.Keys();
```

```TypeScript
Environment.EnvProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);

let keys: Array<string> = Environment.Keys(); // keys 包含 accessibilityEnabled、languageCode、prop
```

## keys

```TypeScript
static keys(): Array<string>
```

返回所有持久化属性的属性名的数组。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;string & gt; | 返回所有持久化属性的属性名的数组。 |

**示例**

```TypeScript
let keys: Array<string> = PersistentStorage.keys();
```

```TypeScript
Environment.envProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);

let keys: Array<string> = Environment.keys(); // keys 包含 accessibilityEnabled、languageCode、prop
```

## PersistProp

```TypeScript
static PersistProp<T>(key: string, defaultValue: T): void
```

将[AppStorage](../../../ui/state-management/arkts-appstorage.md)中key对应的属性持久化到文件中。该接口应在访问AppStorage之前调用。确定属性的类型和值的顺序如下：
1. 如果[PersistentStorage](../../../ui/state-management/arkts-persiststorage.md)文件中存在key对应的属性，在AppStorage中创建对应的key，并用在PersistentStorage中找到的key的属性初始化。
2. 如果PersistentStorage文件中没有查询到key对应的属性，则在AppStorage中查找key对应的属性。如果找到key对应的属性，则将该属性持久化。
3. 如果AppStorage也没查找到key对应的属性，则在AppStorage中创建key对应的属性。用defaultValue初始化其值，并将该属性持久化。
根据上述的初始化流程，如果AppStorage中有该属性，则会使用其值覆盖PersistentStorage文件中的值。由于AppStorage是内存中的数据，这种操作会使持久化文件中的数据被内存数据覆盖，导致持久化数据失去意义。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [persistProp](#persistprop)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要持久化的属性名。 |
| defaultValue | T | 是 | 在PersistentStorage和AppStorage中未查询到时，则使用默认值进行初始化。默认值不允许为null或undefined。 |

**示例**

```TypeScript
PersistentStorage.PersistProp('highScore', '0');
```

## persistProp

```TypeScript
static persistProp<T>(key: string, defaultValue: T): void
```

将[AppStorage](../../../ui/state-management/arkts-appstorage.md)中key对应的属性持久化到文件中。该接口通常在访问AppStorage之前调用。确定属性的类型和值的顺序如下：
1. 如果[PersistentStorage](../../../ui/state-management/arkts-persiststorage.md)文件中存在key对应的属性，在AppStorage中创建对应的key，并用在PersistentStorage中找到的key的属性初始化。
2. 如果PersistentStorage文件中没有查询到key对应的属性，则在AppStorage中查找key对应的属性。如果找到key对应的属性，则将该属性持久化。
3. 如果AppStorage中也没查找到key对应的属性，则在AppStorage中创建key对应的属性。用defaultValue初始化其值，并将该属性持久化。
根据上述的初始化流程，如果AppStorage中有该属性，则会使用其值覆盖PersistentStorage文件中的值。由于AppStorage是内存中的数据，这种操作会使持久化文件中的数据被内存数据覆盖，导致持久化数据失去意义。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要持久化的属性名。 |
| defaultValue | T | 是 | 在PersistentStorage和AppStorage中未查询到时，则使用默认值进行初始化。从API version 12开始可以为null或undefined。 |

**示例**

persistProp具体用法详见[从AppStorage中访问PersistentStorage初始化的属性](../../../ui/state-management/arkts-persiststorage.md#从appstorage中访问persistentstorage初始化的属性)。

## PersistProps

```TypeScript
static PersistProps(
    properties: {
      key: string;
      defaultValue: any;
    }[],
  ): void
```

行为与[PersistProp](#persistprop)类似，不同在于可以一次性持久化多个数据。该接口应在访问AppStorage之前调用，适合在应用启动时初始化。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [PersistProps](#persistprops)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| properties | {       key: string;       defaultValue: any;     }[] | 是 |  |

**示例**

```TypeScript
PersistentStorage.PersistProps([{ key: 'highScore', defaultValue: '0' }, { key: 'weightScore', defaultValue: '1' }]);
```

## persistProps

```TypeScript
static persistProps(props: PersistPropsOptions[]): void
```

行为与[persistProp](#persistprop)类似，不同在于可以一次性持久化多个数据。该接口通常在访问AppStorage之前调用，适合在应用启动时初始化。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| props | [PersistPropsOptions](arkts-arkui-persistpropsoptions-i.md)[] | 是 | 持久化数组，每项包含属性名和默认值。 |

**示例**

```TypeScript
PersistentStorage.persistProps([{ key: 'highScore', defaultValue: '0' }, { key: 'weightScore', defaultValue: '1' }]);
```
