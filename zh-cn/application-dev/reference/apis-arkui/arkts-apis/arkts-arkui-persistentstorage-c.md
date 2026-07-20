# PersistentStorage

PersistentStorage具体UI使用说明，详见[PersistentStorage(持久化存储UI状态)](docroot://ui/state-management/arkts-persiststorage.md)

> **说明：**

> 从API version 12开始，PersistentStorage支持null、undefined。

**起始版本：** 7

<!--Device-unnamed-declare class PersistentStorage--><!--Device-unnamed-declare class PersistentStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="deleteprop"></a>
## DeleteProp

```TypeScript
static DeleteProp(key: string): void
```

[PersistProp](arkts-arkui-persistentstorage-c.md#persistprop-1)的逆向操作。将key对应的属性从[PersistentStorage](docroot://ui/state-management/arkts-persiststorage.md)中删除，后续[AppStorage](docroot://ui/state-management/arkts-appstorage.md)的操作，对PersistentStorage不会再有影响。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [deleteProp](arkts-arkui-persistentstorage-c.md#deleteprop-1)

<!--Device-PersistentStorage-static DeleteProp(key: string): void--><!--Device-PersistentStorage-static DeleteProp(key: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | PersistentStorage中的属性名。 |

<a id="keys"></a>
## Keys

```TypeScript
static Keys(): Array<string>
```

返回所有持久化属性的属性名的数组。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [keys](arkts-arkui-persistentstorage-c.md#keys-1)

<!--Device-PersistentStorage-static Keys(): Array<string>--><!--Device-PersistentStorage-static Keys(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回所有持久化属性的属性名的数组。 |

<a id="persistprop"></a>
## PersistProp

```TypeScript
static PersistProp<T>(key: string, defaultValue: T): void
```

将[AppStorage](docroot://ui/state-management/arkts-appstorage.md)中key对应的属性持久化到文件中。该接口的调用通常在访问AppStorage之前。

确定属性的类型和值的顺序如下：

1. 如果[PersistentStorage](docroot://ui/state-management/arkts-persiststorage.md)文件中存在key对应的属性，在AppStorage中创建对应的propName，并用在PersistentStorage中找到的key的属性初始化。

2. 如果PersistentStorage文件中没有查询到key对应的属性，则在AppStorage中查找key对应的属性。如果找到key对应的属性，则将该属性持久化。

3. 如果AppStorage也没查找到key对应的属性，则在AppStorage中创建key对应的属性。用defaultValue初始化其值，并将该属性持久化。

根据上述的初始化流程，如果AppStorage中有该属性，则会使用其值，覆盖掉PersistentStorage文件中的值。由于AppStorage是内存内数据，该行为会导致数据丧失持久化能力。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [persistProp](arkts-arkui-persistentstorage-c.md#persistprop-1)

<!--Device-PersistentStorage-static PersistProp<T>(key: string, defaultValue: T): void--><!--Device-PersistentStorage-static PersistProp<T>(key: string, defaultValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 属性名。 |
| defaultValue | T | 是 | 在PersistentStorage和AppStorage中未查询到时，则使用默认值进行初始化。不允许为null或undefined。 |

<a id="persistprops"></a>
## PersistProps

```TypeScript
static PersistProps(
    properties: {
      key: string;
      defaultValue: any;
    }[],
  ): void
```

行为和[PersistProp](arkts-arkui-persistentstorage-c.md#persistprop-1)类似，不同在于可以一次性持久化多个数据，适合在应用启动的时候初始化。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [PersistProps](arkts-arkui-persistentstorage-c.md#persistprops-1)

<!--Device-PersistentStorage-static PersistProps(
    properties: {
      key: string;
      defaultValue: any;
    }[],
  ): void--><!--Device-PersistentStorage-static PersistProps(
    properties: {
      key: string;
      defaultValue: any;
    }[],
  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| properties | {       key: string;       defaultValue: any;     }[] | 是 |  |

<a id="deleteprop"></a>
## deleteProp

```TypeScript
static deleteProp(key: string): void
```

[persistProp](arkts-arkui-persistentstorage-c.md#persistprop-1)的逆向操作。将key对应的属性从PersistentStorage中删除，后续[AppStorage](docroot://ui/state-management/arkts-appstorage.md)的操作，对[PersistentStorage](docroot://ui/state-management/arkts-persiststorage.md)不会再有影响。该操作会将对应的key从持久化文件中删除，如果希望再次持久化，可以再次调用[persistProp](arkts-arkui-persistentstorage-c.md#persistprop-1)接口。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PersistentStorage-static deleteProp(key: string): void--><!--Device-PersistentStorage-static deleteProp(key: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | PersistentStorage中的属性名。 |

<a id="keys"></a>
## keys

```TypeScript
static keys(): Array<string>
```

返回所有持久化属性的属性名的数组。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PersistentStorage-static keys(): Array<string>--><!--Device-PersistentStorage-static keys(): Array<string>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回所有持久化属性的属性名的数组。 |

<a id="persistprop"></a>
## persistProp

```TypeScript
static persistProp<T>(key: string, defaultValue: T): void
```

将[AppStorage](docroot://ui/state-management/arkts-appstorage.md)中key对应的属性持久化到文件中。该接口的调用通常在访问AppStorage之前。

确定属性的类型和值的顺序如下：

1. 如果[PersistentStorage](docroot://ui/state-management/arkts-persiststorage.md)文件中存在key对应的属性，在AppStorage中创建对应的propName，并用在PersistentStorage中找到的key的属性初始化。

2. 如果PersistentStorage文件中没有查询到key对应的属性，则在AppStorage中查找key对应的属性。如果找到key对应的属性，则将该属性持久化。

3. 如果AppStorage中也没查找到key对应的属性，则在AppStorage中创建key对应的属性。用defaultValue初始化其值，并将该属性持久化。

根据上述的初始化流程，如果AppStorage中有该属性，则会使用其值，覆盖掉PersistentStorage文件中的值。由于AppStorage是内存内数据，该行为会导致数据丧失持久化能力。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PersistentStorage-static persistProp<T>(key: string, defaultValue: T): void--><!--Device-PersistentStorage-static persistProp<T>(key: string, defaultValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 属性名。 |
| defaultValue | T | 是 | 在PersistentStorage和AppStorage中未查询到时，则使用默认值进行初始化。从API version 12开始允许为null或undefined。 |

<a id="persistprops"></a>
## persistProps

```TypeScript
static persistProps(props: PersistPropsOptions[]): void
```

行为和[persistProp](arkts-arkui-persistentstorage-c.md#persistprop-1)类似，不同在于可以一次性持久化多个数据，适合在应用启动的时候初始化。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PersistentStorage-static persistProps(props: PersistPropsOptions[]): void--><!--Device-PersistentStorage-static persistProps(props: PersistPropsOptions[]): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| props | [PersistPropsOptions](arkts-arkui-persistpropsoptions-i.md)[] | 是 | 持久化数组。 |

