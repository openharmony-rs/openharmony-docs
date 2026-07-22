# getKeyProperties

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## getKeyProperties

```TypeScript
function getKeyProperties(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void
```

获取密钥属性。使用callback异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.getKeyItemProperties<sup>9+</sup>](arkts-universalkeystore-huks-getkeyitemproperties-f.md#getkeyitemproperties)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getKeyItemProperties(](arkts-universalkeystore-huks-getkeyitemproperties-f.md#getkeyitemproperties)

<!--Device-huks-function getKeyProperties(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void--><!--Device-huks-function getKeyProperties(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名，应与所用密钥生成时使用的别名相同。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 空对象（此处传空即可）。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;HuksResult&gt; | 是 | 回调函数。当获取密钥属性成功时，err为undefined，data为获取到的HuksResult；否则为错误对象。 |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
huks.getKeyProperties(keyAlias, emptyOptions, (err, data) => {
});

```


## getKeyProperties

```TypeScript
function getKeyProperties(keyAlias: string, options: HuksOptions): Promise<HuksResult>
```

获取密钥属性。使用Promise异步回调。
> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.getKeyItemProperties<sup>9+</sup>](arkts-universalkeystore-huks-getkeyitemproperties-f.md#getkeyitemproperties)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getKeyItemProperties(keyAlias:](arkts-universalkeystore-huks-getkeyitemproperties-f.md#getkeyitemproperties)

<!--Device-huks-function getKeyProperties(keyAlias: string, options: HuksOptions): Promise<HuksResult>--><!--Device-huks-function getKeyProperties(keyAlias: string, options: HuksOptions): Promise<HuksResult>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 密钥别名，应与所用密钥生成时使用的别名相同。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 空对象（此处传空即可）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HuksResult&gt; | Promise对象，返回HuksResult。HuksResult的properties返回密钥参数。 |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.getKeyProperties(keyAlias, emptyOptions);

```

