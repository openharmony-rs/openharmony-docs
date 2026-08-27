# HttpResponseCache

存储HTTP访问请求响应的对象。在调用HttpResponseCache的方法前，需要先通过[createHttpResponseCache()](arkts-network-http-createhttpresponsecache-f.md)创建一个任 务。  
**响应头中的相应关键字使用**  
- **`Cache-Control`**：用于指定缓存策略，如`no-cache`, `no-store`, `max-age`, `public`, `private`等。  
- **`Expires`**：指定资源的过期时间，格式为GMT时间。  
- **`ETag`**：用于资源版本标识，客户端可以使用`If-None-Match`请求头来验证资源是否已更改。  
- **`Last-Modified`**：指定资源最后修改时间，客户端可以使用`If-Modified-Since`请求头来验证资源是否已更改。  
- **`Vary`**：指定哪些请求头的值会影响缓存的响应，用于区分不同的缓存版本。  
使用这些关键字时，服务器端需要正确配置响应头，客户端则需要根据这些响应头来决定是否使用缓存的资源，以及如何验证资源是否是最新的。正确的缓存策略可以显著提高应用的性能和用户体验。  
**如何设置Cache-Control头** `Cache-Control`为通用报头，但通常是在服务器端进行的，允许定义一个响应资源应该何时、如何被缓存以及缓存多长时间。以下是一些常用的`Cache-Control`指令及其含义：  
- **`no-cache`**：表示在使用缓存前，必须先去源服务器校验资源的有效性。如果资源未变更，则响应状态码为304(Not Modified)，不发送资源内容，使用缓存中的资源。如果资源已经过期，则响应状态码为200(OK  
)，并发送资源内容。  
- **`no-store`**：表示不允许缓存资源，每次请求都必须从服务器获取资源。  
- **`max-age`**：指定缓存的最大时间(以秒为单位)。例如，`Cache-Control: max-age=3600`表示缓存的有效期为1小时。  
- **`public`**：表明响应可以被任何对象(包括：发送请求的客户端，代理服务器等)缓存。  
- **`private`**：表明响应只能被单个用户缓存，不能作为共享缓存(即代理服务器不能缓存)。  
- **`must-revalidate`**：表示必须在使用缓存前验证旧资源的状态，并且在缓存过期后，需要重新验证资源。  
- **`no-transform`**：表示不允许代理服务器修改响应内容。  
- **`proxy-revalidate`**：与`must-revalidate`类似，但仅适用于共享缓存。  
- **`s-maxage`**：类似于`max-age`，但仅适用于共享缓存。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
```

## delete

```TypeScript
delete(callback: AsyncCallback<void>): void
```

禁用缓存并删除其中的数据，使用callback方式作为异步方法。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当删除成功时，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let httpRequest = http.createHttp();
httpRequest.request("EXAMPLE_URL").then(data => {
  const httpResponseCache = http.createHttpResponseCache();
  httpResponseCache.delete((err: BusinessError) => {
    try {
      if (err) {
        console.error('fail: ' + err);
      } else {
        console.info('success');
      }
    } catch (err) {
      console.error('error: ' + err);
    }
  });
  httpRequest.destroy();
}).catch((error: BusinessError) => {
  console.error("errcode" + JSON.stringify(error));
});
```

## delete

```TypeScript
delete(): Promise<void>
```

禁用缓存并删除其中的数据，使用Promise方式作为异步方法。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**示例**

```TypeScript
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let httpRequest = http.createHttp();
httpRequest.request("EXAMPLE_URL").then(data => {
  const httpResponseCache = http.createHttpResponseCache();
  httpResponseCache.delete().then(() => {
    console.info("success");
  }).catch((err: BusinessError) => {
    console.error("fail");
  });
  httpRequest.destroy();
}).catch((error: BusinessError) => {
  console.error("errcode" + JSON.stringify(error));
});
```

## flush

```TypeScript
flush(callback: AsyncCallback<void>): void
```

将缓存中的数据写入文件系统，以便在下一个HTTP请求中访问所有缓存数据，使用callback方式作为异步方法。缓存数据包括：响应头(header)、响应体(result)、cookies、请求时间(requestTime)和响 应时间(responseTime)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。返回写入结果。当写入成功时，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let httpResponseCache = http.createHttpResponseCache();
let httpRequest = http.createHttp();
httpRequest.request("EXAMPLE_URL", (err: BusinessError, data: http.HttpResponse) => {
  if (!err) {
    httpResponseCache.flush((err: BusinessError) => {
      if (err) {
        console.error('flush fail');
      }
      console.info('flush success');
    });
    httpRequest.destroy();
  } else {
    console.error('error:' + JSON.stringify(err));
    // 当该请求使用完毕时，开发者务必调用destroy方法释放资源，避免出现内存泄漏。
    httpRequest.destroy();
  }
});
```

## flush

```TypeScript
flush(): Promise<void>
```

将缓存中的数据写入文件系统，以便在下一个HTTP请求中访问所有缓存数据，使用Promise方式作为异步方法。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**示例**

```TypeScript
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let httpRequest = http.createHttp();
let httpResponseCache = http.createHttpResponseCache();
let promise = httpRequest.request("EXAMPLE_URL");

promise.then((data: http.HttpResponse) => {
  httpResponseCache.flush().then(() => {
    console.error('flush success');
  }).catch((err: BusinessError) => {
    console.error('flush fail');
  });
}).catch((err: Error) => {
  console.error('error:' + JSON.stringify(err));
});
```
