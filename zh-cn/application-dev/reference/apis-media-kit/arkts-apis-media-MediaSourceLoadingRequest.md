# Interface (MediaSourceLoadingRequest)
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @zengyawen-->

> **说明：**
>
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 18开始支持。

用于定义加载请求的对象。应用程序通过该对象来获取请求的资源位置，通过该对象和播放器进行数据交互。

## 导入模块

```ts
import { media } from '@kit.MediaKit';
```

## 属性

**系统能力：** SystemCapability.Multimedia.Media.Core

| 名称   | 类型    | 只读   | 可选   | 说明                |
| --------------------------------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| url       | string                        | 否   | 否   | 资源url，需要应用程序打开的资源路径。<br>**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。 |
| header     | Record<string, string>        | 否   | 是   | 网络请求标头，如果存在，需要应用在下载数据是将头信息设置到http请求中。<br>**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。 |

## respondData<sup>18+</sup>

respondData(uuid: number, offset: number, buffer: ArrayBuffer): number

用于应用程序向播放器发送数据。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名   | 类型     | 必填 | 说明                 |
| -------- | -------- | ---- | -------------------- |
| uuid | number | 是  | 	资源句柄的标识。 |
| offset | number | 是  | 	当前媒体数据相对于资源起始位置的偏移量。 |
| buffer | ArrayBuffer | 是  | 	响应播放器的媒体数据。<br/>**注意：** 不要传输无关数据，会影响正常数据解析和播放。 |

**返回值：**

| 类型           | 说明                                |
| -------------- | ----------------------------------- |
| number | 当前服务端接受的字节数。<br>- 返回值小于0表示操作失败。<br>- 返回值为-2时，表示播放器不再需要当前数据，客户端应停止当前读取过程。<br>- 返回值为-3时，表示播放器的缓冲区已满，客户端应等待下一次读取。 |

**示例：**

```ts
import { HashMap } from '@kit.ArkTS';
let requests: HashMap<number, media.MediaSourceLoadingRequest> = new HashMap();
let uuid = 1;

let request = requests.get(uuid);
let offset = 0; // 当前媒体数据相对于资源起始位置的偏移量
let buf = new ArrayBuffer(0); // 由应用定义，推送给播放器的数据
let num = request?.respondData(uuid, offset, buf);
```

## respondHeader<sup>18+</sup>

respondHeader(uuid: number, header?: Record<string, string>, redirectUrl?: string): void

用于应用程序向播放器发送响应头信息，应在第一次调用[respondData](#responddata18)方法之前调用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名   | 类型     | 必填 | 说明                 |
| -------- | -------- | ---- | -------------------- |
| uuid | number | 是  | 	资源句柄的标识。 |
| header | Record<string, string> | 否  | HTTP响应中的头部信息。应用可将头部信息字段与底层支持解析字段取交集传递或直接传入对应的所有头部信息。<br> - 底层播放需要解析的字段包括Transfer-Encoding、Location、Content-Type、Content-Range、Content-Encode、Accept-Ranges、content-length。 |
| redirectUrl | string | 否  | 	如果存在，为HTTP响应中的重定向URL。 |

**示例：**

```ts
import { HashMap } from '@kit.ArkTS';
let requests: HashMap<number, media.MediaSourceLoadingRequest> = new HashMap();
let uuid = 1;

// 应用根据情况填充。
let header:Record<string, string> = {
  'Transfer-Encoding':'xxx',
  'Location' : 'xxx',
  'Content-Type' : 'xxx',
  'Content-Range' : 'xxx',
  'Content-Encode' : 'xxx',
  'Accept-Ranges' : 'xxx',
  'content-length' : 'xxx'
};
let request = requests.get(uuid);
request?.respondHeader(uuid, header);
```

## finishLoading<sup>18+</sup>

finishLoading(uuid: number, state: LoadingRequestError): void

应用程序用于通知播放器当前请求状态的接口。针对服务侧请求的单个资源，推送完全部资源后需要发送LOADING_ERROR_SUCCESS状态告知该资源推送结束。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名   | 类型     | 必填 | 说明                 |
| -------- | -------- | ---- | -------------------- |
| uuid | number | 是  | 	资源句柄的标识。 |
| state  | [LoadingRequestError](arkts-apis-media-e.md#loadingrequesterror18) | 是  | 请求的状态。 |

**示例：**

```ts
import { HashMap } from '@kit.ArkTS';

let requests: HashMap<number, media.MediaSourceLoadingRequest> = new HashMap();
let uuid = 1;

let request = requests.get(uuid);
let loadingError = media.LoadingRequestError.LOADING_ERROR_SUCCESS;
request?.finishLoading(uuid, loadingError);
```