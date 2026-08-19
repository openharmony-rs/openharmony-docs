# promisify

## 导入模块

```TypeScript
```

## promisify

```TypeScript
function promisify(original: Function): PromisifiedFunc
```

Takes a function following the common error-first callback style, i.e taking an (err, value) => callback as the last argument, and return a function that returns promises.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-util-function promisify(original: Function): PromisifiedFunc--><!--Device-util-function promisify(original: Function): PromisifiedFunc-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| original | Function | 是 | Asynchronous Function |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PromisifiedFunc](arkts-na-util-promisifiedfunc-t.md) | Return a function that returns promises |

