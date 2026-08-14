# format

## format

```TypeScript
function format(format: string, ...args: Object[]): string
```

使用样式化字符串将输入内容按特定格式输出，适用于日志输出、用户界面文本格式化等场景。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-util-function format(format: string, ...args: Object[]): string--><!--Device-util-function format(format: string, ...args: Object[]): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| format | string | 是 | 格式化字符串，可以包含零个或多个占位符，用于指定要插入的参数的位置和格式。 |
| args | Object[] | 是 | 替换format参数中占位符的数据，此参数缺失时，直接返回格式化字符串本身。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的字符串。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { util } from '@kit.ArkTS';

interface utilAddressType {
  city: string;
  country: string;
}
interface utilPersonType {
  name: string;
  age: number;
  address: utilAddressType;
}

let name = 'John';
let age = 20;
let formattedString = util.format('My name is %s and I am %s years old', name, age);
console.info(formattedString);
// 输出结果：My name is John and I am 20 years old
let num = 10.5;
formattedString = util.format('The number is %d', num);
console.info(formattedString);
// 输出结果：The number is 10.5
num = 100.5;
formattedString = util.format('The number is %i', num);
console.info(formattedString);
// 输出结果：The number is 100
const pi = 3.141592653;
formattedString = util.format('The value of pi is %f', pi);
console.info(formattedString);
// 输出结果：The value of pi is 3.141592653
const obj: Record<string,number | string> = { "name": 'John', "age": 20 };
formattedString = util.format('The object is %j', obj);
console.info(formattedString);
// 输出结果：The object is {"name":"John","age":20}
const person: utilPersonType = {
  name: 'John',
  age: 20,
  address: {
    city: 'New York',
    country: 'USA'
  }
};
console.info(util.format('Formatted object using %%O: %O', person));
console.info(util.format('Formatted object using %%o: %o', person));
/*
输出结果：
Formatted object using %O: { name: 'John',
  age: 20,
  address:
  { city: 'New York',
    country: 'USA' } }
Formatted object using %o: { name: 'John',
  age: 20,
  address:
  { city: 'New York',
    country: 'USA' } }
 */
const percentage = 80;
let arg = 'homework';
formattedString = util.format('John finished %d%% of the %s', percentage, arg);
console.info(formattedString);
// 输出结果：John finished 80% of the homework
```

ArkTS-Sta示例：

```TypeScript
import { util } from '@kit.ArkTS';

interface utilAddresstype {
  city: string;
  country: string;
}
interface utilPersontype {
  name: string;
  age: int;
  address: utilAddresstype;
}

let name = 'John';
let age = 20;
let formattedString = util.format('My name is %s and I am %s years old', name, age);
console.info(formattedString);
// 输出结果：My name is John and I am 20 years old
let num = 10.5;
formattedString = util.format('The number is %d', num);
console.info(formattedString);
// 输出结果：The number is 10.5
num = 100.5;
formattedString = util.format('The number is %i', num);
console.info(formattedString);
// 输出结果：The number is 100
const pi = 3.141592653;
formattedString = util.format('The value of pi is %f', pi);
console.info(formattedString);
// 输出结果：The value of pi is 3.141592653
const obj: Record<string,int | string> = { "name": 'John', "age": 20 };
formattedString = util.format('The object is %j', obj);
console.info(formattedString);
// 输出结果：The object is {"name":"John","age":20}
const person: utilPersontype = {
  name: 'John',
  age: 20,
  address: {
    city: 'New York',
    country: 'USA'
  }
};
console.info(util.format('Formatted object using %%O: %O', person));
console.info(util.format('Formatted object using %%o: %o', person));
/*
输出结果：
Formatted object using %O: { name: 'John',
  age: 20,
  address:
  { city: 'New York',
    country: 'USA' } }
Formatted object using %o: { name: 'John',
  age: 20,
  address:
  { city: 'New York',
    country: 'USA' } }
 */
const percentage = 80;
let arg = 'homework';
formattedString = util.format('John finished %d%% of the %s', percentage, arg);
console.info(formattedString);
// 输出结果：John finished 80% of the homework
```

