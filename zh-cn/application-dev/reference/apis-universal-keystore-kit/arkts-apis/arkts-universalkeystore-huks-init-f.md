# init

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## init

```TypeScript
function init(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksHandle>): void
```

init操作密钥接口。使用callback异步回调。

huks.init、huks.update、huks.finish为三段式接口，需要一起使用。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.initSession<sup>9+</sup>](arkts-universalkeystore-huks-initsession-f.md#initsession)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [initSession(keyAlias:](arkts-universalkeystore-huks-initsession-f.md#initsession)

<!--Device-huks-function init(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksHandle>): void--><!--Device-huks-function init(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksHandle>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | Init操作密钥的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | Init操作的参数集合。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;HuksHandle&gt; | 是 | 回调函数。当密钥操作init成功时，err为undefined，data为获取到的HuksHandle；否则为错误对象。HuksHandle的handle返回init生成的handle。 |


## init

```TypeScript
function init(keyAlias: string, options: HuksOptions): Promise<HuksHandle>
```

init操作密钥接口。使用Promise异步回调。

huks.init、huks.update、huks.finish为三段式接口，需要一起使用。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.initSession<sup>9+</sup>](arkts-universalkeystore-huks-initsession-f.md#initsession)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [initSession(keyAlias:](arkts-universalkeystore-huks-initsession-f.md#initsession)

<!--Device-huks-function init(keyAlias: string, options: HuksOptions): Promise<HuksHandle>--><!--Device-huks-function init(keyAlias: string, options: HuksOptions): Promise<HuksHandle>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | Init操作密钥的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | Init参数集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksHandle&gt; | Promise对象，返回HuksResult。HuksHandle的handle返回init生成的handle。 |

