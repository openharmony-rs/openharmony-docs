# HashSetCbFn

```TypeScript
export type HashSetCbFn<T> = (value: T, key: T, set: HashSet<T>) => void
```

HashSet中forEach方法的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type HashSetCbFn<T> = (value: T, key: T, set: HashSet<T>) => void--><!--Device-unnamed-export type HashSetCbFn<T> = (value: T, key: T, set: HashSet<T>) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 当前遍历到的元素键值对的值。  |
| key | T | 是 | 当前遍历到的元素键值对的键（和value相同）。  |
| set | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 当前调用forEach方法的实例对象，默认值为当前实例对象。  |

