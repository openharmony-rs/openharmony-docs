# parseSendable

## 导入模块

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## parseSendable

```TypeScript
function parseSendable(text: string, reviver?: SendableTransformer, options?: ParseOptions): ISendable | null
```

解析JSON字符串，生成可直接跨并发实例（Worker或TaskPool）传递、无需拷贝的Sendable对象。当解析后的JSON数据需要跨线程共享时，使用本接口替代[parse](arkts-arkts-json-parse-f.md)：解析结果直接创建于共享堆，调用返回后即可被各并发实例访问。

使用说明：<ul> <li>取值范围在"0"到"4294967294"之间且不含前导零、符号、小数或指数形式的数字字符串键会作为元素下标存储；"4294967295"及其他形式作为普通属性名。</li> <li>重复键以后值为准，且枚举位置保持在首次出现的位置。</li> <li>当options.parseReturnType为[MAP](arkts-arkts-json-parsereturntype-e.md#map)时，返回键始终为字符串、支持任意条数增删的collections.Map；为[OBJECT](arkts-arkts-json-parsereturntype-e.md#object)（默认）时，返回不可扩展的Sendable对象，其已有属性可更新、不可新增或删除。</li> </ul>

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-json-function parseSendable(text: string, reviver?: SendableTransformer, options?: ParseOptions): ISendable | null--><!--Device-json-function parseSendable(text: string, reviver?: SendableTransformer, options?: ParseOptions): ISendable | null-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 有效的JSON字符串，需符合JSON语法规范。 |
| reviver | [SendableTransformer](arkts-arkts-json-sendabletransformer-t.md) | 否 | 用于转换结果的函数。当前仅接受undefined；传入函数将抛出TypeError（与ASON.parse一致）。默认值是undefined。 |
| options | [ParseOptions](arkts-arkts-json-parseoptions-i.md) | 否 | 解析的配置选项。也可传入仅含bigIntMode的既有ParseOptions对象（此时parseReturnType默认为OBJECT）。默认值是undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ISendable](arkts-arkts-json-isendable-t.md) &#124; null | 返回与JSON字符串对应的Sendable对象；当JSON字符串为'null'时返回null；当options.parseReturnType为[MAP](arkts-arkts-json-parsereturntype-e.md#map)时返回collections.Map。 |

**示例**

```TypeScript
import { JSON, collections, lang } from '@kit.ArkTS';

// 基础用法：解析为Sendable对象，可直接跨Worker/TaskPool传递
let sendableObj: lang.ISendable | null = JSON.parseSendable('{"name": "John", "age": 30}');
console.info(`result: ${(sendableObj as object)?.["name"]}`); // 打印结果：result: John

// 86个数字键：任意数量数字键全部可访问
let parts86: string[] = [];
for (let i = 0; i < 86; i++) {
  parts86.push('"' + i + '": ' + i * 2);
}
let numericObj86: lang.ISendable | null = JSON.parseSendable('{' + parts86.join(',') + '}');
console.info(`result: ${(numericObj86 as object)?.[84]}`); // 打印结果：result: 168
console.info(`result: ${(numericObj86 as object)?.[85]}`); // 打印结果：result: 170

// 1021个数字键：属性数量超过1020时仍全部可访问
let parts1021: string[] = [];
for (let i = 0; i < 1021; i++) {
  parts1021.push('"' + i + '": ' + i);
}
let numericObj1021: lang.ISendable | null = JSON.parseSendable('{' + parts1021.join(',') + '}');
console.info(`result: ${(numericObj1021 as object)?.[0]}`); // 打印结果：result: 0
console.info(`result: ${(numericObj1021 as object)?.[1020]}`); // 打印结果：result: 1020

// MAP返回类型：任意条数可增删，键为字符串
let mapOptions: JSON.ParseOptions = {
  bigIntMode: JSON.BigIntMode.PARSE_AS_BIGINT,
  parseReturnType: JSON.ParseReturnType.MAP
};
let sendableMap: lang.ISendable | null = JSON.parseSendable('{"a": 1, "b": 2}', undefined, mapOptions);
console.info(`result: ${(sendableMap as collections.Map<string, number>).get("a")}`); // 打印结果：result: 1

// 也可传入仅含bigIntMode的ParseOptions对象（parseReturnType默认为OBJECT）
let bigOptions: JSON.ParseOptions = {
  bigIntMode: JSON.BigIntMode.PARSE_AS_BIGINT
};
let bigObj: lang.ISendable | null = JSON.parseSendable('{"largeNumber":112233445566778899}', undefined, bigOptions);
console.info(`result: ${(bigObj as object)?.["largeNumber"]}`); // 打印结果：result: 112233445566778899

// reviver当前仅接受undefined
try {
  JSON.parseSendable('{"a": 1}', (key: string, value: lang.ISendable): lang.ISendable | undefined => {
    return value;
  });
} catch (e) {
  console.error(`error: ${(e as Error).message}`);
  // 打印结果：error: Parameter error. Reviver only supports undefined currently.
}
```
