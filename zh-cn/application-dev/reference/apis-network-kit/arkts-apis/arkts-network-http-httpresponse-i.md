# HttpResponse

request方法回调函数的返回值类型。

**起始版本：** 6

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
```

## connectionExtraInfo

```TypeScript
connectionExtraInfo?: ConnectionExtraInfo
```

HTTP请求交互的详细信息。

**类型：** [ConnectionExtraInfo](arkts-network-http-connectionextrainfo-i.md)

**起始版本：** 24

**系统能力：** SystemCapability.Communication.NetStack

## cookies

```TypeScript
cookies: string
```

服务器返回的原始cookies。开发者可自行处理。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

## header

```TypeScript
header: Object
```

发起HTTP请求返回来的响应头。当前返回的是JSON格式字符串，如需具体字段内容，需开发者自行解析。常见字段及解析方式如下：  
- content-type：header['content-type']。  
- status-line：header['status-line']。  
- date：header.date/header['date']。  
- server：header.server/header['server']。

**类型：** Object

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

## performanceTiming

```TypeScript
performanceTiming: PerformanceTiming
```

HTTP请求的各个阶段的耗时。

**类型：** [PerformanceTiming](arkts-network-http-performancetiming-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetStack

## responseCode

```TypeScript
responseCode: ResponseCode | number
```

回调函数执行成功时，此字段为[ResponseCode](arkts-network-http-responsecode-e.md)。若执行失败，错误码将会从AsyncCallback中的err字段返回。

**类型：** [ResponseCode](arkts-network-http-responsecode-e.md) \| number

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

## result

```TypeScript
result: string | Object | ArrayBuffer
```

HTTP请求根据响应头中content-type类型返回对应的响应格式内容，若HttpRequestOptions无expectDataType字段，按如下规则返回：  
- application/json：返回JSON格式的字符串。  
- application/octet-stream：ArrayBuffer。  
- image：ArrayBuffer。  
- 其他：string。  
若HttpRequestOption有expectDataType字段，开发者需传入与服务器返回类型相同的数据类型。

**类型：** string \| Object \| ArrayBuffer

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

## resultType

```TypeScript
resultType: HttpDataType
```

返回值类型。

**类型：** [HttpDataType](arkts-network-http-httpdatatype-e.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack
