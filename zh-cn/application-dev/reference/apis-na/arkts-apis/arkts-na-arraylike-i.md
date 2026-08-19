# ArrayLike

表示具有length属性且可通过索引访问的对象。

**继承/实现关系：** ArrayLike extends Iterable<T>

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export interface ArrayLike--><!--Device-unnamed-export interface ArrayLike-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
```

## $_get

```TypeScript
$_get(index: int): T
```

获取指定索引处的元素。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArrayLike-$_get(index: int): T--><!--Device-ArrayLike-$_get(index: int): T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 待获取元素的索引，从0开始计数。 <br>取值约束：应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 指定索引处的元素。 |

