# getHash

## getHash

```TypeScript
function getHash(object: object): number
```

获取对象的哈希值。
如果尚未获取过哈希值，则生成一个随机哈希值，保存到对象的 **hash** 字段中并返回。如果已经获取过哈希值，则返回保存在
**hash** 字段中的哈希值（同一对象返回相同的值）。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| object | object | 是 | 要获取哈希值的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 哈希值。 |

**示例：**

```TypeScript
interface Person {
  name: string,
  age: number
}
let obj: Person = { name: 'Jack', age: 20 };
let result1 = util.getHash(obj);
console.info('result1 is ' + result1);
let result2 = util.getHash(obj);
console.info('result2 is ' + result2);
// 输出结果：result1 与 result2 的值相等，且为随机的Hash值。

```

