# setInterval

## setInterval

```TypeScript
export declare function setInterval(handler: Function | string, delay: number, ...arguments: any[]): number
```

重复调用一个函数，在每次调用之间具有固定的时间延迟。 删除该定时器需手动调用clearInterval()接口。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare function setInterval(handler: Function | string, delay: number, ...arguments: any[]): number--><!--Device-unnamed-export declare function setInterval(handler: Function | string, delay: number, ...arguments: any[]): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Function \| string | 是 | 类型为Function表示定时器到期后执行函数；&lt;br&gt;类型为string则通过Error方式 打印string中内容，不进行其他处理。 |
| delay | number | 是 | 延迟的毫秒数，函数的调用会在该延迟之后发生。建议传入整数，若传入小数，会被向下取整。 &lt;br&gt;**注意**&lt;br&gt;1. 该计时器非精准计时器，实际延迟可能会与预期延迟存在误差。&lt;br&gt;2. 如果值小于1， 将被默认设置为0。&lt;br&gt;3. delay值受系统限制，超出2^31 - 1时会溢出，delay值为0。 |
| arguments | any[] | 是 | 附加参数，仅当handler类型为Function时生效，作为参数传递给handler。 &lt;br&gt;arguments参数数量少于handler函数参数数量时，未被arguments覆盖的参数会被设为undefined。 &lt;br&gt;arguments参数数量多于handler函数参数数量时，多余的arguments参数会被忽略，但可通过handler函数内部的 arguments对象访问。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 该定时器的ID，定时器ID为进程共享，是从0开始顺序增加的整数，无重复值。 |

