# SourceCloseCallback

```TypeScript
type SourceCloseCallback = (uuid: number) => void
```

由应用实现此回调函数，应用应释放相关资源。

> **注意：**
>
> 客户端在处理完请求后应立刻返回。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | long | 是 | 资源句柄的标识。 |

