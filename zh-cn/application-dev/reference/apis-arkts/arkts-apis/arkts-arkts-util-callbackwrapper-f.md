# callbackWrapper

## callbackWrapper

```TypeScript
function callbackWrapper(original: Function): (err: Object, value: Object) => void
```

对异步函数进行回调化处理，回调中第一个参数是拒绝原因（如果Promise已解决，则为null），第二个参数是已解决的值。 > **说明：** > > 该接口要求参数original必须是异步函数类型。如果传入的参数不是异步函数，不会进行拦截，但是会输出错误信息： > "callbackWrapper: The type of Parameter must be AsyncFunction"。 > > 该接口用于将返回Promise的async函数转换为错误优先回调风格的函数，调用此接口返回的函数接收一个回调函数作为第二个入参，调用此方法时会先执行original函数。 > 当original的Promise返回resolve时，入参的回调函数的第一个参数为null，第二个参数为resolve的值。 > 当original的Promise返回reject时，入参的回调函数的第一个参数为错误对象，第二个参数为null。 > > 由于此方法返回类型的声明为`(err: Object, value: Object) => void`，TypeScript编译器会按照该声明进行参数数量校验， > 因此当original为无入参的函数时，此接口返回的函数第一个入参需传入一个无效的占位参数。 > 当original为多个入参的函数时，此接口返回的函数当前仅支持传入一个参数，可使用array等容器进行多个入参的传入调用（参照下方示例代码）。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-util-function callbackWrapper(original: Function): (err: Object, value: Object) => void--><!--Device-util-function callbackWrapper(original: Function): (err: Object, value: Object) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| original | Function | 是 | 异步函数，要求函数返回Promise对象。该异步函数的resolve值会作为回调的第二个参数传入，reject原因会作为回调的第一个参数传入。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| (err: Object, value: Object) =&gt; void | 返回一个回调函数，该函数第一个参数 **err** 是拒绝原因（如果Promise已解决，则为null），第二个参数 **value** 是已解决的值。 |

## 示例

```TypeScript
// original为一个入参示例
async function fn(input: string) {
  return input;
}
let cb = util.callbackWrapper(fn);
cb('hello world', (err : Object, ret : string) => {
  if (err) throw new Error();
  console.info(ret);
});
// 输出结果：hello world
```

```TypeScript
// original需要传入多个入参场景示例
async function fn(args: Array<string | number | Function>) {
  console.info('args[0]: ' + args[0]); // args[0]: hello world
  console.info('args[1]: ' + args[1]); // args[1]: 8
  return args[0];
}
let cb = util.callbackWrapper(fn);
let args: Array<string | number | Function> = ['hello world', 8]
cb(args, (err : Object, ret : string) => {
  if (err) throw new Error;
  console.info(ret); // 输出结果：hello world
});
```

