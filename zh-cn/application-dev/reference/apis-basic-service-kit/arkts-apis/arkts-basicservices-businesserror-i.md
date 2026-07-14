# BusinessError

错误参数。

**继承/实现关系：** BusinessError extends [Error](Error)

**起始版本：** 6

**系统能力：** SystemCapability.Base

## code

```TypeScript
code: number
```

接口调用失败返回的错误码信息。

**类型：** number

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Base

## data

```TypeScript
data?: T
```

接口调用失败时返回的附加错误信息。如果不填，则错误对象不包含附加数据。

**类型：** T

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Base

