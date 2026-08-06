# HashMapCbFn

```TypeScript
export type HashMapCbFn<K, V> = (value: V, key: K, map: HashMap<K, V>) => void
```

HashMap中forEach方法的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type HashMapCbFn<K, V> = (value: V, key: K, map: HashMap<K, V>) => void--><!--Device-unnamed-export type HashMapCbFn<K, V> = (value: V, key: K, map: HashMap<K, V>) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | V | 是 | 当前遍历到的元素键值对的值。  |
| key | K | 是 | 当前遍历到的元素键值对的键。  |
| map | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;K, V&gt; | 是 | 当前调用forEach方法的实例对象，默认值为当前实例对象。  |

