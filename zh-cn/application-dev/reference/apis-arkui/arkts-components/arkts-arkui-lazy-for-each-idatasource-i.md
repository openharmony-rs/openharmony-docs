# IDataSource

LazyForEach的数据源。

**起始版本：** 7

<!--Device-unnamed-declare interface IDataSource--><!--Device-unnamed-declare interface IDataSource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getData

```TypeScript
getData(index: number): any
```

获取索引值index对应的数据。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-IDataSource-getData(index: number): any--><!--Device-IDataSource-getData(index: number): any-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 获取数据对应的索引值。取值范围是[0, 数据源长度-1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| any | 获取索引值index对应的数据，由数据源决定具体类型。 |

## registerDataChangeListener

```TypeScript
registerDataChangeListener(listener: DataChangeListener): void
```

注册数据改变的监听器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-IDataSource-registerDataChangeListener(listener: DataChangeListener): void--><!--Device-IDataSource-registerDataChangeListener(listener: DataChangeListener): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listener | [DataChangeListener](arkts-arkui-lazy-for-each-datachangelistener-i.md) | 是 | 数据变化监听器。 |

## totalCount

```TypeScript
totalCount(): number
```

获得数据总数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-IDataSource-totalCount(): number--><!--Device-IDataSource-totalCount(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获得数据总数，由数据源决定实际大小。 |

## unregisterDataChangeListener

```TypeScript
unregisterDataChangeListener(listener: DataChangeListener): void
```

注销数据改变的监听器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-IDataSource-unregisterDataChangeListener(listener: DataChangeListener): void--><!--Device-IDataSource-unregisterDataChangeListener(listener: DataChangeListener): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| listener | [DataChangeListener](arkts-arkui-lazy-for-each-datachangelistener-i.md) | 是 | 数据变化监听器。 |

