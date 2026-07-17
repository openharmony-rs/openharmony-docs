# isKeyExist

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## isKeyExist

```TypeScript
function isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>): void
```

判断密钥是否存在。使用callback异步回调。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.isKeyItemExist<sup>9+</sup>](arkts-universalkeystore-huks-iskeyitemexist-f.md#iskeyitemexist-1)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isKeyItemExist(keyAlias:

<!--Device-huks-function isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>): void--><!--Device-huks-function isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 所需查找的密钥的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于查询时指定密钥的属性TAG。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。false代表密钥不存在，true代表密钥存在。 |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
huks.isKeyExist(keyAlias, emptyOptions, (err, data) => {
});

```


## isKeyExist

```TypeScript
function isKeyExist(keyAlias: string, options: HuksOptions): Promise<boolean>
```

判断密钥是否存在。使用Promise异步回调。

> **说明：**  
>  
> 从API version 8开始支持，从API version 9开始废弃，建议使用  
> [huks.isKeyItemExist<sup>9+</sup>](arkts-universalkeystore-huks-iskeyitemexist-f.md#iskeyitemexist-2)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isKeyItemExist(keyAlias:

<!--Device-huks-function isKeyExist(keyAlias: string, options: HuksOptions): Promise<boolean>--><!--Device-huks-function isKeyExist(keyAlias: string, options: HuksOptions): Promise<boolean>-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyAlias | string | 是 | 所需查找的密钥的别名。 |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 是 | 用于查询时指定密钥的属性TAG。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。false代表密钥不存在，true代表密钥存在。 |

**示例：**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* 此处options选择emptyOptions来传空 */
let keyAlias = 'keyAlias';
let emptyOptions: huks.HuksOptions = {
  properties: []
};
let result = huks.isKeyExist(keyAlias, emptyOptions);

```

