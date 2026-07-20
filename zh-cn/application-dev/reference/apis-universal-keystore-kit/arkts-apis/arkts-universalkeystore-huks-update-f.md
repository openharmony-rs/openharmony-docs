# update

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

<a id="update"></a>
## update

```TypeScript
function update(handle: number, token?: Uint8Array, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

update操作密钥接口。使用callback异步回调。

huks.init、huks.update、huks.finish为三段式接口，需要一起使用。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.updateSession<sup>9+</sup>](arkts-universalkeystore-huks-updatesession-f.md#updatesession-1)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [updateSession(](arkts-universalkeystore-huks-updatesession-f.md#updatesession-1)

<!--Device-huks-function update(handle: number, token?: Uint8Array, options: HuksOptions, callback: AsyncCallback<HuksResult>): void--><!--Device-huks-function update(handle: number, token?: Uint8Array, options: HuksOptions, callback: AsyncCallback<HuksResult>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Update操作的uint64类型的handle值。 |
| token | Uint8Array | 否 | Update操作的token。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | Update操作的参数集合。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;HuksResult&gt; | 是 | 回调函数。当密钥操作update成功时，err为undefined，data为获取到的HuksResult；否则为错误对象。 |


<a id="update-1"></a>
## update

```TypeScript
function update(handle: number, token?: Uint8Array, options: HuksOptions): Promise<HuksResult>
```

update操作密钥接口。使用Promise异步回调。

huks.init、huks.update、huks.finish为三段式接口，需要一起使用。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.updateSession<sup>9+</sup>](arkts-universalkeystore-huks-updatesession-f.md#updatesession-1)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [updateSession(handle:](arkts-universalkeystore-huks-updatesession-f.md#updatesession-1)

<!--Device-huks-function update(handle: number, token?: Uint8Array, options: HuksOptions): Promise<HuksResult>--><!--Device-huks-function update(handle: number, token?: Uint8Array, options: HuksOptions): Promise<HuksResult>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | number | 是 | Update操作的uint64类型的handle值。 |
| token | Uint8Array | 否 | Update操作的token。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | Update操作的参数集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise对象，返回HuksResult。 |

