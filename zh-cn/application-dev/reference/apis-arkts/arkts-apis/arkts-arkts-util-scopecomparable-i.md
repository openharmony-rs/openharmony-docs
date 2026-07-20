# ScopeComparable

**ScopeComparable** 类型的值用于实现 **compareTo** 方法。因此，请确保输入参数是可比较的。

**起始版本：** 7

<!--Device-util-interface ScopeComparable--><!--Device-util-interface ScopeComparable-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

<a id="compareto"></a>
## compareTo

```TypeScript
compareTo(other: ScopeComparable): boolean
```

比较两个值并返回布尔值。

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScopeComparable-compareTo(other: ScopeComparable): boolean--><!--Device-ScopeComparable-compareTo(other: ScopeComparable): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | [ScopeComparable](arkts-arkts-util-scopecomparable-i.md) | 是 | 与当前值进行比较的另一个值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果当前值大于等于输入值，则返回 **true**；否则返回 **false**。 |

**示例：**

构造新类，实现compareTo方法。后续示例代码中，均以此Temperature类为例。

```TypeScript
class Temperature implements util.ScopeComparable {
  private readonly _temp: number;

  constructor(value: number) {
    this._temp = value;
  }

  compareTo(value: Temperature) {
    return this._temp >= value.getTemp();
  }

  getTemp() {
    return this._temp;
  }

  toString(): string {
    return this._temp.toString();
  }
}

```

