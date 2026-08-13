# callbackWrapper

## callbackWrapper

```TypeScript
function callbackWrapper(original: Function): Function
```

Takes an async function (or a function that returns a Promise) and returns a function following the error-first callback style.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-util-function callbackWrapper(original: Function): Function--><!--Device-util-function callbackWrapper(original: Function): Function-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| original | Function | 是 | Asynchronous function |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Function | Return a Asynchronous function |

