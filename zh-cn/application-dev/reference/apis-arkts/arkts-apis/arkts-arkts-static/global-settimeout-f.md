# setTimeout

## setTimeout

```TypeScript
function setTimeout(func: Function, delayMs: int | null | undefined, ...args: FixedArray<Any>): int
```

在定时器超时后执行回调函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-function setTimeout(func: Function, delayMs: int | null | undefined, ...args: FixedArray<Any>): int--><!--Device-unnamed-function setTimeout(func: Function, delayMs: int | null | undefined, ...args: FixedArray<Any>): int-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| func | Function | 是 | 定时器超时后要执行的回调函数。 |
| delayMs | int \| null \| undefined | 是 | 超时时间，单位为毫秒（ms），如果传入null或undefined，将视为0毫秒。 |
| args | FixedArray&lt;Any&gt; | 是 | 传递给func的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 定时器ID。 |

