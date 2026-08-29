# promisify

## 导入模块

```TypeScript
```

## promisify

```TypeScript
function promisify(original: (err: Object, value: Object) => void): Function
```

接收一个采用"错误优先"回调模式的函数，即以`(err, value) =&gt; callback`作为最后一个参数，并返回其Promise函数。 适用于将旧版回调式异步API转换为Promise风格，以便使用async/await语法进行调用，从而简化异步代码编写。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| original | (err: Object, value: Object) =&gt; void | 是 | 回调函数中第一个参数 **err** 是拒绝原因（如果Promise已解决，则为null），第二个参数 **value** 是已解决的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Function | 返回一个Promise函数，该Promise在原始回调函数成功执行时resolve为回调的value值，在原始回调函数执行出错时reject为错误对象。 |

**示例**

```TypeScript
async function fn() {
  return 'hello world';
}
const addCall = util.promisify(util.callbackWrapper(fn));
(async () => {
  try {
    let res: string = await addCall();
    console.info(res);
    // 输出结果：hello world
  } catch (err) {
    console.info(err);
  }
})();
```
