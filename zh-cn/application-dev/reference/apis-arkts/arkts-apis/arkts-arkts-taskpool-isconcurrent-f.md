# isConcurrent

## isConcurrent

```TypeScript
function isConcurrent(func: Function): boolean
```

检查函数是否为并发函数。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| func | Function | 是 | 需要检查的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。如果被检查函数标注了<br/>[@Concurrent装饰器](../../../../arkts-utils/taskpool-introduction.md#concurrent装饰器)，则返回**true**；<br/>否则返回**false**。 |

**示例：**

```TypeScript
@Concurrent
function test() {}

let result: Boolean = taskpool.isConcurrent(test);
console.info("result is: " + result);

```

