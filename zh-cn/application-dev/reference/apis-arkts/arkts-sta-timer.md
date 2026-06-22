# Timer (定时器)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

本模块提供了基础的定时器能力，支持按照指定的时间执行对应函数或重复执行函数。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## setTimeout

setTimeout(func: Function): int

设置一个定时器，在下一个事件循环周期执行函数。该接口等价于调用setTimeout(func, 0)。

该定时器在回调被执行后自动删除，或使用[clearTimeout](#cleartimeout)接口手动删除。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| func | Function | 是 | 定时器到期后执行的函数。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| int | 该定时器的ID，定时器ID为进程共享，是从1开始顺序增加的整数，无重复值。与动态语言不同，动态语言的定时器ID从0开始。 |

**示例：**

```ts
let timeoutID = setTimeout(() => {
  console.info('executed on next cycle');
});
console.info('timeoutID: ' + timeoutID);
// timeoutID: 1
// executed on next cycle
```

## setTimeout

setTimeout(func: Function, delayMs: int | null | undefined, ...args: FixedArray\<Any>): int

设置一个定时器，该定时器在定时器到期后执行一个函数，并可将附加参数传递给该函数。

该定时器在回调被执行后自动删除，或使用[clearTimeout](#cleartimeout)接口手动删除。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| func | Function | 是 | 定时器到期后执行的函数。 |
| delayMs | int \| null \| undefined | 是 | 延迟的毫秒数，函数的调用会在该延迟之后发生。<br>如果传入null或undefined，将视为0毫秒。<br>**注意**：<br>1. 该计时器非精准计时器，实际延迟可能会与预期延迟存在误差。<br>2. 如果值小于0，将被默认设置为0。 |
| ...args | FixedArray\<Any> | 否 | 附加参数，作为参数传递给func。<br>args参数数量少于func函数参数数量时，会抛出ArgumentsUnderapplicationError。<br>args参数数量多于func函数参数数量时，多余的args参数会被忽略。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| int | 该定时器的ID，定时器ID为进程共享，是从1开始顺序增加的整数，无重复值。与动态语言不同，动态语言的定时器ID从0开始。 |

**示例1**：不带附加参数。

```ts
let timeoutID = setTimeout(() => {
  console.info('delay 1s');
}, 1000);
console.info('timeoutID: ' + timeoutID);
// timeoutID: 1
// delay 1s（定时器到期后执行）
```

**示例2**：带附加参数。

```ts
function myFunction(param1: string, param2: string) {
  console.info(param1, param2);
}
let timeoutID = setTimeout(myFunction, 1000, 'Hello', 'World');
// Hello World（定时器到期后执行）
```

**示例3**：附加参数数量多于函数参数数量。

```ts
function myFunction(a: string) {
  console.info(a);
}
setTimeout(myFunction, 1000, 'Hello', 'World');
// Hello（多余的args参数被忽略）
```

## setTimeout

setTimeout(msg: string, delayMs?: int | null): int

设置一个定时器，该定时器在定时器到期后通过console.error方式打印字符串内容，不进行其他处理。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| msg | string | 是 | 定时器到期后打印的消息内容。 |
| delayMs | int \| null | 否 | 延迟的毫秒数，消息的打印会在该延迟之后发生。<br>如果省略该参数或者传入null，将视为0毫秒。<br>**注意**：<br>1. 该计时器非精准计时器，实际延迟可能会与预期延迟存在误差。<br>2. 如果值小于0，将被默认设置为0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| int | 该定时器的ID，定时器ID为进程共享，是从1开始顺序增加的整数，无重复值。与动态语言不同，动态语言的定时器ID从0开始。 |

**示例：**

```ts
let timeoutID = setTimeout('error message', 1000);
console.info('timeoutID: ' + timeoutID);
// timeoutID: 1
// error message（定时器到期后，以console.error输出）
```

## clearTimeout

clearTimeout(timerId?: int | null): void

取消通过调用[setTimeout](#settimeout)建立的定时器。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| timerId | int \| null | 否 | 要取消定时器的ID，需要与调用[setTimeout](#settimeout)设置定时器的返回值一致。如果省略该参数、传入null或undefined，不会取消任何定时任务。如果传入的定时器ID不存在，不会产生任何效果。 |

**示例：**

```ts
let timeoutID = setTimeout(() => {
  console.info('do after 1s delay.');
}, 1000);
clearTimeout(timeoutID);
// 无输出，定时器已被取消
```

## setInterval

setInterval(func: Function, delayMs: int | null | undefined, ...args: FixedArray\<Any>): int

重复调用一个函数，在每次调用之间具有固定的时间延迟。首次调用将在delayMs延迟之后发生。

删除该定时器需手动调用[clearInterval](#clearinterval)接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| func | Function | 是 | 定时器到期后执行的函数。 |
| delayMs | int \| null \| undefined | 是 | 延迟的毫秒数，函数的调用会在该延迟之后发生。<br>如果传入null或undefined，将视为0毫秒。<br>**注意**：<br>1. 该计时器非精准计时器，实际延迟可能会与预期延迟存在误差。<br>2. 如果值小于0，将被默认设置为0。 |
| ...args | FixedArray\<Any> | 否 | 附加参数，作为参数传递给func。<br>args参数数量少于func函数参数数量时，会抛出ArgumentsUnderapplicationError。<br>args参数数量多于func函数参数数量时，多余的args参数会被忽略。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| int | 该定时器的ID，定时器ID为进程共享，是从1开始顺序增加的整数，无重复值。与动态语言不同，动态语言的定时器ID从0开始。 |

**示例1**：不带附加参数。

```ts
let intervalID = setInterval(() => {
  console.info('do every 1s.');
}, 1000);
// do every 1s.（首次在1000毫秒延迟后执行，之后每隔1000毫秒重复执行）
// do every 1s.
// ...持续执行，直到调用clearInterval取消
```

**示例2**：带附加参数。

```ts
function myFunction(param1: string) {
  console.info(param1);
}
setInterval(myFunction, 1000, 'Hello');
// Hello（首次在1000毫秒延迟后执行，之后每隔1000毫秒重复执行）
// Hello
// ...持续执行，直到调用clearInterval取消
```

**示例3**：附加参数数量多于函数参数数量。

```ts
function myFunction(a: string) {
  console.info(a);
}
setInterval(myFunction, 1000, 'Hello', 'World');
// Hello（多余的args参数被忽略，首次在1000毫秒延迟后执行，之后每隔1000毫秒重复执行）
// Hello
// ...持续执行，直到调用clearInterval取消
```

## setInterval

setInterval(msg: string, delayMs?: int | null): int

重复通过console.error方式打印字符串内容，在每次打印之间具有固定的时间延迟。首次打印将在delayMs延迟之后发生。

删除该定时器需手动调用[clearInterval](#clearinterval)接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| msg | string | 是 | 重复打印的消息内容。 |
| delayMs | int \| null | 否 | 延迟的毫秒数，消息的打印会在该延迟之后发生。<br>如果省略该参数或传入null，将视为0毫秒。<br>**注意**：<br>1. 该计时器非精准计时器，实际延迟可能会与预期延迟存在误差。<br>2. 如果值小于0，将被默认设置为0。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| int | 该定时器的ID，定时器ID为进程共享，是从1开始顺序增加的整数，无重复值。与动态语言不同，动态语言的定时器ID从0开始。 |

**示例：**

```ts
let intervalID = setInterval('error message', 1000);
// error message（首次在1000毫秒延迟后以console.error输出，之后每隔1000毫秒重复输出）
// error message
// ...持续执行，直到调用clearInterval取消
```

## clearInterval

clearInterval(timerId?: int | null): void

取消通过调用[setInterval](#setinterval)设置的重复定时任务。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| timerId | int \| null | 否 | 要取消的重复定时器的ID，需要与调用[setInterval](#setinterval)设置重复定时器的返回值一致。如果省略该参数、传入null或undefined，不会取消任何定时任务。如果传入的定时器ID不存在，不会产生任何效果。 |

**示例：**

```ts
let intervalID = setInterval(() => {
  console.info('do every 1s.');
}, 1000);
clearInterval(intervalID);
// 无输出，定时器已被取消
```

## 其他说明

### 超时延迟

如果当前正忙于其他任务，定时器的实际触发时间可能比设定的延迟时间晚。setTimeout的回调函数会在下一个事件周期执行。例如：

```ts
function foo() {
  console.info('foo is called')
}
setTimeout(foo, 0);
console.info('After setTimeout')

// output
After setTimeout
foo is called
```

这是因为，虽然setTimeout()设置了0ms的延迟，但任务不会立即执行，而是被放入队列中，等待下一次事件循环。当前代码执行完毕后，队列中的函数才会被执行，因此最终的执行顺序可能与预期不一致。

### 最大延迟值

delayMs参数类型为int（32位带符号整数），取值范围为0 ~ 2147483647（约24.8天）。如果值小于0，将被默认设置为0。

### 定时器冻结

定时器的触发受底层任务调度。当应用被切换到后台后，定时器到期不会触发回调，定时器进入冻结状态；应用被重新拉起到前台后，到期定时器的回调会按序触发。可以使用trace查看进程是否还存在调度，如果进程无调度任务，定时器会进入休眠状态。

### 定时器ID

setTimeout()和setInterval()使用相同的ID池，定时器ID从1开始顺序增加。因此技术上可以互相调用clearTimeout()和clearInterval()来清除。然而，为了提高代码的可读性和可维护性，建议分别使用各自对应的清除方法，以避免混淆。
