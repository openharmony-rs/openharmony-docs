# ErrorCallback

```TypeScript
type ErrorCallback = (err: ErrorEvent) => void
```

表示异常回调类型。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| err | ErrorEvent | 是 | 错误事件类，<br/>表示Worker执行过程中出现的异常信息。 |

