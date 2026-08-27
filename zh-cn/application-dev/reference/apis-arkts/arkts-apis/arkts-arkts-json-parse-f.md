# parse

## 导入模块

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## parse

```TypeScript
function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null
```

解析JSON字符串生成ArkTS对象或null。解析过程中，每个键值对按从最内层到最外层的顺序依次经过reviver函数处理，返回值替换原始值； 当传入ParseOptions指定BigIntMode时，符合条件的整数将被解析为BigInt；当入参字符串为'null'时返回null。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 有效的JSON字符串，需符合JSON语法规范。 |
| reviver | Transformer | 否 | 转换函数，用于修改解析生成的原始值；当需要对解析结果进行自定义转换时使用。默认值是undefined。 |
| options | ParseOptions | 否 | 解析的配置选项，用于控制解析生成的类型。默认值是undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object \| null | 当传入的字符串为'null'时，返回null。 |

**示例**

```TypeScript
import { JSON } from '@kit.ArkTS';

function reviverFunc(key: string, value: Object): Object | undefined | null {
  if (key === "age" && typeof value === 'number') {
    return value + 1;
  }
  return value;
}

const jsonText = '{"name": "John", "age": 30, "city": "ChongQing"}';
let parsedObj = JSON.parse(jsonText);
console.info((parsedObj as object)?.["name"]);
// 打印结果：John

const jsonTextStr = '{"name": "John", "age": 30}';
let objRst = JSON.parse(jsonTextStr, reviverFunc);
console.info((objRst as object)?.["age"]);
// 打印结果：31

const numberText = '{"number": 10, "largeNumber": 112233445566778899}';
let options: JSON.ParseOptions = { bigIntMode: JSON.BigIntMode.PARSE_AS_BIGINT };
let numberObj = JSON.parse(numberText, null, options) as Object;

console.info(typeof (numberObj as object)?.["number"]);
// 打印结果：number
console.info((numberObj as object)?.["number"]);
// 打印结果：10

console.info(typeof (numberObj as object)?.["largeNumber"]);
// 打印结果：bigint
console.info((numberObj as object)?.["largeNumber"]);
// 打印结果：112233445566778899
```
