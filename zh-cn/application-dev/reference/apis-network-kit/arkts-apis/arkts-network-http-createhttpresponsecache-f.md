# createHttpResponseCache

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## createHttpResponseCache

```TypeScript
function createHttpResponseCache(cacheSize?: int): HttpResponseCache
```

创建一个HttpResponseCache对象，可用于存储HTTP请求的响应数据。对象中可调用 [flush](arkts-network-http-httpresponsecache-i.md#flush)与 [delete](arkts-network-http-httpresponsecache-i.md#delete)方法，cacheSize指定缓存大小。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-http-function createHttpResponseCache(cacheSize?: int): HttpResponseCache--><!--Device-http-function createHttpResponseCache(cacheSize?: int): HttpResponseCache-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cacheSize | int | 否 | 响应缓存大小，单位为Byte。取值范围为1*1024*1024到10*1024*1024，即1MB到10MB。默认值为10MB。超出10MB时设置为10MB；小于1MB时，设置 为1MB。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HttpResponseCache](arkts-network-http-httpresponsecache-i.md) | 返回一个存储HTTP访问请求响应的对象。 |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { http } from '@kit.NetworkKit';

let httpResponseCache = http.createHttpResponseCache();
```

ArkTS-Sta示例：

```TypeScript
import http from '@ohos.net.http';

let httpResponseCache: http.HttpResponseCache = http.createHttpResponseCache();
```

