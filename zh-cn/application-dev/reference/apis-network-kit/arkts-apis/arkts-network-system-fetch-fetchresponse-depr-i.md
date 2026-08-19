# FetchResponse

**表2** responseType与success中data关系 | responseType | data | 说明 | | -------- | -------- | -------- | | 无 | string | 服务器返回的header中的type如果是text/\*或application/json、application/javascript、application/xml，值为文本内容。 | | text | string | 返回文本内容。 | | json | Object | 返回json格式的对象。 |

**起始版本：** 3

<!--Device-unnamed-export interface FetchResponse--><!--Device-unnamed-export interface FetchResponse-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
```

## code

```TypeScript
code: number
```

表示服务器的状态code。

**类型：** number

**起始版本：** 3

<!--Device-FetchResponse-code: number--><!--Device-FetchResponse-code: number-End-->

**系统能力：** SystemCapability.Communication.NetStack

## data

```TypeScript
data: string | object
```

返回数据类型由responseType确定，详见表 responseType与success中data关系。

**类型：** string \| object

**起始版本：** 3

<!--Device-FetchResponse-data: string | object--><!--Device-FetchResponse-data: string | object-End-->

**系统能力：** SystemCapability.Communication.NetStack

## headers

```TypeScript
headers: Object
```

表示服务器response的所有header。

**类型：** Object

**起始版本：** 3

<!--Device-FetchResponse-headers: Object--><!--Device-FetchResponse-headers: Object-End-->

**系统能力：** SystemCapability.Communication.NetStack

