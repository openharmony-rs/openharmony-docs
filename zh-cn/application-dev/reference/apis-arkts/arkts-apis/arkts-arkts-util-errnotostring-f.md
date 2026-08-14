# errnoToString

## errnoToString

```TypeScript
function errnoToString(errno: number): string
```

获取系统错误码对应的详细信息。适用于系统调用出错时将数字错误码转换为可读的描述信息，便于开发者快速定位和排查系统级错误，常用于错误日志记录和错误提示显示。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-util-function errnoToString(errno: number): string--><!--Device-util-function errnoToString(errno: number): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errno | number | 是 | 系统发生错误产生的错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 错误码对应的详细信息，包含可读的错误描述文本，便于开发者定位问题。 |

## 示例

```TypeScript
let errnum = -1; // -1 : a system error number
let result = util.errnoToString(errnum);
console.info("result = " + result);
// 输出结果：result = operation not permitted
```

