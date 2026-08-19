# format

## 导入模块

```TypeScript
```

## format

```TypeScript
function format(format: string, ...args: Object[]): string
```

%s: 用于转换除BigInt、Object和-0之外的所有值。BigInt值将以n表示，没有用户定义toString函数的对象使用util.inspect()检查， 选项为{ depth: 0, colors: false, compact: 3 }。 %d: 用于转换除BigInt和Symbol之外的所有值。 %i: 对除BigInt和Symbol之外的所有值使用parseInt(value, 10)。 %f: 对除BigInt和Symbol之外的所有值使用parseFloat(value)。 %j: JSON。如果参数包含循环引用，则替换为字符串'[Circular]'。 %o: Object。对象的通用JavaScript对象格式字符串表示。类似于 util.inspect()，选项为{ showHidden: true, showProxy: true}。这将显示完整对象，包括 不可枚举属性和代理。 %O: Object。对象的通用JavaScript对象格式字符串表示。 %O: Object。对象的通用JavaScript对象格式字符串表示。类似于 util.inspect()，没有选项。这将显示完整对象，不包括不可枚举属性和 代理。 %c: CSS。此说明符被忽略，将跳过传入的任何CSS。 %%: 单个百分号('%')。这不会消耗参数。返回：&lt;string&gt; 格式化的字符串。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-util-function format(format: string, ...args: Object[]): string--><!--Device-util-function format(format: string, ...args: Object[]): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| format | string | 是 | 格式字符串 |
| args | Object[] | 是 | 要格式化的数据 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 按特定格式格式化的字符串。 |

