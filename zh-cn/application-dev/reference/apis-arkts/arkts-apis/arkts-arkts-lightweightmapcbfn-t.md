# LightWeightMapCbFn

```TypeScript
export type LightWeightMapCbFn<K, V> = (value: V, key: K, map: LightWeightMap<K, V>) => void
```

LightWeightMap中forEach方法的回调函数。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type LightWeightMapCbFn<K, V> = (value: V, key: K, map: LightWeightMap<K, V>) => void--><!--Device-unnamed-export type LightWeightMapCbFn<K, V> = (value: V, key: K, map: LightWeightMap<K, V>) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | V | 是 | 当前遍历到的元素键值对的值。 |
| key | K | 是 | 当前遍历到的元素键值对的键。 |
| map | [LightWeightMap](arkts-arkts-util-lightweightmap-lightweightmap-c.md)&lt;K, V&gt; | 是 | 当前正在遍历的LightWeightMap实例。 |

