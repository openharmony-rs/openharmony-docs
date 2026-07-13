# GlobalScope

Worker线程自身的运行环境，GlobalScope类继承WorkerEventTarget。

**继承/实现关系：** GlobalScope extends [WorkerEventTarget](arkts-arkts-workereventtarget-i.md)

**起始版本：** 9

**系统能力：** SystemCapability.Utils.Lang

## name

```TypeScript
readonly name: string
```

Worker的名字，new Worker时指定。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## onerror

```TypeScript
onerror?: (ev: ErrorEvent) => void
```

Worker在执行过程中发生异常被调用的回调函数，该回调函数在Worker线程中执行。
其中ev类型为ErrorEvent，表示收到的异常数据。

**类型：** (ev: ErrorEvent) => void

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## self

```TypeScript
readonly self: GlobalScope & typeof globalThis
```

GlobalScope本身。

**类型：** GlobalScope & typeof globalThis

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

