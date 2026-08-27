# printf

## 导入模块

```TypeScript
```

## printf

```TypeScript
function printf(format: string, ...args: Object[]): string
```

通过式样化字符串对输入的内容按特定格式输出。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [format](arkts-arkts-util-format-f.md)

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| format | string | 是 | 式样化字符串。 |
| args | Object[] | 是 | 替换式样化字符串通配符的数据，此参数缺失时，默认返回第一个参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 按特定格式式样化后的字符串，包含根据格式说明符处理后的参数值。 |

**示例**

```TypeScript
let res = util.printf("%s", "hello world!");
console.info(res);
// 输出结果：hello world!
```
