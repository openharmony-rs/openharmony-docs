# ArrayListReplaceCb

```TypeScript
export type ArrayListReplaceCb<T> =  (value: T, index: int, arrlist: ArrayList<T>) => T
```

ArrayList中replaceAllElements方法的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type ArrayListReplaceCb<T> =  (value: T, index: int, arrlist: ArrayList<T>) => T--><!--Device-unnamed-export type ArrayListReplaceCb<T> =  (value: T, index: int, arrlist: ArrayList<T>) => T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 当前遍历到的元素。  |
| index | int | 是 | 当前遍历到的下标值。  |
| arrlist | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 当前调用replaceAllElements方法的实例对象。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 此回调返回替换后的元素。 |

